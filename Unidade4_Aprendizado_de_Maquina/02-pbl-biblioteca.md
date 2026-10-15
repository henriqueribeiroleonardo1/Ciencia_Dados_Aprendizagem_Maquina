<img src="assets/logo-udf.jpg" alt="UDF Centro Universitário" width="230">

**Profa. Kadidja Valéria | UDF**  
Ciência de Dados e Aprendizado de Máquina · Sistemas de Informação · 2026.2

# PBL — Biblioteca em Foco

## Identificação

- Estudante ou equipe: **Henrique Ribeiro Leonardo**
- Turma: **Sistemas de Informação — 2026.2**
- Data de realização: **30/10/2026**
- Integrantes e contribuições (se em equipe): **Atividade feita individualmente.**

## Situação-problema

Uma biblioteca universitária enfrenta filas em horários específicos e baixa utilização de alguns serviços. A coordenação deseja melhorar o atendimento e planejar recursos. Este é um cenário didático.

**Público-alvo:** estudantes usuários, equipe de atendimento e gestão.

**Questão norteadora:** como os dados podem orientar o planejamento da biblioteca e a oferta de serviços sem identificar ou discriminar seus usuários?

## Investigação em equipe

1. Delimitem o problema e a decisão a apoiar.
2. Registrem o que já sabem e o que precisam investigar.
3. Formulem duas perguntas de negócio.
4. Definam a unidade de análise, os atributos e o alvo, quando houver.
5. Justifiquem a abordagem e indiquem se uma análise descritiva já seria suficiente.
6. Proponham avaliação, cuidados com os dados e limitações.

## Canvas da equipe

| Campo | Registro |
| --- | --- |
| Problema e decisão | Existem dois problemas diferentes que não devem ser misturados: **fila** (falta de gente no balcão em certas horas) e **serviço ocioso** (pouca procura por, por exemplo, reserva de salas ou empréstimo de notebooks). Decisões: montar a escala semanal do balcão e decidir o que fazer com cada serviço pouco usado (divulgar, mudar o horário ou encerrar). |
| Público-alvo | Estudantes (esperar menos e conhecer os serviços), atendentes (escala que acompanha o movimento) e coordenação (gastar o orçamento onde há demanda). |
| O que sabemos | As filas se concentram em alguns horários; parte dos serviços tem pouca procura; o sistema da biblioteca registra empréstimos e devoluções com data e hora. |
| O que precisamos investigar | Se a fila é por excesso de gente ou por um atendimento lento (por exemplo, renovação que só pode ser feita no balcão); se os serviços ociosos são desconhecidos ou simplesmente não interessam; quanto o calendário (provas, TCC) muda o movimento. |
| Pergunta de negócio 1 | Quantos atendimentos no balcão devemos esperar em cada bloco de uma hora da próxima semana? |
| Pergunta de negócio 2 | Que padrões de uso existem entre os serviços (quem usa sala de estudo também pega livro? quem só devolve?), olhando apenas números agregados, e que serviço faz sentido divulgar para cada padrão? |
| Unidade de análise e período | P1: um bloco de 1 hora em um dia, nos dois últimos semestres. P2: uma visita (entrada até saída), sem ligar a visita a uma pessoa, no mesmo período. |
| Atributos, unidades e origem pretendida | Dia da semana, hora, semana do semestre (início, provas, entrega de TCC, férias), atendimentos por hora (sistema de empréstimo), entradas por hora (catraca), número de atendentes na escala (RH), reservas de sala e de equipamento (sistema de reservas). |
| Alvo e momento em que será conhecido, ou ausência de alvo | P1: alvo = atendimentos no bloco de 1 hora; conhecido quando a hora termina; a previsão é feita na sexta-feira para a semana seguinte. P2: não tem alvo. |
| Abordagem e justificativa | P1: **regressão**, porque o alvo é uma contagem. P2: **agrupamento**, porque ninguém definiu os perfis antes. Minha aposta é que, para a escala, uma tabela simples dia × hora já resolve quase tudo; o modelo só vale a pena se errar claramente menos que essa tabela. |
| Alternativa sem ML | Um mapa de calor com a média de atendimentos por dia e hora, separado por período do semestre, e um formulário curto perguntando aos estudantes quais serviços conhecem. |
| Como avaliar a proposta | P1: MAE em atendimentos por hora, testando nas semanas mais recentes (divisão no tempo), comparado à média histórica do mesmo dia e hora. Depois de aplicar: tempo médio de espera antes e depois. P2: a equipe avalia se os grupos fazem sentido e se a divulgação aumentou o uso. |
| Privacidade e limitações | Trabalhar só com contagens por hora e visitas sem identificação; não cruzar com notas ou dados acadêmicos; apagar dados detalhados depois de agregá-los. Limitações: quem desistiu da fila não aparece em registro nenhum; semanas atípicas (greve, reforma) distorcem a média; e quem quase não usa a biblioteca quase não aparece nos dados. |

## Registro de colaboração

| Integrante | Papel | Contribuição |
| --- | --- | --- |
| Henrique Ribeiro Leonardo | Todos os papéis | Delimitação do problema, perguntas, dados, abordagem, avaliação e cuidados com privacidade. |

## Conclusão da equipe

**Proposta:** Separar os dois problemas. Para a fila, começar pelo mapa de calor dia × hora e ajustar a escala; testar regressão só se ela bater a média histórica no MAE. Para os serviços ociosos, primeiro perguntar aos estudantes se conhecem o serviço; agrupar padrões de visita só se a pesquisa não explicar a baixa procura.

**Dúvida ainda aberta:** Como estimar a demanda de quem chegou, viu a fila e foi embora? Uma ideia é comparar as entradas na catraca com os atendimentos no mesmo horário.

**Feedback recebido e melhoria realizada:** A registrar depois da apresentação.

## Entrega

Canvas preenchido e síntese para apresentação de dois minutos. Avaliar coerência da pergunta, dados, abordagem, responsabilidade e colaboração. [Voltar ao início](README.md).
