<img src="assets/logo-udf.jpg" alt="UDF Centro Universitário" width="230">

**Profa. Kadidja Valéria | UDF**  
Ciência de Dados e Aprendizado de Máquina · Sistemas de Informação · 2026.2

# Questões de revisão — Registro individual

## Identificação

- Estudante ou equipe: **Henrique Ribeiro Leonardo**
- Turma: **Sistemas de Informação — 2026.2**
- Data de realização: **30/10/2026**
- Integrantes e contribuições (se em equipe): **Individual.**

Responda com suas palavras e apresente os cálculos quando solicitados. Os números dos exercícios manuais não são os resultados do laboratório.

## 1. Explique a diferença entre regra programada para bloquear uma palavra e modelo de spam treinado com exemplos.

**Resposta:** Na regra, quem decide é o programador: ele escolhe a palavra e o sistema obedece, sempre do mesmo jeito. É transparente, mas frágil: basta escrever a palavra com um número no lugar de uma letra para escapar, e e-mails normais que usam a palavra são barrados. No modelo, quem "escreve" a regra são os exemplos: o algoritmo vê muitas mensagens já marcadas e aprende quais combinações de sinais costumam ser spam. Ele lida melhor com variações e pode ser retreinado, mas só é tão bom quanto as marcações que recebeu e é mais difícil explicar cada decisão.

## 2. Por que codificar evadiu/permaneceu como 1/0 não transforma classificação em regressão?

**Resposta:** O que define a tarefa é o que o alvo significa, não o tipo de dado na coluna. "Evadiu" e "permaneceu" são duas categorias; eu poderia ter usado "A" e "B" que nada mudaria. Não existe 0,5 de evasão, e 1 não é "mais" que 0 no sentido de quantidade. Por isso avalio com matriz de confusão, acurácia e sensibilidade, e não com MAE.

## 3. Uma biblioteca quer estimar empréstimos e descobrir perfis. Que tarefas correspondem a cada pergunta?

**Resposta:** São duas tarefas diferentes. Estimar quantos empréstimos vão acontecer é **regressão** (supervisionado), porque o alvo é um número e o histórico já o registra. Descobrir perfis de usuários é **agrupamento** (não supervisionado), porque não existe uma lista prévia de perfis para servir de alvo.

## 4. O que são atributo, alvo e unidade de análise no laboratório educacional?

**Resposta:** A unidade de análise é o "quem" de cada linha: um estudante fictício em um semestre. Os atributos são o que se sabe sobre ele na hora de prever, no fim da semana 4: `frequencia_sem4`, `nota_sem4` e `entregas_sem4`. O alvo é o que se quer adivinhar: `evasao_fim_semestre` (1 = evadiu), que só se conhece no fim do semestre.

## 5. Por que calcular a mediana antes de dividir os dados pode invalidar a avaliação?

**Resposta:** Porque a mediana seria calculada olhando também as notas dos estudantes de teste. Esses valores entrariam no treino disfarçados de "preenchimento", e o teste deixaria de ser composto por dados realmente nunca vistos. Isso se chama vazamento de dados, e o resultado tende a sair melhor do que seria na prática. O certo é dividir primeiro e deixar a mediana ser calculada só no treino, como faz o `SimpleImputer` dentro do `Pipeline`.

## 6. Em uma matriz didática com TN=80, FP=5, FN=10, TP=5, calcule acurácia e sensibilidade. O resultado é suficiente para aprovar o modelo?

**Resposta:**
- Total = 80 + 5 + 10 + 5 = 100
- Acurácia = (TN + TP) / total = (80 + 5) / 100 = **0,85**
- Sensibilidade = TP / (TP + FN) = 5 / (5 + 10) = 5 / 15 ≈ **0,33**

Não basta. Existem 15 positivos reais (FN + TP) e 85 negativos. Um modelo que dissesse "negativo" para todo mundo acertaria 85 de 100, exatamente a mesma acurácia, sem fazer nada. Este modelo encontra só 1 em cada 3 positivos. Antes de aprovar, eu compararia com essa referência, veria quanto custa cada falso negativo e testaria em outros dados.

## 7. Valores reais 100, 120, 140 e previsões 110, 115, 130. Calcule MAE e informe a unidade se o alvo for vendas em reais.

**Resposta:**

| Real | Previsto | Erro absoluto |
| --- | --- | --- |
| 100 | 110 | 10 |
| 120 | 115 | 5 |
| 140 | 130 | 10 |

MAE = (10 + 5 + 10) / 3 = 25 / 3 ≈ **R$ 8,33**. Em média, cada previsão erra cerca de R$ 8,33, para mais ou para menos.

## 8. Um R² de -0,2 significa “20% de acertos negativos”? Explique.

**Resposta:** Não, porque R² nunca foi porcentagem de acertos. Ele compara o erro do modelo com o erro de prever sempre a média: R² = 1 − (erro² do modelo / erro² da média). Se R² = −0,2, então erro² do modelo / erro² da média = 1,2. Ou seja, o modelo erra 20% **a mais** do que alguém que só chutasse a média. É um sinal de que o modelo é pior que nada.

## 9. Uma árvore tem acurácia 1,00 no treino e 0,65 na validação. Que hipótese investigar e como?

**Resposta:** A hipótese principal é **sobreajuste**: a árvore cresceu até decorar cada registro do treino (por isso 100%), mas essas regras não valem para dados novos. Como investigar: repetir a validação cruzada no treino limitando `max_depth` e aumentando `min_samples_leaf` e ver se a distância entre treino e validação diminui sem a validação cair. No meu laboratório, a árvore sem limite e com folha 5 teve 0,87 no treino e 0,71 na validação; com folha 40 a distância caiu para 0,05. Também vale conferir se algum atributo funciona como identificador (como um código do aluno) e comparar com a referência.

## 10. Por que escolher a profundidade pelo teste prejudica a estimativa final?

**Resposta:** Porque, ao testar várias profundidades no teste e ficar com a melhor, eu estou usando o teste para treinar uma decisão. A profundidade escolhida fica ajustada às particularidades daqueles 150 registros, e a acurácia final passa a ser uma estimativa otimista. O teste só vale como "prova" se for usado uma vez, depois de todas as escolhas. Para escolher, uso validação dentro do treino.

## 11. Baixa frequência associada à evasão demonstra causa? Proponha explicação alternativa.

**Resposta:** Não. Duas explicações alternativas: (1) **causa comum**: o estudante conseguiu um emprego com horário que choca com a aula; isso reduz a frequência e, mais tarde, o leva a sair. A frequência baixa é um sintoma, não a causa. (2) **causalidade invertida**: o estudante já decidiu trancar ou sair e por isso parou de ir. Nos dois casos, obrigar a presença não resolveria a evasão.

## 12. Um modelo sinaliza um estudante como possível evasão. Que ação responsável pode ser adotada?

**Resposta:** Uma pessoa da equipe de apoio olha o caso antes de qualquer coisa. Se fizer sentido, o estudante recebe um convite opcional e acolhedor (conversa, monitoria, informação sobre bolsas e auxílios), sem a palavra "risco" e sem nenhuma consequência na nota ou na matrícula. Ele pode recusar, perguntar por que foi contatado e corrigir os dados. A informação fica restrita à equipe de apoio e é apagada depois.

## Fontes adicionais consultadas

**Material do Módulo IV (Profa. Kadidja Valéria, UDF, 2026); SCIKIT-LEARN. *User Guide* e *Common pitfalls and recommended practices*. Disponível em: https://scikit-learn.org/stable/. Acesso em: 30 out. 2026. Uso de IA: usei um assistente de IA (Claude, da Anthropic) para apoiar a redação, montar os notebooks e conferir os cálculos; revisei as respostas e sou responsável pelo conteúdo.**

[Voltar ao início](README.md).
