# 1. Identificação básica
## 1.1 Fatores que Influenciam a Rejeição de Pull Requests em OSS

## 1.2 ID / código
808904

## 1.3 Versão do documento e histórico de revisão
v1.0

## 1.4 Datas (criação, última atualização)
21/11/2025

## 1.5 Autores
- Thiago Andrade Ramalho
- Danilo de Quadros Maia Filho

## 1.6 Responsável principal
Thiago Andrade Ramalho

## 1.7 Projeto / produto / iniciativa relacionada
Este estudo está inserido no contexto de projetos Open Source hospedados no GitHub, que utilizam Pull Requests como forma de contribuição nos projetos. Forma que é comumente utilizada nas empresas que elaboram sistemas e precisam de um aprimoramento da qualidade das contribuições, a otimização do processo de revisão e a promoção de uma participação mais inclusiva de novos desenvolvedores.

# 2. Contexto e problema
## 2.1 Descrição do problema / oportunidade
A rejeição de Pull Requests é uma etapa comum, porém não é muito compreendida, do processo de desenvolvimento em projetos Open Source. Embora parte natural da manutenção da qualidade, rejeições frequentes ou não fundamentadas podem gerar impactos negativos, como frustração de contribuidores, retrabalho e até abandono do projeto por novos participantes.

Diversas pesquisam focam em entender os motivos de aceitação de Pull Requests, porém os motivos que levam à rejeição, recebem uma parte pequena da atenção dos pesquisadores. Com isso, existe uma falta de entendimento por parte de desenvolvedores relacionado ao por que contribuições são recusadas, quais padrões técnicos e sociais estão associados a esses casos e como essas rejeições poderiam ser mitigadas ou melhor justificadas. Assim a pesquisa busca dentificar fatores, padrões e motivos recorrentes de rejeição, contribuindo para práticas mais transparentes, eficientes e inclusivas na colaboração OSS.

## 2.2 Contexto organizacional e técnico
O experimento ocorrerá a partir da análise de projetos públicos disponíveis no GitHub. Nesse ambiente, a colaboração ocorre de forma aberta e descentralizada, envolvendo mantenedores experientes, contribuidores frequentes e novos participantes.

Do ponto de vista técnico, o estudo será estruturado com base em:

- Coleta de dados por meio da API do GitHub.

- Extração de métricas como número de arquivos modificados, número de commits, conflitos detectados, presença de testes, entre outras.

- Análise estatística com ferramentas como Python, pandas, numpy e matplotlib.

- Aplicação de técnicas de processamento de linguagem natural (NLP) para identificar padrões textuais nos comentários de rejeição.

## 2.3 Trabalhos e evidências prévias (internos e externos)
A literatura recente em Engenharia de Software Empírica tem ampliado o entendimento sobre o comportamento de Pull Requests em projetos Open Source, mas grande parte desses trabalhos ainda foca principalmente nos fatores que favorecem a aceitação das contribuições. Com isso, existe uma lacuna importante na investigação dos elementos que levam um PR a ser rejeitado, o que torna este estudo especialmente relevante.

Entre os trabalhos mais atuais que se aproximam desse tema está o de Li et al. (2022), “Opportunities and Challenges in Repeated Revisions to Pull-Requests: An Empirical Study”. Embora o objetivo principal dos autores seja analisar PRs que passam por várias rodadas de revisão, eles mostram que PRs sujeitos a muitas iterações acabam tendo maior chance de não serem aceitos. As razões mais comuns incluem desalinhamento com o escopo do projeto, dificuldade do autor em atender às solicitações dos revisores, falhas de comunicação e perda de consistência ao longo das revisões.

Além das evidências da literatura, a prática cotidiana em projetos também mostra padrões importantes. Pela experiência do próprio autor deste estudo, PRs que modificam um número muito grande de arquivos, fazem alterações extensas ou não incluem testes automatizados costumam ter maior probabilidade de rejeição. Na prática, esses PRs demandam mais tempo para revisar, aumentam o risco de introduzir regressões e dificultam a compreensão da intenção da mudança. 

## 2.4 Referencial teórico e empírico essencial
1. Engenharia de Software Empírica
Oferece métodos sistemáticos para coleta, análise e interpretação de dados reais sobre o desenvolvimento de software.

2. Colaboração em Projetos Open Source
Modelos de governança, dinâmicas de participação voluntária, papéis dos mantenedores e práticas de revisão de código são elementos essenciais para compreender decisões de aceitação e rejeição de PRs.

3. Determinantes técnicos de Pull Requests
Fatores como granularidade da alteração, complexidade da modificação, uso de testes, número de arquivos e presença de conflitos são amplamente estudados como indicadores de qualidade e esforço de revisão.

4. Comunicação técnica e fatores sociais
Clareza da descrição e justificativas fornecidas constituem elementos comunicacionais que influenciam o processo de decisão durante revisões.

# 3. Objetivos e questões (Goal / Question / Metric)
## 3.1 Objetivo geral (Goal template)
O objetivo é analisar quais fatores técnicos, sociais e de comunicação influenciam a rejeição de Pull Requests em projetos Open Source, com o propósito de entender padrões e causas, melhorar a qualidade das contribuições e ajudar colaboradores no processo de revisão.

## 3.2 Objetivos específicos
Decomponha o objetivo geral em metas mais focadas (O1, O2, etc.), que descrevam resultados concretos de aprendizado ou decisão que o experimento deve gerar.

- O1: Identificar e organizar quais PRs foram rejeitados nos projetos analisados
- O2: Avaliar se caracteristicas técnicas, como tamanho, número de arquivos modificados, presença de testes, influenciam a rejeição.
- O3: Analisar se as experiencias do autor correspondem com a realidade dos motivos gerais das rejeições.
- O4: Identificar os comentários mais citados pelos revisores de PRs.
- O5: Comparar diferentes reportitorios com o intuito e identificar se ha um padrão nas rejeições ou são variados.

## 3.3 Questões de pesquisa / de negócio
Formule perguntas claras que o experimento deverá responder (Q1, Q2, etc.), em linguagem que faça sentido para os stakeholders técnicos e de negócio.

Q1: Quais são os motivos mais recorrentes nos comentários de PRs rejeitados?
Q2: PRs maiores ou que alteram muitos arquivos são rejeitados com mais frequência?
Q3: Existem diferenças relevantes nos padrões de rejeição entre os projetos analisados?

## 3.4 Métricas associadas (GQM)
Associe a cada questão as métricas que serão usadas para respondê-la, com nome, definição, unidade e fonte dos dados, garantindo alinhamento entre G, Q e M.

### Q1 — Quais são os motivos mais recorrentes nos comentários de PRs rejeitados?
- M1 - Classificação do motivo de rejeição(muitos arqivos, falta de testes, padrão incorreto) / 
   Unidade: categoria textual.
   Fonte: comentários via API + NLP.

- M2 - Frequência do motivo / 
  Unidade: contagem / %.
  Fonte: comentários dos PRs.

- M3 - Quantidade total de comentários por PR / 
Unidade: número de comentários.
Fonte: API.

- M4 - Presença de feedback negativo explícito /
Unidade: número de comentários.
Fonte: API.

- M5 - Tempo até o primeiro comentário de crítica / 
Unidade: horas/dias.
Fonte: timestamps da API.

### Q2 - PRs maiores ou que alteram muitos arquivos são rejeitados com mais frequência?

- M1 - Linhas adicionadas/removidas (LOC) / 
Unidade: linhas.
Fonte: diff.

- M2 — Número de arquivos modificados
Unidade: contagem.
Fonte: API.

- M3 — Número de commits no PR
Unidade: contagem.
Fonte: API.

- M4 — Presença ou ausência de arquivos de teste
Unidade: booleano + contagem.
Fonte: diff.

- M5 — Complexidade total do PR (LOC + num arquivos + num commits)
Unidade: índice numérico.
Fonte: cálculo a partir das outras métricas.

### Q3 - Existem diferenças relevantes nos padrões de rejeição entre os projetos analisados?

- M1 - Taxa de rejeição por projeto
Proporção de PRs rejeitados em cada repositório.
Unidade: %.
Fonte: API.

- M2 — Tamanho médio dos PRs rejeitados por projeto
Média de LOC entre PRs rejeitados, comparando repositórios.
Unidade: linhas.
Fonte: diff + API.

- M3 — Distribuição dos motivos de rejeição por projeto
Quais motivos aparecem mais em cada projeto.
Unidade: % por categoria.
Fonte: comentários + NLP.

- M4 — Tempo médio até rejeição (time-to-close)
Quanto tempo o PR leva para ser fechado sem merge.
Unidade: horas/dias.
Fonte: timestamps.

- M5 — Experiência média do autor dos PRs rejeitados por projeto
Quantidade de contribuições prévias dos autores rejeitados, comparando repositórios.
Unidade: contagem de PRs anteriores.
Fonte: API (histórico do autor).

# 4. Escopo e contexto do experimento
## 4.1 Escopo funcional / de processo (incluído e excluído)
Explique claramente o que será coberto (atividades, artefatos, equipes, módulos) e o que ficará fora do experimento, para evitar interpretações divergentes.

Coberto:
- Análise de Pull Requests rejeitados em projetos Open Source hospedados no GitHub.
- Coleta de dados estruturais (LOC, arquivos modificados, commits, presença de testes).
- Coleta de dados sociais/comunicacionais (comentários, experiência do autor, motivos de rejeição).
- Processamento de linguagem natural (NLP) para identificar padrões textuais em comentários.
- Comparação entre diferentes repositórios para observar padrões distintos de rejeição.
- Identificação de fatores que aumentam a probabilidade de um PR ser rejeitado.

Fora:
- Analise do código fonte dos PRs
- Recomendações de correções para os PRs rejeitados
- Análise de PRs privados ou internos de empresas

## 4.2 Contexto do estudo (tipo de organização, projeto, experiência)
Caracterize o contexto em que o estudo ocorrerá: tipo e tamanho de organização, tipo de projeto, criticidade e perfil de experiência dos participantes.

O estudo será realizado no contexto de comunidades de software Open Source distribuídas, compostas por mantenedores experientes, colaboradores eventuais e novos contribuidores. Esses projetos funcionam com regras próprias de governança, revisão de código e políticas de contribuição, normalmente documentadas em arquivos como CONTRIBUTING.md e CODE_OF_CONDUCT.md. (não sei o que coloco aqui: tamanho de organização, o chat me deu isso)

A pesquisa irá utilizar projetos de grande porte e muito utilizado por qualquer tipo de sistema ou usuario do ramo de programação, além de serem repositorios com alto volume de PRs e de colaborações ativas. Nesses projetos, os participantes, autores dos PRs, possuem diferentes níveis de experiência, desde pequenas contribuições feitas por iniciantes até contribuições contínuas de desenvolvedores mais experientes. (Preciso explicar o que é PR nesse contexto?)

## 4.3 Premissas
Liste as suposições consideradas verdadeiras para o plano funcionar (por exemplo, disponibilidade de ambiente, estabilidade do sistema), mesmo que não possam ser garantidas.

- A API do GitHub permanecerá estável e acessível durante todo o período de coleta.
- Os repositórios selecionados manterão seus dados públicos e disponíveis.
- Os comentários registrados nos PRs refletem de forma honesta e direta os motivos de rejeição.
- A classificação textual feita com NLP conseguirá identificar padrões significativos.
- A amostra de projetos escolhidos representará adequadamente práticas comuns em OSS.
- As métricas coletadas (LOC, arquivos modificados, histórico do autor etc.) são suficientes para identificar fatores relevantes de rejeição.

## 4.4 Restrições
Registre limitações práticas como tempo, orçamento, ferramentas, acessos ou regras organizacionais que impõem limites ao desenho.

- Tempo limitado para coleta, processamento e análise dos dados.
- Limites de rate limit da GitHub API, podendo exigir coleta por etapas.
- Falta de padronização das mensagens de rejeição entre diferentes projetos.
- Restrições computacionais do ambiente local (ex.: processamento de NLP mais pesado).
- Possíveis inconsistências nos dados, como PRs abandonados sem justificativa formal.

## 4.5 Limitações previstas
Explique fatores que podem prejudicar a generalização dos resultados (validez externa), como contexto muito específico ou amostra pouco representativa.

- Contexto específico de projetos analisados: padrões de rejeição podem diferir em outros tipos de projetos ou comunidades.
- Diversidade de governança entre repositórios: cada projeto possui regras próprias, o que pode limitar comparações diretas.
- Amostra não totalmente representativa do universo do GitHub, por ser  extremamente grande e heterogêneo.
- Motivos textuais incompletos: muitos PRs são rejeitados sem explicação formal, o que afeta a análise de motivos.
- Impossibilidade de capturar fatores subjetivos, como percepção do revisor ou decisões baseadas em preferências pessoais.
- Limitação da análise automática: técnicas de NLP podem não captar nuances mais sutis presentes nos comentários.

# 5. Stakeholders e impacto esperado
## 5.1 Stakeholders principais
Liste os grupos ou papéis que têm interesse ou serão impactados pelo experimento (por exemplo, devs, QA, produto, gestores, clientes internos).

- Mantenedores dos projetos Open Source
- Contribuidores frequentes
- Contribuidores iniciantes
- Comunidade do projeto como um todo (usuários, testers, revisores eventuais e participantes das discussões)
- Pesquisadores e profissionais de Engenharia de Software

## 5.2 Interesses e expectativas dos stakeholders
Descreva o que cada grupo espera obter do experimento (insights, evidências, validação de decisão, mitigação de risco, etc.).

- Mantenedores:
Esperam compreender melhor os fatores que tornam a revisão mais difícil e os motivos que levam à rejeição de PRs. Buscam evidências que ajudem a tornar o processo mais ágil, claro e consistente.

- Contribuidores frequentes:
Têm interesse em saber quais práticas aumentam ou reduzem a chance de rejeição, buscando melhorar a qualidade de suas contribuições e diminuir retrabalho.

- Contribuidores iniciantes: 
Esperam orientações claras sobre como evitar erros comuns, diminuir frustração com rejeições e entender melhor as expectativas da comunidade.

- Comunidade do projeto:
Espera benefícios indiretos, como maior estabilidade do código, PRs mais bem estruturados e processos de revisão mais fluídos.

- Pesquisadores e profissionais da área:
Buscam evidências empíricas que possam alimentar estudos sobre colaboração distribuída, qualidade de código e boas práticas em processos baseados em Pull Requests.

## 5.3 Impactos potenciais no processo / produto
Impactos potenciais positivos:
- Maior clareza sobre fatores que tornam PRs mais propensos à rejeição.
- Melhorias futuras no fluxo de contribuição, reduzindo retrabalho e aumentando qualidade.
- Contribuidores mais b-em preparados para enviar PRs alinhados às expectativas dos mantenedores.
- Possibilidade de criação de guidelines mais objetivas e úteis para novos colaboradores.

Impactos potenciais negativos ou neutros:

- A análise pode exigir tempo para coleta e processamento dos dados, sem afetar diretamente o produto, mas consumindo esforço do pesquisador.
- Como se trata de um estudo observacional, não há impacto direto no código ou nos prazos dos projetos analisados.
- Diferenças entre projetos podem limitar a generalização dos resultados, exigindo cuidado na interpretação.

# 6. Riscos de alto nível, premissas e critérios de sucesso
## 6.1 Riscos de alto nível (negócio, técnicos, etc.)
Identifique os principais riscos para negócio e tecnologia (atrasos, falhas de ambiente, indisponibilidade de dados, etc.) em nível macro.

- Indisponibilidade ou instabilidade da API do GitHub
- Limites de requisições (rate limit)
- Dados incompletos ou não padronizados
- Mudanças inesperadas nos repositórios analisados
- Complexidade na análise textual
- Volume de dados maior que o esperado
- Dependência de interpretação automática (NLP)

## 6.2 Critérios de sucesso globais (go / no-go)
Defina as condições sob as quais o experimento será considerado útil e viável, inclusive critérios que sustentem uma decisão de seguir ou não com mudanças.
 
GO:

- Coleta completa de dados dos PRs necessários nos repositórios selecionados, sem perda significativa por falhas da API.

- Classificação válida dos motivos de rejeição, obtida por meio da análise dos comentários e confirmação de que as categorias fazem sentido para o contexto.

- Identificação clara de padrões técnicos, como relação entre tamanho do PR, número de arquivos e probabilidade de rejeição.

- Diferenças entre projetos percebidas e documentadas, permitindo comparações objetivas.

- Produção de insights úteis que possam orientar contribuidores e mantenedores sobre como melhorar a qualidade das contribuições e reduzir rejeições desnecessárias.

NO-GO:

- Não houver dados suficientes para análise.
- Os comentários dos PRs forem escassos ou pouco informativos.
- A API impedir a coleta consistente dos PRs.
- O processamento ou classificação via NLP for inconclusivo.

## 6.3 Critérios de parada antecipada (pré-execução)
Descreva situações em que o experimento deve ser adiado ou cancelado antes de começar (falta de recursos críticos, reprovação ética, mudanças de contexto).

- Indisponibilidade total da API do GitHub por período prolongado.
- Impossibilidade de acessar os repositórios selecionados, seja por privacidade, exclusão ou arquivamento.
- Falta de recursos técnicos essenciais, como máquina para executar os scripts, ambiente de Python configurado ou acesso à internet estável.
- Volume insuficiente de PRs rejeitados, impossibilitando análise estatística.
- Mudança significativa no escopo do projeto, como retirada de repositórios importantes ou alteração do tema de pesquisa.
- Problemas éticos ou de política dos repositórios, caso algum projeto não permita mineração de dados conforme licenças ou guidelines.

# 7. Modelo conceitual e hipóteses
## 7.1 Modelo conceitual do experimento
Explique, em texto ou esquema, como você acredita que os fatores influenciam as respostas (por exemplo, “técnica A reduz defeitos em relação a B”).

## 7.2 Hipóteses formais (H0, H1)
Formule explicitamente as hipóteses nulas e alternativas para cada questão principal, incluindo a direção esperada do efeito quando fizer sentido.

## 7.3 Nível de significância e considerações de poder
Defina o nível de significância (por exemplo, α = 0,05) e comente o que se espera em termos de poder estatístico, relacionando-o ao tamanho de amostra planejado.

8. Variáveis, fatores, tratamentos e objetos de estudo
8.1 Objetos de estudo
Descreva o que será efetivamente manipulado ou analisado (módulos de código, requisitos, tarefas, casos de teste, issues, etc.).

8.2 Sujeitos / participantes (visão geral)
Caracterize em alto nível quem serão os participantes (desenvolvedores, testadores, estudantes, etc.), sem ainda entrar em detalhes de seleção.

8.3 Variáveis independentes (fatores) e seus níveis
Liste os fatores que serão manipulados (por exemplo, técnica, ferramenta, processo) e indique os níveis de cada um (A/B, X/Y, alto/baixo).

8.4 Tratamentos (condições experimentais)
Descreva claramente cada condição de experimento (grupo controle, tratamento 1, tratamento 2, etc.) e o que distingue uma da outra.

8.5 Variáveis dependentes (respostas)
Informe as medidas de resultado que você observará (por exemplo, número de defeitos, esforço em horas, tempo de conclusão, satisfação).

8.6 Variáveis de controle / bloqueio
Liste fatores que você não está estudando diretamente, mas que serão mantidos constantes ou usados para formar blocos (por exemplo, experiência, tipo de tarefa).

8.7 Possíveis variáveis de confusão conhecidas
Identifique fatores que podem distorcer os resultados (como diferenças de contexto, motivação ou carga de trabalho) e que você pretende monitorar.

9. Desenho experimental
9.1 Tipo de desenho (completamente randomizado, blocos, fatorial, etc.)
Indique qual tipo de desenho será utilizado e justifique brevemente por que ele é adequado ao problema e às restrições.

9.2 Randomização e alocação
Explique o que será randomizado (sujeitos, tarefas, ordem de tratamentos) e como a randomização será feita na prática (ferramentas, procedimentos).

9.3 Balanceamento e contrabalanço
Descreva como você garantirá que os grupos fiquem comparáveis (balanceamento) e como lidará com efeitos de ordem ou aprendizagem (contrabalanço).

9.4 Número de grupos e sessões
Informe quantos grupos existirão e quantas sessões ou rodadas cada sujeito ou grupo irá executar, com uma breve justificativa.

10. População, sujeitos e amostragem
10.1 População-alvo
Descreva qual é a população real que você deseja representar com o experimento (por exemplo, “desenvolvedores Java de times de produto web”).

10.2 Critérios de inclusão de sujeitos
Especifique os requisitos mínimos para um participante ser elegível (experiência, conhecimento, papel, disponibilidade, etc.).

10.3 Critérios de exclusão de sujeitos
Liste condições que impedem participação (conflitos de interesse, falta de skills essenciais, restrições legais ou éticas).

10.4 Tamanho da amostra planejado (por grupo)
Defina quantos participantes você pretende ter no total e em cada grupo, relacionando a decisão com poder, recursos e contexto.

10.5 Método de seleção / recrutamento
Explique como os participantes serão escolhidos (amostra de conveniência, sorteio, convite aberto, turma de disciplina, time específico).

10.6 Treinamento e preparação dos sujeitos
Descreva qual treinamento ou material preparatório será fornecido para nivelar entendimento e reduzir vieses por falta de conhecimento.

11. Instrumentação e protocolo operacional
11.1 Instrumentos de coleta (questionários, logs, planilhas, etc.)
Liste todos os instrumentos que serão usados para coletar dados (arquivos, formulários, scripts, ferramentas), com uma breve descrição do papel de cada um.

11.2 Materiais de suporte (instruções, guias)
Descreva as instruções escritas, guias rápidos, slides ou outros materiais que serão fornecidos a participantes e administradores do experimento.

11.3 Procedimento experimental (protocolo – visão passo a passo)
Escreva, em ordem, o que acontecerá na operação (do convite ao encerramento), de modo que alguém consiga executar o experimento seguindo esse roteiro.

11.4 Plano de piloto (se haverá piloto, escopo e critérios de ajuste)
Indique se um piloto será realizado, com que participantes e objetivos, e defina que tipo de ajuste do protocolo poderá ser feito com base nesse piloto.

12. Plano de análise de dados (pré-execução)
12.1 Estratégia geral de análise (como responderá às questões)
Explique, em alto nível, como os dados coletados serão usados para responder cada questão de pesquisa ou de negócio.

12.2 Métodos estatísticos planejados
Liste os principais testes ou técnicas estatísticas que pretende usar (por exemplo, t-teste, ANOVA, testes não paramétricos, regressão).

12.3 Tratamento de dados faltantes e outliers
Defina previamente as regras para lidar com dados ausentes e valores extremos, evitando decisões oportunistas após ver os resultados.

12.4 Plano de análise para dados qualitativos (se houver)
Descreva como você tratará dados qualitativos (entrevistas, comentários, observações), especificando a técnica de análise (codificação, categorias, etc.).

13. Avaliação de validade (ameaças e mitigação)
13.1 Validade de conclusão
Liste ameaças que podem comprometer a robustez das conclusões estatísticas (baixo poder, violação de suposições, erros de medida) e como pretende mitigá-las.

13.2 Validade interna
Identifique ameaças relacionadas a causas alternativas para os efeitos observados (history, maturation, selection, etc.) e explique suas estratégias de controle.

13.3 Validade de constructo
Refleta se as medidas escolhidas realmente representam os conceitos de interesse e descreva como você reduzirá ambiguidades de interpretação.

13.4 Validade externa
Discuta em que contextos os resultados podem ser generalizados e quais diferenças de cenário podem limitar essa generalização.

13.5 Resumo das principais ameaças e estratégias de mitigação
Faça uma síntese das ameaças mais críticas e das ações planejadas, de preferência em forma de lista ou tabela simples.

14. Ética, privacidade e conformidade
14.1 Questões éticas (uso de sujeitos, incentivos, etc.)
Descreva potenciais questões éticas (pressão para participar, uso de estudantes, incentivos, riscos de exposição) e como serão tratadas.

14.2 Consentimento informado
Explique como os participantes serão informados sobre objetivos, riscos, benefícios e como registrarão seu consentimento.

14.3 Privacidade e proteção de dados
Indique que dados pessoais serão coletados, como serão protegidos (anonimização, pseudoanonimização, controle de acesso) e por quanto tempo serão mantidos.

14.4 Aprovações necessárias (comitê de ética, jurídico, DPO, etc.)
Liste órgãos ou pessoas que precisam aprovar o experimento (comitê de ética, jurídico, DPO, gestores) e o status atual dessas aprovações.

15. Recursos, infraestrutura e orçamento
15.1 Recursos humanos e papéis
Identifique os membros da equipe do experimento e descreva brevemente o papel e responsabilidade de cada um.

15.2 Infraestrutura técnica necessária
Liste ambientes, servidores, ferramentas, repositórios e integrações que devem estar disponíveis para executar o experimento.

15.3 Materiais e insumos
Relacione materiais físicos ou digitais necessários (máquinas, licenças, formulários, dispositivos) que precisam estar prontos antes da operação.

15.4 Orçamento e custos estimados
Faça uma estimativa dos principais custos envolvidos (horas de pessoas, serviços, licenças, infraestrutura) e a fonte de financiamento.

16. Cronograma, marcos e riscos operacionais
16.1 Macrocronograma (até o início da execução)
Defina as principais datas e marcos (conclusão do plano, piloto, revisão, início da operação) com uma visão de tempo realista.

16.2 Dependências entre atividades
Indique quais atividades dependem de outras para começar (por exemplo, treinamento após aprovação ética), deixando essas dependências claras.

16.3 Riscos operacionais e plano de contingência
Liste riscos ligados a cronograma, disponibilidade de pessoas ou recursos, e descreva ações de contingência caso esses riscos se materializem.

17. Governança do experimento
17.1 Papéis e responsabilidades formais
Defina quem decide, quem executa, quem revisa e quem apenas deve ser informado, deixando claro o fluxo de responsabilidade.

17.2 Ritos de acompanhamento pré-execução
Descreva as reuniões, checkpoints e revisões previstos antes da execução, incluindo frequência e participantes.

17.3 Processo de controle de mudanças no plano
Explique como mudanças no desenho ou no escopo do experimento serão propostas, analisadas, aprovadas e registradas.

18. Plano de documentação e reprodutibilidade
18.1 Repositórios e convenções de nomeação
Indique onde o plano, instrumentos, scripts e dados (futuros) serão armazenados e quais convenções de nomes serão usadas.

18.2 Templates e artefatos padrão
Liste os modelos (questionários, formulários, checklists, scripts) que serão usados e onde podem ser encontrados.

18.3 Plano de empacotamento para replicação futura
Descreva o que será organizado desde já (documentos, scripts, instruções) para facilitar a replicação do experimento por outras equipes ou no futuro.

19. Plano de comunicação
19.1 Públicos e mensagens-chave pré-execução
Liste os grupos que precisam ser comunicados e quais mensagens principais devem receber (objetivos, escopo, datas, impactos esperados).

19.2 Canais e frequência de comunicação
Defina por quais canais (e-mail, reuniões, Slack/Teams, etc.) e com que frequência as comunicações serão feitas.

19.3 Pontos de comunicação obrigatórios
Especifique os eventos que exigem comunicação formal (aprovação do plano, mudanças relevantes, adiamentos, cancelamentos).

20. Critérios de prontidão para execução (Definition of Ready)
20.1 Checklist de prontidão (itens que devem estar completos)
Liste os itens que precisam estar finalizados e aprovados (plano, instrumentos, aprovação ética, recursos, comunicação) para autorizar o início da operação.

20.2 Aprovações finais para iniciar a operação