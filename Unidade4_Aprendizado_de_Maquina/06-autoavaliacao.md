<img src="assets/logo-udf.jpg" alt="UDF Centro Universitário" width="230">

**Profa. Kadidja Valéria | UDF**  
Ciência de Dados e Aprendizado de Máquina · Sistemas de Informação · 2026.2

# Autoavaliação e conferência da entrega

## Identificação

- Estudante ou equipe: **Henrique Ribeiro Leonardo**
- Turma: **Sistemas de Informação — 2026.2**
- Data de realização: **30/10/2026**
- Integrantes e contribuições (se em equipe): **Individual.**

## Checklist

- [x] Diferenciei IA, Ciência de Dados e ML com um exemplo.
- [x] Completei o quadro supervisionado/não supervisionado.
- [x] Justifiquei pelo menos cinco situações-problema.
- [x] Registrei a investigação da biblioteca.
- [x] Identifiquei atributos, alvo, unidade e momento da previsão.
- [x] Executei e documentei a prática em Python ou Orange.
- [x] Escolhi configurações usando treino/validação.
- [x] Mantive o teste fora do ajuste e da seleção.
- [x] Interpretei acurácia, matriz, MAE e R².
- [x] Comparei com uma referência e discuti erros.
- [x] Registrei limitações, dados sintéticos, privacidade e vieses.
- [x] Formulei recomendações de apoio com revisão humana.
- [x] Respondi às questões individuais.
- [x] Conferi os links e os arquivos de evidências.
- [x] Substituí os campos PREENCHER ou justifiquei os não aplicáveis.

## Reflexão individual

- O que aprendi e consigo explicar: **A diferença entre escrever regras e deixar o modelo aprender com exemplos; quando o problema é classificação, regressão ou agrupamento; por que dividir os dados antes de qualquer preparação; e como ler uma matriz de confusão sem me deixar enganar pela acurácia. O que mais me marcou foi ver na prática o sobreajuste: a árvore sem limite chegou a 87% no treino e ficou em 71% na validação.**
- Qual foi minha principal dificuldade: **Aceitar que, quando várias configurações empatam dentro do desvio, "a maior média" não é automaticamente a melhor escolha. Precisei definir uma regra de desempate antes de olhar o teste para não ficar tentado a escolher pelo resultado final.**
- Qual evidência mostra meu avanço: **O [notebook do laboratório](notebooks/laboratorio-henrique.ipynb) com a grade completa de parâmetros; os cálculos manuais da matriz (117/150 = 0,78 e sensibilidade 47/61 ≈ 0,77) no [registro do laboratório](03-aula2-laboratorio.md); e o [experimento do TCC](07-aplicacao-tcc-rag.md), em que apliquei o mesmo método a um problema meu.**
- Como contribuímos com a equipe: **Fiz a atividade individualmente. Levei o conteúdo para o meu TCC, que faço em dupla com o Pedro Luiz Oliveira da Costa: o roteador de perguntas da atividade 07 é uma proposta para levar à dupla.**
- O que preciso revisar: **Calibração de probabilidades (o Naive Bayes do experimento do TCC deu confiança 0,81 para uma pergunta que era claramente ambígua), validação com divisão no tempo e métricas para classes muito desbalanceadas.**
- Ferramentas de apoio utilizadas, incluindo IA quando houver, e como verifiquei as respostas: **Python com scikit-learn 1.9.1, pandas e matplotlib. Usei um assistente de IA (Claude, da Anthropic) para apoiar a escrita dos textos e montar os notebooks. Conferi os números executando os notebooks com a semente 42 e refazendo as contas da matriz e do MAE à mão.**

## Critérios de avaliação

Escala sugerida do material: nível 3 consistente, 2 adequado com lacunas, 1 parcial, 0 ausente/incoerente. Nota do critério = peso × nível/3. A professora pode ajustar a aplicação.

| Critério | Peso aula 1 | Peso aula 2/PBL |
| --- | --- | --- |
| Problema e conceitos | 3,0 | 2,0 |
| Dados e justificativa | 2,0 | 2,0 |
| Método e avaliação | 1,0 | 3,0 |
| Interpretação e responsabilidade | 2,0 | 2,0 |
| Clareza e colaboração | 2,0 | 1,0 |
| Total | 10,0 | 10,0 |

Na aula 1, método corresponde à avaliação proposta. Na aula 2, inclui execução e interpretação. A maior acurácia isolada não assegura a melhor avaliação da atividade.

## Fontes de apoio

- SCIKIT-LEARN. *User Guide*. https://scikit-learn.org/stable/user_guide.html.
- SCIKIT-LEARN. *Common pitfalls and recommended practices*. https://scikit-learn.org/stable/common_pitfalls.html.
- ORANGE DATA MINING. *Test and Score*. https://orangedatamining.com/widget-catalog/evaluate/testandscore/.

Referências indicadas no material didático do módulo. Consultadas por mim em 30 out. 2026.

[Voltar ao início](README.md).
