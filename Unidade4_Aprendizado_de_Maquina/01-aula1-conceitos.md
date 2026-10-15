<img src="assets/logo-udf.jpg" alt="UDF Centro Universitário" width="230">

**Profa. Kadidja Valéria | UDF**  
Ciência de Dados e Aprendizado de Máquina · Sistemas de Informação · 2026.2

# Aula 1 — Conceitos e classificação de problemas

## Identificação

- Estudante ou equipe: **Henrique Ribeiro Leonardo**
- Turma: **Sistemas de Informação — 2026.2**
- Data de realização: **30/10/2026**
- Integrantes e contribuições (se em equipe): **Atividade individual.**

## Objetivos

Distinguir programação tradicional e Machine Learning, identificar atributos e alvo e diferenciar classificação, regressão e agrupamento.

## 1. Explicação com suas palavras

1. Como um modelo aprende com dados? **Na programação tradicional eu escrevo a regra e o computador aplica. No aprendizado de máquina eu entrego exemplos e o algoritmo descobre a regra. Ele começa com um palpite, compara o que previu com o resultado real de cada exemplo e vai corrigindo seus parâmetros até o erro ficar pequeno. "Aprender", aqui, é isso: ajustar números para errar menos nos exemplos conhecidos. Só sei se aprendeu de verdade quando testo com exemplos que ele nunca viu.**
2. Qual diferença entre algoritmo e modelo? **O algoritmo é a receita; o modelo é o bolo pronto. Árvore de decisão é um algoritmo: um jeito de montar perguntas a partir dos dados. A árvore que saiu do meu laboratório, com a pergunta "nota ≤ 6,21?" no topo, é o modelo. Com outro conjunto de dados, o mesmo algoritmo gera outro modelo.**
3. Compare uma regra de bloqueio de palavra com um modelo de spam. **A regra ("se tiver 'ganhe dinheiro', vai para o spam") é previsível e fácil de auditar, mas é cega ao contexto: barra um e-mail legítimo que cita a frase e deixa passar quem escreve "g4nhe d1nheiro". Também precisa de alguém atualizando a lista o tempo todo. O modelo aprende com milhares de mensagens já marcadas e pesa vários sinais ao mesmo tempo (palavras, links, remetente, formato). Ele se adapta melhor quando o golpe muda, mas depende de rótulos bons e é mais difícil explicar por que uma mensagem foi barrada.**
4. Dê um exemplo de atributo e alvo e defina o momento da previsão. **Exemplo de um app de mobilidade: atributos = horário, dia da semana, distância e região de embarque; alvo = se a corrida será cancelada pelo passageiro (sim/não). O momento da previsão é quando a corrida é aceita. Só posso usar o que já se sabe nesse instante; o tempo de espera real, por exemplo, ainda não existe e não pode entrar como atributo.**

## 2. Quadro comparativo

| Critério | Supervisionado | Não supervisionado |
| --- | --- | --- |
| Presença de alvo no treino | Tem. Cada exemplo vem com a resposta certa anotada. | Não tem. Só as características dos registros. |
| Pergunta que pode responder | "Para este caso novo, qual é a resposta?" | "Como esses registros se organizam? O que é parecido com o quê?" |
| Tipo de saída | Uma classe (classificação) ou um número (regressão). | Grupos, uma estrutura ou registros fora do padrão. |
| Tarefas e exemplo | Classificar e-mail em spam/legítimo; prever o consumo de energia do mês. | Separar clientes em perfis de compra; achar transações estranhas. |
| Dados necessários | Histórico em que o desfecho foi registrado de forma confiável. | Atributos que façam sentido comparar entre si, na mesma escala. |
| Forma de avaliação | Comparar previsão e resposta real em dados separados (acurácia, matriz de confusão, MAE, R²). | Não há gabarito: medidas internas como silhueta e, principalmente, se os grupos fazem sentido para quem vai usá-los. |
| Limitação | Rotular custa caro e o rótulo pode carregar viés ou erro. | Os grupos sempre "aparecem", mesmo quando não significam nada útil. |

## 3. Situações-problema

| Caso | Situação-problema |
| --- | --- |
| 1 Educação | Prever evadiu/permaneceu com histórico rotulado de turmas anteriores. |
| 2 Saúde | Estimar o tempo de espera em minutos a partir de registros de atendimento. |
| 3 Comércio | Descobrir perfis de compra sem categorias prévias de clientes. |
| 4 Finanças | Prever inadimplente/adimplente com contratos e desfechos conhecidos. |
| 5 Segurança digital | Distinguir spam/legítima com mensagens já revisadas. |
| 6 Comércio | Estimar o total de vendas em reais na próxima semana. |
| 7 Educação | Agrupar perfis de acesso ao ambiente virtual sem rótulo de evasão. |
| 8 Saúde | Classificar exames em categorias previamente definidas por especialistas. |

| Caso escolhido | Alvo ou ausência de alvo | Categoria, quantidade ou grupos? | Abordagem e justificativa | Dados necessários e limitação |
| --- | --- | --- | --- | --- |
| 2 Saúde | Alvo: minutos de espera | Quantidade | Supervisionado, **regressão**. A resposta é um número contínuo, e o histórico de atendimentos já registra quanto cada paciente esperou. | Hora de chegada, dia, classificação de risco, médicos de plantão, fila no momento. Limitação: a espera depende de casos graves que chegam sem aviso; o erro médio pode ser bom e ainda assim errar muito em dias atípicos. |
| 3 Comércio | Sem alvo | Grupos | Não supervisionado, **agrupamento**. Ninguém definiu antes quais são os perfis; o objetivo é descobri-los. | Frequência de compra, ticket médio, categorias, canal (loja ou site). Limitação: se eu mudar os atributos ou a escala, os grupos mudam; quem decide se um grupo é útil é o time de marketing, não o algoritmo. |
| 4 Finanças | Alvo: inadimplente/adimplente | Categoria | Supervisionado, **classificação**. Contratos antigos já têm o desfecho conhecido. | Renda declarada, valor e prazo do contrato, histórico de pagamento. Limitação: só aprende com quem teve crédito aprovado (quem foi recusado nunca gerou desfecho), e atributos podem reproduzir discriminação. |
| 5 Segurança digital | Alvo: spam/legítima | Categoria | Supervisionado, **classificação**, com as mensagens revisadas servindo de rótulo. | Texto, links, remetente, horário de envio. Limitação: quem manda spam muda a estratégia, então o modelo envelhece rápido e precisa ser retreinado. |
| 6 Comércio | Alvo: vendas em R$ | Quantidade | Supervisionado, **regressão**. O alvo é um valor em reais. | Vendas das semanas anteriores, feriados, promoções, clima. Limitação: o teste tem que vir depois do treino no tempo; sortear semanas misturaria passado e futuro. |
| 7 Educação | Sem alvo (não há rótulo de evasão) | Grupos | Não supervisionado, **agrupamento** de padrões de acesso ao AVA. | Dias e horários de acesso, tempo logado, materiais abertos. Limitação: "acessa pouco" não quer dizer "vai evadir"; usar o grupo como se fosse diagnóstico seria um erro. |
| 8 Saúde | Alvo: categoria definida por especialistas | Categoria | Supervisionado, **classificação** com rótulos dados por médicos. | Exames com laudo confirmado. Limitação: um falso negativo pode ser grave; o modelo deve apoiar o médico, não substituir o laudo. |

## 4. Raciocínio crítico

“Detectar fraude” define sozinho o tipo de aprendizado? **Não. O nome do problema não diz qual técnica usar; o que decide é o dado que eu tenho. Se o banco guardou transações já investigadas e marcadas como "fraude" ou "legítima", dá para treinar um classificador supervisionado. Ele fica bom em reconhecer golpes parecidos com os antigos, mas tem dois problemas: fraude é rara (o modelo pode "acertar" 99% só dizendo que nada é fraude) e golpes novos não aparecem no histórico. Se não existem rótulos, posso procurar transações que fogem do padrão do cliente (detecção de anomalias). Isso pega golpes novos, mas também acusa a compra legítima e incomum, como uma viagem. Na prática, o mais sensato é combinar os dois e manter uma pessoa revisando os alertas.**

## 5. Ligação com meu trabalho

No TCC, eu e o Pedro construímos um assistente RAG que roda em computador sem GPU. Três pontos do projeto viram problemas de ML:

| Problema | Alvo | Tipo | Abordagem |
| --- | --- | --- | --- |
| Saber de qual coleção de documentos é a pergunta | Coleção (RH, jurídico, financeiro, TI ou fora do escopo) | Categoria | Classificação supervisionada. Testei isso na [atividade 07](07-aplicacao-tcc-rag.md). |
| Estimar quantos segundos o SLM vai levar para responder | Tempo em segundos | Quantidade | Regressão, com tamanho da pergunta, trechos recuperados e modelo usado. |
| Organizar documentos sem pasta definida | Sem alvo | Grupos | Agrupamento dos embeddings dos documentos. |

## Entrega

Salve este arquivo preenchido. Critérios: distinção conceitual, pertinência dos dados, justificativa e clareza. [Voltar ao início](README.md).
