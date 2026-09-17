# Definição do Projeto de Ciência de Dados

**Unidade:** III - Gestão de Projetos
**Metodologia:** PBL + trabalho em equipes
**Entregável:** Documento de definição do projeto

> **Nota de preenchimento:** este documento foi montado a partir do projeto de assistente RAG local já definido pela equipe. Campos entre `[colchetes]` dependem de informação que só a equipe possui. Se a disciplina de Gestão de Projetos exigir um projeto diferente do TCC, o conteúdo precisa ser substituído.

## 1. Identificação do projeto

| Campo | Preenchimento |
|---|---|
| Título provisório do projeto | Avaliação de desempenho de assistentes conversacionais locais baseados em RAG para consulta a documentos sensíveis |
| Curso / disciplina | Ciência da Computação — Gestão de Projetos (Unidade III) |
| Turma | [PREENCHER] |
| Equipe | [NOME DA EQUIPE, se houver] |
| Integrantes e funções iniciais | Henrique Ribeiro Leonardo — [função]; Pedro Luiz Oliveira da Costa — [função] |
| Professor(a) | [PREENCHER] |
| Data de elaboração | [PREENCHER] |
| Versão do documento | 1.0 |

## 2. Visão geral

### 2.1 Resumo do projeto

Organizações que lidam com documentos sensíveis não podem enviar esse conteúdo a serviços de IA em nuvem, o que as exclui do uso de assistentes de consulta documental. O projeto construirá um assistente que roda inteiramente na máquina do usuário, combinando recuperação de informação com modelos de linguagem de pequeno porte, e medirá seu desempenho em duas dimensões: qualidade das respostas e custo computacional. O resultado esperado é um conjunto de dados de desempenho que permita a um gestor de TI decidir se a execução local é viável no hardware de que dispõe.

### 2.2 Declaração do projeto em uma frase

> Nosso projeto utilizará **medições de qualidade de resposta e de custo computacional coletadas em execuções controladas** para compreender **o compromisso entre privacidade, qualidade e desempenho em assistentes RAG locais**, apoiando **organizações que lidam com documentos sensíveis e não dispõem de GPU dedicada** na decisão de **adotar ou não uma solução de consulta documental executada internamente**.

## 3. Contexto e definição do problema

### 3.1 Contexto

O uso de modelos de linguagem para consultar acervos documentais consolidou-se em torno de serviços hospedados em nuvem. Para obter uma resposta fundamentada em um documento, o conteúdo desse documento precisa ser transmitido a um servidor de terceiros.

- **Onde o problema ocorre?** Em organizações que mantêm acervos de acesso restrito — escritórios de advocacia, clínicas, setores de RH, órgãos públicos, áreas de compliance.
- **Quem é afetado?** Profissionais que precisam localizar informação em grandes volumes de documentos internos e não podem transmiti-los externamente.
- **Quais sinais indicam sua existência?** Medeiros e Oliveira (2025) registram que o uso de modelos proprietários acessados via API levanta preocupações quanto à segurança de dados sensíveis, e concluem que modelos de código aberto são alternativa viável nesse cenário.
- **Por que investigar agora?** Modelos de pequeno porte tornaram a execução local tecnicamente plausível, mas o custo real dessa escolha em máquinas comuns não está medido na literatura nacional.

### 3.2 Problema central

> Organizações que lidam com documentos sensíveis enfrentam a impossibilidade de usar assistentes de consulta documental baseados em IA no contexto de obrigações de sigilo que vedam a transmissão de dados a terceiros, produzindo dependência de busca manual em acervos extensos.

### 3.3 Evidências iniciais

| Evidência | Fonte | O que ela indica? | Confiabilidade / limitação |
|---|---|---|---|
| 1. Modelos de código aberto são alternativa viável quando a privacidade dos dados é aspecto importante; embeddings proprietários via API levantam preocupações de segurança com dados sensíveis | MEDEIROS; OLIVEIRA (2025), SEMISH/SBC | Há caminho técnico para execução local sem perda proibitiva de qualidade | Artigo revisado por pares; não mede custo computacional em inferência nem declara hardware |
| 2. Pipeline RAG com modelos de pequeno porte atinge desempenho competitivo com uso reduzido de recursos | OLIVERA et al. (2025), SBBD/SBC | Modelos pequenos são suficientes para a tarefa | Experimentos conduzidos em GPU dedicada de 24 GB; não representa o cenário-alvo |
| 3. Avaliação automática de sistemas RAG por LLM-juiz teve concordância limitada com especialistas em formato de avaliação direta, subindo apenas no formato pareado | MIYAJI et al. (2025), STIL/SBC | O protocolo de avaliação precisa de desenho cuidadoso | Amostra de 50 perguntas, um avaliador por tarefa; domínio corporativo específico |

## 4. Público-alvo e partes interessadas

### 4.1 Público-alvo principal

| Aspecto | Descrição |
|---|---|
| Quem são os usuários ou beneficiários? | Profissionais que consultam acervos documentais restritos, e os gestores de TI responsáveis por aprovar ferramentas |
| Quais necessidades possuem? | Localizar informação específica em documentos extensos sem violar obrigações de sigilo |
| Como são afetados pelo problema? | Recorrem a busca manual ou por palavra-chave, com alto custo de tempo, ou usam ferramentas externas assumindo risco de conformidade |
| Que decisão poderão tomar com os resultados? | Adotar, adaptar ou descartar a execução local, com base no desempenho medido no hardware de que dispõem |

### 4.2 Partes interessadas

| Parte interessada | Interesse no projeto | Influência | Forma de envolvimento |
|---|---|---|---|
| Professora orientadora | Qualidade acadêmica e cumprimento do cronograma | Alta | Reuniões de orientação e validação das entregas |
| Gestores de TI de organizações com dados restritos | Viabilidade prática e custo de infraestrutura | Média | Público dos resultados; possível validação qualitativa |
| Comunidade acadêmica de PLN em português | Dados de desempenho sob restrição de hardware | Baixa | Publicação dos resultados e do código |

## 5. Objetivos do projeto

### 5.1 Objetivo geral

Avaliar o desempenho de um assistente conversacional baseado em geração aumentada por recuperação, executado integralmente em hardware sem GPU dedicada, quanto à qualidade das respostas e ao custo computacional, no contexto de consulta a documentos sensíveis.

### 5.2 Objetivos específicos

| Nº | Objetivo específico | Evidência de conclusão |
|---:|---|---|
| 1 | Levantar e fichar a produção nacional sobre RAG e modelos de pequeno porte em português | Planilha de registro e caderno de fichamentos preenchidos |
| 2 | Construir a base documental e o conjunto de perguntas de teste com respostas de referência | Base indexada e conjunto de teste versionado |
| 3 | Implementar o pipeline RAG de execução integralmente local | Protótipo funcional com documentação UML |
| 4 | Medir qualidade das respostas e custo computacional para cada modelo avaliado | Tabela de resultados com todas as métricas coletadas |
| 5 | Analisar o compromisso entre privacidade, qualidade e custo | Seção de discussão com recomendação fundamentada |

### 5.3 Verificação dos objetivos

- [x] São específicos e escritos com clareza.
- [x] Podem ser verificados por meio de entregáveis ou métricas.
- [ ] São viáveis com os dados, recursos e tempo disponíveis. *(confirmar após definir a máquina de referência)*
- [x] Estão diretamente relacionados ao problema central.
- [x] Consideram os usuários e a decisão que será apoiada.

## 6. Perguntas de negócio

| Nº | Pergunta de negócio | Decisão apoiada | Dados necessários | Análise ou indicador possível |
|---:|---|---|---|---|
| 1 | Qual a qualidade das respostas obtida com execução local em comparação com o padrão esperado pelo usuário? | Adotar ou não a solução local | Respostas geradas, respostas de referência, trechos recuperados | Fidelidade ao contexto e relevância da resposta |
| 2 | Quanto tempo o usuário espera por uma resposta em uma máquina sem GPU? | Definir se a experiência de uso é aceitável | Registros de latência por consulta | Tempo até o primeiro token e latência total (mediana e percentil 95) |
| 3 | Qual configuração de hardware é o mínimo necessário para operar a solução? | Dimensionar a infraestrutura | Pico de memória e uso de CPU por execução | Consumo máximo de RAM por configuração |
| 4 | Qual modelo oferece o melhor equilíbrio entre qualidade e custo? | Escolher o modelo a implantar | Resultados cruzados de qualidade e custo | Comparação qualidade × latência por modelo |
| 5 | Quantos trechos recuperados compensam ser incluídos antes de o ganho deixar de justificar o custo? | Configurar o parâmetro de recuperação | Revocação e contagem de tokens por valor de top-n | Curva de revocação × custo, com ponto de inflexão |

## 7. Hipóteses iniciais

| Hipótese | Como poderá ser testada? | Resultado que a refutaria? |
|---|---|---|
| H1. Modelos de pequeno porte executados localmente atingem qualidade aceitável para consulta documental | Comparar as métricas de qualidade contra um limiar definido com a orientadora antes dos testes | Qualidade abaixo do limiar em todas as configurações testadas |
| H2. A latência em hardware sem GPU permanece dentro de um limite tolerável para uso interativo | Medir a latência total por consulta em repetições suficientes para estimar variabilidade | Latência mediana acima do limite definido como tolerável |
| H3. O ganho de qualidade ao aumentar o número de trechos recuperados estabiliza antes de o custo se tornar proibitivo | Variar o top-n e registrar qualidade e custo em cada valor | Ganho crescendo de forma proporcional ao custo, sem ponto de estabilização |

## 8. Dados necessários e viabilidade

| Conjunto ou fonte de dados | Variáveis principais | Formato | Acesso / responsável | Qualidade esperada |
|---|---|---|---|---|
| Corpus documental de teste | Texto do documento, metadados, identificador do trecho | PDF / texto | [DEFINIR — ver 8.1] | Boa; documentos estruturados e revisados |
| Conjunto de perguntas de teste | Pergunta, resposta de referência, trecho-fonte | CSV / JSON | Equipe | Depende do cuidado na elaboração |
| Registros de execução | Latência, tokens por segundo, pico de memória, modelo, configuração | CSV gerado em log | Equipe | Alta; coleta automatizada |
| Resultados de avaliação de qualidade | Pontuação por métrica, por pergunta e por configuração | CSV | Equipe | Depende do protocolo de avaliação |

### 8.1 Avaliação inicial dos dados

- **Disponibilidade:** os registros de execução e de avaliação são gerados pelo próprio experimento. O corpus é a única dependência externa.
- **Volume e período coberto:** [DEFINIR — número de documentos e de perguntas de teste.]
- **Dados ausentes, duplicados ou inconsistentes previstos:** falhas pontuais de execução podem gerar registros incompletos; documentos digitalizados sem camada de texto exigiriam OCR.
- **Necessidade de integração entre fontes:** os registros de custo e de qualidade precisam ser unidos pelo identificador da pergunta e da configuração.
- **Restrições legais, contratuais ou institucionais:** usar documentos efetivamente sensíveis exigiria autorização formal e possivelmente aprovação ética. **Recomendação:** adotar um acervo público com as mesmas características estruturais — linguagem técnica, formato padronizado, terminologia de domínio — o que preserva a validade do experimento e permite publicar os resultados sem restrição.

### 8.2 Privacidade, ética e segurança

- [x] A equipe verificou se há dados pessoais ou sensíveis.
- [x] A coleta e o uso dos dados possuem finalidade legítima e explícita.
- [x] O acesso será limitado às pessoas autorizadas.
- [x] Dados pessoais serão minimizados, anonimizados ou pseudonimizados quando necessário.
- [ ] Possíveis vieses e impactos sobre grupos serão analisados. *(a definir: como tratar desempenho desigual entre tipos de consulta)*
- [x] A divulgação dos resultados evitará reidentificação ou exposição indevida.

**Cuidados específicos deste projeto:** o projeto evita o problema na origem ao usar corpus público no experimento. Há, porém, um ponto de atenção: se a avaliação de qualidade recorrer a um modelo externo como juiz, isso ocorre apenas na etapa de análise e sobre dados públicos — nunca em operação real com documentos sensíveis. Essa distinção precisa ficar explícita no relatório, sob pena de a proposta parecer contraditória.

## 9. Escopo do projeto

| Dentro do escopo | Fora do escopo |
|---|---|
| Implementação de pipeline RAG com execução integralmente local | Treinamento ou ajuste fino de modelos |
| Medição de qualidade das respostas e de custo computacional | Proposição de nova técnica de recuperação ou geração |
| Comparação entre modelos de pequeno porte, mantendo os demais componentes constantes | Estudo de vetores de ataque ou vazamento pelo corpus indexado |
| Documentação UML da solução | Parecer jurídico sobre conformidade com a LGPD |
| Recomendação fundamentada de configuração | Implantação em ambiente de produção real |

**Restrições conhecidas:** prazo de um semestre; ausência de GPU dedicada, que é condição do experimento e não limitação a contornar; acesso restrito a documentos efetivamente sensíveis; equipe de dois integrantes acumulando desenvolvimento e análise.

## 10. Resultados e entregáveis previstos

| Entregável | Descrição | Formato | Responsável | Critério de aceite |
|---|---|---|---|---|
| Base tratada | Corpus segmentado, vetorizado e indexado | Banco vetorial + script de ingestão | [DEFINIR] | Reproduzível a partir do script, sem ajuste manual |
| Análise exploratória | Caracterização do corpus e do conjunto de perguntas | Notebook | [DEFINIR] | Cobre extensão dos documentos, distribuição dos trechos e tipos de pergunta |
| Visualizações / painel | Gráficos de qualidade × custo por modelo e curva de revocação × top-n | Figuras no relatório | [DEFINIR] | Permitem comparar modelos sem consultar as tabelas |
| Relatório ou apresentação | Monografia e defesa oral | PDF (ABNT) + slides | Ambos | Conforme o Regulamento de TC do UDF |
| Protótipo | Assistente funcional executável localmente | Repositório com README | [DEFINIR] | Executa em máquina limpa seguindo o README |

## 11. Critérios de sucesso

| Critério | Indicador ou evidência | Meta | Forma de verificação |
|---|---|---|---|
| Relevância para o problema | Perguntas de negócio respondidas com dados coletados | 5 de 5 | Conferência na seção de resultados |
| Qualidade dos dados | Execuções válidas sobre o total de execuções | ≥ 95% | Contagem nos registros |
| Qualidade da análise | Métricas reportadas com medida de dispersão, não apenas média | Todas | Revisão da tabela de resultados |
| Utilidade para o público-alvo | Recomendação explícita de configuração mínima de hardware | Presente | Seção de discussão |
| Comunicação dos resultados | Aprovação pela banca | Nota ≥ 6,0 | Parecer da Banca Examinadora |

## 12. Plano inicial de trabalho

| Etapa | Atividades principais | Responsável(is) | Prazo | Dependências |
|---|---|---|---|---|
| 1. Definição | Delimitar escopo, definir modelos e máquina de referência | Ambos | [DEFINIR] | — |
| 2. Obtenção dos dados | Selecionar e coletar o corpus; elaborar as perguntas de teste | [DEFINIR] | [DEFINIR] | Etapa 1 |
| 3. Preparação dos dados | Segmentar, vetorizar e indexar; validar a recuperação | [DEFINIR] | [DEFINIR] | Etapa 2 |
| 4. Análise / modelagem | Executar o protocolo de medição para cada configuração | [DEFINIR] | [DEFINIR] | Etapa 3 |
| 5. Validação | Conferir consistência, repetir execuções discrepantes | Ambos | [DEFINIR] | Etapa 4 |
| 6. Comunicação | Redigir a monografia e preparar a defesa | Ambos | [DEFINIR] | Etapa 5 |

## 13. Riscos do projeto

| Risco | Probabilidade | Impacto | Estratégia de resposta | Responsável |
|---|---|---|---|---|
| Desempenho local inviável para uso interativo | Média | Médio | Resultado negativo ainda é resultado válido; relatar o limite encontrado em vez de forçar conclusão favorável | Ambos |
| Conjunto de perguntas de teste pequeno demais para sustentar conclusões | Alta | Alto | Dimensionar o conjunto no início e declarar a limitação explicitamente no relatório | [DEFINIR] |
| Protocolo de avaliação de qualidade divergir do julgamento humano | Média | Alto | Adotar formato pareado e validar uma amostra manualmente | [DEFINIR] |
| Escopo crescer com a inclusão de novos modelos ou métricas | Alta | Médio | Congelar a lista de configurações ao fim da etapa 1 | Ambos |
| Concentração de conhecimento técnico em um integrante | Média | Alto | Revisão cruzada de código e rodízio nas execuções | Ambos |
| Corpus indisponível ou inadequado | Baixa | Alto | Selecionar o corpus já na etapa 1, com alternativa definida | [DEFINIR] |

## 14. Organização da equipe

| Integrante | Papel principal | Responsabilidades | Apoio necessário |
|---|---|---|---|
| Henrique Ribeiro Leonardo | [DEFINIR] | [DEFINIR] | [DEFINIR] |
| Pedro Luiz Oliveira da Costa | [DEFINIR] | [DEFINIR] | [DEFINIR] |

> **Atenção:** o Regulamento de TC do UDF prevê que a avaliação é individual mesmo em trabalhos de grupo, e que integrantes que não cumprirem as atividades podem ser reprovados. Registrem aqui a divisão real, não uma divisão simbólica.

## 15. Validação da definição do projeto

- [x] O problema é real, relevante e delimitado.
- [x] O público-alvo e as partes interessadas estão identificados.
- [x] O objetivo geral e os objetivos específicos são coerentes.
- [x] As perguntas de negócio orientam decisões concretas.
- [ ] Há dados potencialmente disponíveis para responder às perguntas. *(pendente: definir o corpus)*
- [ ] O escopo é compatível com o prazo e os recursos. *(pendente: confirmar após fixar a lista de configurações)*
- [x] Os critérios de sucesso são mensuráveis.
- [x] Riscos, privacidade, ética e segurança foram considerados.
- [ ] Funções e responsabilidades foram distribuídas. *(pendente: seção 14)*

## 16. Aprovação e registro de ajustes

| Responsável | Validação / observação | Data |
|---|---|---|
| Representante da equipe | | |
| Professor(a) / orientador(a) | | |

### Ajustes solicitados após a apresentação inicial

________________________________________________________________________________

________________________________________________________________________________
