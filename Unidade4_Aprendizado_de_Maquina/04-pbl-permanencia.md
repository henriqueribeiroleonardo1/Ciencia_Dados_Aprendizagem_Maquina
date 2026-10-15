<img src="assets/logo-udf.jpg" alt="UDF Centro Universitário" width="230">

**Profa. Kadidja Valéria | UDF**  
Ciência de Dados e Aprendizado de Máquina · Sistemas de Informação · 2026.2

# PBL integrador — Apoio à Permanência

## Identificação

- Estudante ou equipe: **Henrique Ribeiro Leonardo**
- Turma: **Sistemas de Informação — 2026.2**
- Data de realização: **30/10/2026**
- Integrantes e contribuições (se em equipe): **Atividade individual.**

## Contexto

Uma instituição quer compreender sinais associados à evasão e oferecer apoio antes do fim do semestre. Público-alvo: estudantes matriculados e equipe de apoio acadêmico. O cenário é didático e a prática usa dados sintéticos.

**Questão norteadora:** como identificar situações que merecem atenção e oferecer apoio, reconhecendo erros do modelo e dificuldades que os dados não capturam?

## Proposta da equipe

### 1. Delimitação

- Problema e público: **Quando a evasão aparece nos relatórios, o semestre já acabou e não dá mais para ajudar. Beneficiários: os estudantes matriculados. Quem usa a informação: a equipe de apoio acadêmico.**
- Decisão que o resultado pode apoiar: **A ordem em que a equipe de apoio faz os contatos a partir da semana 5, dada a quantidade de pessoas que ela consegue atender. O modelo não decide quem recebe ajuda; decide por onde começar.**
- Definição de evasão, unidade e horizonte: **Evasão = não ter matrícula ativa nem frequência nas duas últimas semanas do semestre. Trancamento formal e transferência para outro curso da própria instituição ficam fora, porque são caminhos diferentes e pedem outro tipo de apoio. Unidade: estudante em um semestre. Horizonte: previsão no fim da semana 4, desfecho no fim do semestre.**

### 2. Perguntas de negócio

1. **Com frequência, nota parcial e entregas até a semana 4, quais estudantes têm a maior chance estimada de evadir e devem ser contatados primeiro?**
2. **Se a equipe consegue fazer N contatos por semana, quantos dos estudantes que realmente evadiriam ela alcança, e quantos contatos seriam "desnecessários"?**

### 3. Dados necessários

| Dado | Papel no projeto | Disponível quando? | Origem pretendida | Necessidade e risco |
| --- | --- | --- | --- | --- |
| Frequência até a semana 4 | Atributo | Fim da semana 4 | Diário de classe | Necessário. Risco: faltas por motivo de saúde ou trabalho viram "sinal de risco" sem contexto. |
| Nota parcial até a semana 4 | Atributo | Fim da semana 4 | Sistema acadêmico | Atributo mais informativo na simulação. Risco: disciplinas sem prova até a semana 4 geram ausências. |
| Entregas no AVA até a semana 4 | Atributo | Fim da semana 4 | Ambiente virtual | Útil. Risco: depende de cada professor usar o AVA do mesmo jeito. |
| Situação no fim do semestre | Alvo | Fim do semestre | Secretaria | Indispensável para treinar. Risco: definição de evasão diferente entre setores. |
| Código pseudônimo | Junta as bases; não entra no modelo | Sempre | Secretaria | Necessário. Risco: reidentificação; a tabela de correspondência fica só com a secretaria. |
| Renda, raça, deficiência, idade | **Não entra como atributo.** Só para auditoria de equidade, se autorizada | — | Questionário voluntário | Alto risco de discriminação. Só com base legal, consentimento e comitê de ética. |

Diferencie dados usados na simulação e dados que seriam necessários para uma investigação real: **No laboratório usei 600 linhas fictícias, três atributos e uma regra de geração conhecida, com registros independentes. Uma investigação real precisaria de vários semestres por curso e turno, a mesma definição de evasão em todos eles, as datas (para treinar no passado e testar no futuro), informação suficiente para checar se o modelo erra mais com algum grupo, e a voz dos estudantes sobre o que os faz sair (questionário ou entrevista). Tudo isso com aprovação do comitê de ética e de acordo com a LGPD.**

### 4. Abordagem e algoritmo

- Classificação, regressão ou outra formulação, com justificativa: **Classificação binária supervisionada. O histórico tem o desfecho (evadiu ou não), e o desfecho é uma categoria. Representar como 1/0 é só um código.**
- Algoritmo introdutório escolhido: **Árvore de decisão com `max_depth=4` e `min_samples_leaf=40`, com a nota faltante preenchida pela mediana dentro do pipeline. Escolhi uma árvore rasa e com folhas grandes porque ela empatou com as mais complexas na validação, e cada regra pode ser lida e questionada pela equipe de apoio.**
- Referência simples: **`DummyClassifier` que responde sempre "permaneceu".**

### 5. Avaliação

- Preparação, divisão e validação: **Holdout estratificado 75/25 (450/150), semente 42; mediana aprendida só no treino; grade de 24 combinações de parâmetros e escolha do limiar por validação cruzada estratificada em 5 partes no treino; teste usado uma vez. Com dados reais: treinar em semestres anteriores e testar no seguinte.**
- Métricas e razão da escolha: **Sensibilidade da classe "evadiu" como métrica principal, porque deixar de contatar quem ia sair é o pior erro. Precisão, para medir quanto do tempo da equipe vai para contatos desnecessários. Acurácia e matriz de confusão, sempre ao lado da referência.**
- Resultados efetivamente calculados e link da evidência: **Validação 0,729 ± 0,030. Teste: acurácia 0,780 (referência 0,593), TN 70, FP 19, FN 14, TP 47, sensibilidade 0,770, precisão 0,712. Evidências: [notebook executado](notebooks/laboratorio-henrique.ipynb), [registro do laboratório](03-aula2-laboratorio.md), [matriz](assets/henrique-matriz-confusao.png).**
- Erros relevantes e consequências: **14 estudantes que evadiram (23% dos casos) não seriam sinalizados. 19 que permaneceram receberiam um contato que não precisavam. A segunda pergunta de negócio entra aqui: no treino, baixar o limiar para 0,4 subiria a sensibilidade para cerca de 0,75 (em vez de 0,61 com 0,5 na validação), mas exigiria contatar metade da turma. A escolha do limiar depende da capacidade da equipe, e isso é decisão da instituição, não do modelo.**

### 6. Limites e proteção

- Por que os resultados não demonstram causalidade? **O modelo aprendeu que nota baixa e evasão andam juntas, mas não sabe por quê. Pode ser que o estudante comece a trabalhar e isso derrube tanto a nota quanto a permanência. No meu experimento, retirar a frequência não piorou o modelo, embora a simulação a use para gerar a evasão: importância para prever não é a mesma coisa que causa.**
- Por que dados sintéticos não validam uso institucional? **Os dados só têm o que quem programou a simulação colocou: três atributos, uma fórmula e um ruído. Uma instituição real tem cursos, turnos, mudanças de ano para ano e erros de registro que a simulação nem tenta imitar. Um resultado bom aqui mostra que o método funciona, não que o modelo funcionaria lá.**
- Que grupos podem ser mal representados? Como investigar isso com evidências apropriadas? **Estudantes do noturno que trabalham, ingressantes (sem histórico), pessoas com deficiência, cursos com poucas turmas e estudantes de EAD. Para investigar: medir sensibilidade e falsos positivos separadamente por grupo, em dados reais e autorizados, com amostra suficiente em cada grupo; ouvir os estudantes e a equipe; e repetir a análise a cada semestre. O conjunto sintético não tem grupos, então não posso afirmar nada sobre equidade.**
- Como minimizar dados, restringir acesso e definir retenção? **Usar só os três atributos acadêmicos; o modelo recebe um código, nunca nome ou matrícula; a lista fica só com a equipe de apoio e cada acesso fica registrado; professores não veem a lista, para ela não influenciar notas; ao fim do semestre a lista é apagada e só ficam números agregados para avaliar o modelo.**
- Como garantir revisão humana e contestação? **Alguém da equipe revisa cada nome antes do contato e pode tirar ou incluir estudantes. O estudante sabe que o convite é opcional, pode perguntar por que foi contatado e corrigir dados errados. Nenhuma decisão acadêmica (nota, bolsa, matrícula) usa o modelo. Há um canal para reclamações e uma revisão do modelo a cada semestre.**

### 7. Recomendações de apoio

- Ação voluntária proposta: **Mensagem acolhedora da coordenação convidando para uma conversa, com opções concretas: monitoria, orientação de estudos, informação sobre bolsas e auxílios e atendimento psicopedagógico. A mensagem nunca fala em "risco de evasão".**
- Como acolher estudantes não sinalizados pelo modelo: **Os mesmos serviços divulgados para todas as turmas, um formulário em que o próprio estudante pede ajuda e o encaminhamento por professores e colegas. O modelo é uma porta de entrada a mais, não a única.**
- O que precisa ser verificado antes de aplicação real: **Desempenho com dados reais e divisão por semestre; desempenho por grupo; parecer jurídico e do comitê de ética (LGPD); definição oficial de evasão; quantos contatos a equipe consegue fazer de fato; e um piloto em poucas turmas para ver se o apoio muda alguma coisa.**

Previsões não são certezas. Priorize apoio e revisão humana, sem punições ou decisões automáticas prejudiciais.

## Apresentação de cinco minutos

| Tempo | Conteúdo | Responsável |
| --- | --- | --- |
| 1 minuto | Problema e dados | Henrique |
| 2 minutos | Método e resultados | Henrique |
| 1 minuto | Limitações | Henrique |
| 1 minuto | Recomendações de apoio | Henrique |

## Contribuições

| Integrante | Contribuição verificável |
| --- | --- |
| Henrique Ribeiro Leonardo | Todas as seções, com base no [notebook executado](notebooks/laboratorio-henrique.ipynb) e no [registro do laboratório](03-aula2-laboratorio.md). |

[Voltar ao início](README.md).
