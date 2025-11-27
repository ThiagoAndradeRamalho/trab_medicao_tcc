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
O objetivo é analisar quais fatores técnicos, sociais e de comunicação influenciam a rejeição de Pull Requests em projetos Open Source, com o propósito de entender padrões e causas, melhorar a qualidade das contribuições.

| Objetivo | Questões | Métricas |
|------------------|-------------------|------------------------------|
| O1 - Identificar os motivos textuais mais frequentes nas rejeições de PRs. | Q1.1 - Quais são os motivos mais citados quando se rejeita os PRs? | M1, M2 |
| | Q1.2 - Qual é a frequência de cada motivo de rejeição? | M2, M3 |
| | Q1.3 - O tempo para ser feito o primeiro comentário possui influencia na rejeição? | M4, M5 |
| O2 - Avaliar o impacto do tamanho e complexidade do PR na rejeição. | Q2.1 - PRs maiores (em LOC) são rejeitados com mais frequência? | M6, M10 |
| | Q2.2 - PRs que alteram muitos arquivos têm maior risco de rejeição? | M7, M10 |
| | Q2.3 - O número de commits afeta a rejeição? | M8, M10 |
| O3 - Analisar o impacto dos fatores sociais na rejeição dos PRs. | Q3.1 - A experiência do autor reduz a probabilidade de rejeição? | M11, M12 |
| | Q3.2 - PRs de autores iniciantes recebem mais feedback negativo? | M1, M13 |
| | Q3.3 - Autores experientes esperam menos tempo até revisão? | M5, M12 |
| O4 - Quais os padrões de rejeição entre diferentes projetos. | Q4.1 - A taxa de rejeição varia entre projetos? | M14, M15 |
| | Q4.2 - Cada projeto possui diferentes tipos de rejeição? | M1, M16 |
| | Q4.3 - Projetos maiores são mais rápidos para rejeitar PR? | M5, M15 |


## 3.2 Métricas associadas (GQM)

| Métrica | Descrição da Métrica                                | Unidade             |
|---------|-----------------------------------------------------|--------------------------------|
| M1 - Categoria do motivo           | Tipo de motivo de rejeição do PR.                     | Categoria (texto)              |
| M2 - Frequência do motivo          | Quantidade de vezes que cada motivo aparece.          | Contagem (n)                   |
| M3 - Número total de comentários   | Total de comentários em um PR.                        | Contagem (n)                   |
| M4 - Presença de feedback negativo | Indica se há comentário com crítica/rejeição direta.  | Binária (0 = não, 1 = sim)     |
| M5 - Tempo até o primeiro comentário crítico | Tempo até o primeiro comentário crítico no PR. | Tempo (horas ou dias)          |
| M6 - LOC (linhas adicionadas/removidas) | Linhas de código alteradas no PR.                | Linhas de código (LOC)         |
| M7 - Arquivos modificados          | Número de arquivos alterados no PR.                   | Contagem de arquivos (n)       |
| M8 - Número de commits             | Total de commits incluídos no PR.                     | Contagem de commits (n)        |
| M9 - Presença de arquivos de teste | Indica se há arquivos de teste alterados ou criados.  | Binária (0 = não, 1 = sim)     |
| M10 - Índice de complexidade do PR | Medida combinando tamanho e dispersão do PR.          | Número            |
| M11 - Experiência do autor         | PRs anteriores aceitos do mesmo autor no projeto.     | Contagem de PRs (n)            |
| M12 - Histórico total do autor     | Total de PRs enviados pelo autor (aceitos + rejeitados). | Contagem de PRs (n)         |
| M13 - Sentimento do comentário     | Polaridade média dos comentários do PR.               | Escala numérica (-1 a 1)       |
| M14 - Taxa de rejeição por projeto | Proporção de PRs rejeitados em um projeto.            | Percentual (%)                 |
| M15 - Tamanho médio dos PRs rejeitados | Média de LOC dos PRs rejeitados em um projeto.    | Linhas de código (LOC)         |
| M16 - Distribuição dos motivos por projeto | Participação de cada motivo nas rejeições de um projeto. | Percentual por categoria (%) |

# 4. Escopo e contexto do experimento
## 4.1 Escopo funcional / de processo (incluído e excluído)

Coberto:
- Analise de Pull Requests rejeitados em projetos Open Source hospedados no GitHub.
- Coleta de dados como LOC, quais os tipos de arquivos modificados, commits, se há presença de testes.
- Coleta de dados referente a comunicação/perfil dos contribuidores como os comentários do PR, grau de experiência/relevancia do autor nos PRs, motivos de rejeição.
- Processamento de linguagem natural (NLP) para conseguir identificar os padrões textuais nos comentários dos PRs.
- Comparação entre diferentes repositórios para identificar padrões diferentes de rejeição.
- Identificação de fatores que aumentam a probabilidade de um PR ser rejeitado.

Fora:
- Analise do código fonte dos PRs
- Recomendações de correções para os PRs que foram rejeitados
- Analise de PRs privados ou internos de empresas

## 4.2 Contexto do estudo (tipo de organização, projeto, experiência)

Analisar Pull Requests rejeitados em projetos de software open source hospedados no GitHub, com o propósito de identificar e compreender os fatores técnicos, sociais e comunicacionais que influenciam a rejeição de contribuições, com respeito a qualidade do processo de revisão e da decisão sobre PRs, do ponto de vista de pesquisadores em Engenharia de Software e de mantenedores de projetos OSS, no contexto de repositórios GitHub de médio e grande porte.

## 4.3 Premissas

- A API do GitHub permanecerá estável e acessível durante todo o período de coleta.
- Os repositórios escolhidos antes da analise continuarao com seus dados públicos e disponíveis.
- Os comentários doss PRs vao conter os motivos das rejeições dos PRs.
- A classificação textual feita com NLP vai conseguir identificar padrões.
- As metricas selecionadas condiz com a realidade e irão ajudar na analise dos dados.

## 4.4 Restrições

- Tempo limitado para coleta, processamento e análise dos dados.
- Limites de rate limit da API do GitHub pode dividir a coleta por etapas.
- Falta de padronização das mensagens de rejeição entre diferentes projetos.
- Comentários com textos que não correspondem ao contexto do PR.
- Exigir mais do processamento de NLP dessa forma atrasando mais.
- PRs rejeitados sem justificativa.

## 4.5 Limitações previstas

- Padrões de rejeição totalmente diferentes um dos outros.
- Amostra não totalmente representativa do universo do GitHub, por ser  extremamente grande e heterogêneo.
- Motivos textuais incompletos
- Não ser possível identificar/analisar/capturar comentarios em que possui preferencias pessoais.
- Limitação da análise automática

# 5. Stakeholders e impacto esperado
## 5.1 Stakeholders principais

- Mantenedores dos projetos Open Source
- Contribuidores frequentes
- Contribuidores iniciantes
- Contribuidores do projeto como um todo (usuários, testers, revisores e participantes dos comentarios dos PRs)

## 5.2 Interesses e expectativas dos stakeholders

- Mantenedores:
Entender melhor quais características dos Pull Requests estão associadas à rejeição e quais os motivos mais comuns nos comentários. Buscam ver o que fazer para reduzir rejeições evitáveis, orientar contribuidores sobre boas práticas e tornar o processo de revisão mais eficiente e previsível.

- Contribuidores frequentes:
Tem interesse em saber em o que fazer para conseguir  aumentar ou reduzir a chance de rejeição, buscando melhorar a qualidade de suas contribuições e diminuir retrabalho.

- Contribuidores iniciantes: 
Esperam orientações claras sobre como evitar erros comuns, diminuir rejeições e entender melhor como contribuir em um projeto.

- Comunidade do projeto:
Espera benefícios indiretos, como maior estabilidade do código, PRs mais bem estruturados e processos de revisão mais fluídos.


## 5.3 Impactos potenciais no processo / produto
Impactos potenciais positivos:
- Maior clareza sobre motivos que tornam PRs com mais chance de rejeição.
- Melhorias futuras nas contribuições, reduzindo retrabalho e aumentando qualidade.
- Contribuidores mais preparados para contribuir

Impactos potenciais negativos ou neutros:

- A análise pode exigir tempo para coleta e processamento dos dados, sem afetar diretamente o produto, mas consumindo esforço do pesquisador.
- Como se trata de um estudo observacional, não há impacto direto no código ou nos prazos dos projetos analisados.
- Diferenças entre projetos podem limitar a generalização dos resultados, exigindo cuidado na interpretação.

# 6. Riscos de alto nível, premissas e critérios de sucesso
## 6.1 Riscos de alto nível (negócio, técnicos, etc.)

- Indisponibilidade ou instabilidade da API do GitHub
- Limites de requisições (rate limit)
- Dados incompletos ou não padronizados
- Mudanças inesperadas nos repositórios analisados
- Complexidade na análise textual
- Volume de dados maior que o esperado
- Dependência de interpretação automática (NLP)

## 6.2 Critérios de sucesso globais (go / no-go)
 
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

- Indisponibilidade total da API do GitHub por um grande periodo
- Acesso negado em repositórios selecionados, seja por privacidade, exclusão ou arquivamento.
- Volume insuficiente de PRs rejeitados, impossibilitando análise estatística.
- Retirada de repositórios importantes ou alteração do tema de pesquisa.
- Problemas relacionados a lei ao coletar dados de repositorios.

# 7. Modelo conceitual e hipóteses
## 7.1 Modelo conceitual do experimento
A rejeição de Pull Requests é influenciada por um conjunto de fatores técnicos, sociais e comunicacionais. Sendo assim:

### Fatores técnicos:
PRs maiores, seja código, arquivo, commits, requer mais esforço para revisar, tendo assim uma atenção maior por estar alterando ou adicionando mais coisas ao projeto.

PRs sem testes ou com alterações em arquivos críticos(arquivos comumente conhecidos como arquivos críticos), requer cuidado em áreas sensíveis sem validação, dessa forma tendo um cuidado maior e analizando mais calmamente tendo uma chance maior de rejeição.

### Fatores sociais/experiência

Devs com muitos PRs aceitos, terá maior confiaça e com isso menor chance de rejeição.

Devs iniciantes, ou sem histórico ou com muitos PRs recusados, há uma desconfiaça na qualidade ou ao padrão do repositorio tendo uma chance maior de rejeição.

### Fatores comunicacionais

Devs realizando descrições mais claras e bem estruturadas e que correspondem a issue, facilita a compreensão do que foi realmente feito diminuindo os riscos de rejeição.

Motivos sendo repetidos nos comentários da revisão, seja por falta de teste, alteração muito grande, não respeitou a arquitetura, facilita a identificar padões de rejeição.


## 7.2 Hipóteses formais (H0, H1)
Formule explicitamente as hipóteses nulas e alternativas para cada questão principal, incluindo a direção esperada do efeito quando fizer sentido.

  Q1 - 
- H0 - Não existem motivos padronizados nos comentários de PRs rejeitados,  os motivos são específicos para cada PR.
- H1 - Existem motivos predominantes nos comentários, como falta de testes, mudança grande demais, fora de escopo, aparecendo frequentemente nos comentários de PRs rejeitados.
  
Q2 
- H0 - Não há diferença na taxa de rejeição entre PRs pequenos e PRs maiores, LOC, número de arquivos modificados ou número de commits.
- H1 - PRs maiores apresentam uma taxa de rejeição significativamente maior do que PRs menores.

Q3 - 
- H0 - A experiência do autor, medida por histórico de PRs anteriores no projeto não significa em uma probabilidade maior de rejeição de novos PRs.
- H1 - Autores com mais experiência, ou seja, mais PRs aceitos, têm uma probabilidade menor de terem seus PRs rejeitados, quando comparados a autores com pouca ou nenhuma experiência.

Q4 - 
- H0 - Não existe diferenças nas taxas de rejeição e nos motivos de rejeição dos projetos, todos os repositórios possuem os mesmos padrões.
- H1 - Existem diferenças nas taxas de rejeição ou motivos comuns de rejeição entre os projetos.

## 7.3 Nível de significância e considerações de poder
Defina o nível de significância (por exemplo, α = 0,05) e comente o que se espera em termos de poder estatístico, relacionando-o ao tamanho de amostra planejado.

A pesquisa possui nível de significância α = 0,05, tendo assim um risco de 5% de rejeitar a hipótese nula quando verdadeira. Para a análise será utilizado uma amostra de milhares de PRs, para conseguir dessa forma ter um porder estatístico capaz de concluir os objetivos da pesquisa e identificar as diferenças entre os dados analisados, como PRs menores ou maiores, autores iniciantes ou experientes, etc.

# 8. Variáveis, fatores, tratamentos e objetos de estudo
## 8.1 Objetos de estudo
Descreva o que será efetivamente manipulado ou analisado (módulos de código, requisitos, tarefas, casos de teste, issues, etc.).

Os objetos de estudo deste experimento são focados nos PRs rejeitados, fechados sem merge, de projetos Open Source hospedados no GitHub. Além  dos comentários associados aos PRs, focando aos que possuem justificativas ou feedback dos revisores.

Metadados dos PRs, como número de arquivos modificados, quantidade de linhas alteradas (LOC), número de commits, presença de arquivos de teste, datas de abertura e fechamento, e histórico do desenvolvedor.

## 8.2 Sujeitos / participantes (visão geral)
Caracterize em alto nível quem serão os participantes (desenvolvedores, testadores, estudantes, etc.), sem ainda entrar em detalhes de seleção.

Os participantes da pesquisa são desenvolvedores(com diferentes níveis de experiência) que enviaram contribuições(PRs), aos projetos OSS. Além de revisores/ mantenedores, que são os desenvolvedores responsáveis por avaliar, comentar, aceitar ou rejeitar PRs.

## 8.3 Variáveis independentes (fatores) e seus níveis
Liste os fatores que serão manipulados (por exemplo, técnica, ferramenta, processo) e indique os níveis de cada um (A/B, X/Y, alto/baixo).

| **Tipo**              | **Variável**          | **Descrição**                                                            | **Níveis**                                      |
|-----------------------|-----------------------|-------------------------------------------------------------------------|-----------------------------------------------------------|
| Fator técnico         | Tamanho do PR (LOC)   | Quantidade de linhas adicionadas/removidas no Pull Request.            | Baixo / Médio / Alto (faixas definidas na análise)        |
| Fator técnico         | Arquivos modificados  | Número total de arquivos alterados pelo PR.                             | Poucos arquivos / Muitos arquivos                         |
| Fator técnico         | Número de commits     | Total de commits incluídos no PR.                                       | Poucos commits / Muitos commits                           |
| Fator técnico         | Presença de testes    | Indica se o PR criou ou modificou arquivos de teste.                    | Com testes / Sem testes                                   |
| Fator social          | Experiência do autor  | Quantidade de PRs anteriores enviados/aceitos pelo autor no projeto.    | Iniciante / Intermediário / Experiente                    |
| Fator de contexto     | Projeto / Repositório | Identifica de qual projeto o PR faz parte.                              | Projeto A / Projeto B / Projeto C (e outros escolhidos)   |

## 8.4 Tratamentos (condições experimentais)
Descreva claramente cada condição de experimento (grupo controle, tratamento 1, tratamento 2, etc.) e o que distingue uma da outra.

| **Condição**        | **Nome / Papel**        | **Descrição da condição**                                                                                       | **O que distingue essa condição das outras**                                                |
|---------------------|-------------------------|------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------|
| C0                  | Grupo controle          | PRs pequenos (baixa LOC), poucos arquivos modificados, com testes e enviados por autores experientes.           | Representa o cenário considerado “mais favorável”: mudanças menores, com testes e experiência. |
| C1                  | Tratamento 1 – PRs grandes | PRs com alto número de linhas alteradas (alta LOC), independentemente de testes ou experiência.              | Mudanças extensas; avalia impacto direto do tamanho do PR na rejeição.                      |
| C2                  | Tratamento 2 – Muitos arquivos | PRs que modificam muitos arquivos, mesmo que não tenham tantas linhas por arquivo.                           | Foca na dispersão da mudança pelo código, e não só na quantidade de linhas.                 |
| C3                  | Tratamento 3 – Sem testes | PRs que não criam nem modificam arquivos de teste.                                                              | Compara cenários com e sem suporte de testes automatizados.                                 |
| C4                  | Tratamento 4 – Autores iniciantes | PRs enviados por autores com pouca experiência (poucos PRs anteriores no projeto).                           | Analisa impacto da experiência do autor na rejeição, comparado ao grupo controle.           |
| C5                  | Tratamento 5 – Autores experientes | PRs enviados por autores com histórico forte de contribuições aceitas.                                       | Permite comparar iniciantes vs experientes em termos de rejeição e motivos.                 |
| C6                  | Tratamento 6 – Projeto mais rígido | PRs de um projeto com alta taxa de rejeição global e/ou regras de contribuição mais rígidas.                 | Ajuda a entender influência da cultura de revisão do projeto.                               |
| C7                  | Tratamento 7 – Projeto mais flexível | PRs de um projeto com taxa de rejeição menor e aceitação mais frequente.                                     | Serve de contraste com o projeto mais rígido, isolando efeito do contexto de repositório.   |

## 8.5 Variáveis dependentes (respostas)
Informe as medidas de resultado que você observará (por exemplo, número de defeitos, esforço em horas, tempo de conclusão, satisfação).

| **Variáveis Dependentes**        | **Descrição**                                                                                         | **Unidade / Tipo**                 |
|--------------------------------|-------------------------------------------------------------------------------------------------------|------------------------------------|
| Status do PR                   | Indica se o Pull Request foi rejeitado (fechado sem merge) ou aceito (merge realizado).              | Categórica (Aceito / Rejeitado)    |
| Motivos de rejeição            | Categorias textuais que resumem as razões de rejeição presentes nos comentários dos revisores.       | Categórica (labels de motivo)      |
| Frequência de cada motivo      | Quantas vezes cada tipo de motivo de rejeição aparece entre os PRs analisados.                        | Contagem / Porcentagem             |
| Tempo até rejeição             | Intervalo entre a abertura do PR e o fechamento sem merge (quando rejeitado).                        | Contínua (horas / dias)            |
| Quantidade de comentários      | Número total de comentários feitos no PR, incluindo discussões técnicas e pedidos de ajuste.         | Contínua (contagem)                |
| Feedback negativo explícito    | Presença de críticas diretas ou termos que indiquem rejeição ou problemas graves na contribuição.    | Categórica (Presente / Ausente)    |

## 8.6 Variáveis de controle / bloqueio
Liste fatores que você não está estudando diretamente, mas que serão mantidos constantes ou usados para formar blocos (por exemplo, experiência, tipo de tarefa).

| **Variável de controle** | **Descrição**                                                                                      | **Como será usada**                                             |
|--------------------------|----------------------------------------------------------------------------------------------------|------------------------------------------------------------------|
| Janela temporal          | Período de tempo dos PRs analisados, para evitar misturar épocas muito diferentes do projeto.     | Mantida fixa (ex.: PRs entre 2020 e 2025).                      |
| Tipo de projeto          | Natureza do repositório (framework, biblioteca, ferramenta, etc.).                                | Usado para formar blocos ou grupos, não como foco principal.    |
| Critério mínimo de PRs   | Seleção de repositórios com volume mínimo (ex.: ≥ 500 PRs rejeitados) para garantir base de dados.| Mantido constante como critério de inclusão de projetos.        |


## 8.7 Possíveis variáveis de confusão conhecidas
Identifique fatores que podem distorcer os resultados (como diferenças de contexto, motivação ou carga de trabalho) e que você pretende monitorar.

| **Variável de confusão**              | **Descrição**                                                                                                            | **Como será tratada**                                                   |
|---------------------------------------|--------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
| Cultura de revisão do projeto         | Diferenças de rigor, estilo e critérios de revisão entre projetos, que podem afetar taxas de rejeição e motivos declarados. | Monitorada por comparação entre projetos e discutida como possível viés. |
| Motivação / carga de trabalho dos revisores | Situações de sobrecarga, pouco tempo ou baixa motivação, que podem levar a decisões mais rápidas ou mais restritivas.   | Não é observável diretamente; será reconhecida e discutida como limitação. |

# 9. Desenho experimental
## 9.1 Tipo de desenho (completamente randomizado, blocos, fatorial, etc.)
Indique qual tipo de desenho será utilizado e justifique brevemente por que ele é adequado ao problema e às restrições.

O estudo adota um desenho de Estudo Observacional Retrospectivo,  classificado no contexto de Engenharia de Software como Mining Software Repositories - MSR.

Justificativa: Não haverá intervenção direta no ambiente de desenvolvimento ou manipulação de variáveis em tempo real (o que caracterizaria um experimento controlado). Ao invés disso, o estudo analisa dados históricos de Pull Requests que já foram processados, aceitos ou rejeitados. O objetivo é observar correlações e padrões de causa e efeito, rejeição, baseando-se em eventos passados, permitindo a análise de um volume de dados muito superior ao que seria viável em um experimento laboratorial controlada.

## 9.2 Randomização e alocação
Explique o que será randomizado (sujeitos, tarefas, ordem de tratamentos) e como a randomização será feita na prática (ferramentas, procedimentos).

Como o estudo é observacional, não haverá randomização de sujeitos, tarefas ou tratamentos no sentido clássico, uma vez que os Pull Requests já foram criados, revisados e aceitos ou rejeitados antes do início do experimento. A randomização será aplicada estritamente na ordem de análise dos dados para evitar viés de inspeção manual ou subjetividade durante a leitura. Por exemplo, ao inspecionar os comentários para refinar as categorias dos motivos de rejeição, a leitura será feita em uma ordem aleatória para impedir que padrões temporais ou fadiga influenciem a classificação.

Além disso, quando for tecnicamente inviável analisar o conjunto total de dados manualmente — como na etapa de rotulação humana para treinar ou validar o algoritmo de NLP — selecionarei amostras menores (por exemplo, 100 PRs rejeitados) através de sorteio aleatório a partir do conjunto maior. Para operacionalizar isso, utilizarei scripts em Python com funções nativas de randomização ou comandos de amostragem em arquivos CSV, garantindo que a escolha não seja tendenciosa. É importante deixar claro que esse processo se refere apenas à seleção de subconjuntos para inspeção e não implica na alocação de tratamentos aos participantes.

## 9.3 Balanceamento e contrabalanço
Descreva como você garantirá que os grupos fiquem comparáveis (balanceamento) e como lidará com efeitos de ordem ou aprendizagem (contrabalanço).

É esperado que a base de dados extraída do GitHub apresente um desbalanceamento natural, pois na prática existem muito mais PRs pequenos e simples do que contribuições complexas, assim como a quantidade de PRs aceitos costuma superar a de rejeitados. Não realizarei um balanceamento artificial ou descarte aleatório de dados durante a coleta para tentar igualar os grupos, pois isso distorceria a realidade do ecossistema que estamos tentando entender. Para mitigar o impacto desse desbalanceamento na validade das conclusões, o controle será feito na etapa de análise estatística, utilizando testes não paramétricos que são robustos a distribuições não normais e capazes de lidar com grupos de tamanhos desiguais.

## 9.4 Número de grupos e sessões
Informe quantos grupos existirão e quantas sessões ou rodadas cada sujeito ou grupo irá executar, com uma breve justificativa.

O experimento consiste em uma única fase de execução focada na mineração e processamento dos dados. Os grupos de comparação não são segregados antes do início do estudo, mas sim categorizados a posteriori com base nos níveis das variáveis independentes coletadas. Dessa forma, os PRs serão divididos logicamente durante a análise entre grupos de alta e baixa complexidade, grupos de autores com e sem experiência prévia no projeto, e grupos de contribuições que possuem ou não testes automatizados, permitindo o cruzamento dessas características com os motivos de rejeição identificados.

## 9.5 Fluxograma

![Fluxograma do desenho experimental detalhando a coleta e análise de dados](/imgs/fluxograma.png)

# 10. População, sujeitos e amostragem
## 10.1 População-alvo
Descreva qual é a população real que você deseja representar com o experimento (por exemplo, “desenvolvedores Java de times de produto web”).

A população-alvo deste estudo é formada por colaboradores de projetos de software Open Source que utilizam o GitHub como plataforma principal de desenvolvimento e adotam um fluxo de trabalho baseado em Pull Requests. Isso inclui autores de PRs, revisores e mantenedores que participam ativamente do processo de contribuição e revisão de código. De forma mais concreta, o estudo busca representar desenvolvedores que contribuem para projetos de médio e grande porte, com alto volume de PRs e práticas consolidadas de revisão, independentemente da linguagem de programação ou domínio específico do projeto.

## 10.2 Critérios de inclusão de sujeitos
Especifique os requisitos mínimos para um participante ser elegível (experiência, conhecimento, papel, disponibilidade, etc.).

Como o estudo é observacional e baseado em dados históricos, os sujeitos são considerados de forma indireta, a partir de suas ações registradas na plataforma. Para que um participante seja incluído, ele deve ter atuado como autor, revisor ou mantenedor em um dos repositórios selecionados. No caso dos autores, serão considerados elegíveis aqueles que tiverem enviado pelo menos um Pull Request dentro da janela temporal definida para o estudo e cujo PR contenha alterações de código ou arquivos de teste, e não apenas ajustes triviais ou mudanças cosméticas de documentação. Revisores e mantenedores serão incluídos sempre que tiverem interagido com os PRs analisados por meio de comentários, revisões de código ou decisões explícitas de aceitação ou rejeição.

## 10.3 Critérios de exclusão de sujeitos
Liste condições que impedem participação (conflitos de interesse, falta de skills essenciais, restrições legais ou éticas).

Serão excluídos do estudo participantes que não representem contribuições humanas típicas ao processo de desenvolvimento. Isso inclui contas de bots e automações que abrem PRs automaticamente (por exemplo, ferramentas de atualização de dependências) e contas que apenas executam tarefas mecânicas sem tomada de decisão humana explícita. Também serão excluídos PRs de repositórios claramente marcados como exemplos didáticos, projetos de teste ou material de treinamento, quando isso estiver sinalizado na própria descrição do repositório, para evitar que padrões artificiais de sala de aula distorçam os resultados.

## 10.4 Tamanho da amostra planejado (por grupo)
Defina quantos participantes você pretende ter no total e em cada grupo, relacionando a decisão com poder, recursos e contexto.

O tamanho da amostra será definido com base na disponibilidade de dados em repositórios com alta atividade. O plano é trabalhar com projetos que possuam pelo menos 3000 Pull Requests rejeitados, o que já garante uma base robusta para análises estatísticas. Considerando dois ou mais repositórios que atendam a esse critério, espera-se obter, no mínimo, alguns milhares de PRs no conjunto total de dados, incluindo tanto PRs rejeitados quanto aceitos, para permitir comparações entre grupos. Em termos de grupos analíticos, pretende-se formar conjuntos suficientemente grandes de PRs pequenos, médios e grandes, bem como grupos com e sem testes e com autores de diferentes níveis de experiência. A ideia não é fixar um número exato de participantes por grupo, como em experimentos controlados com pessoas em laboratório, mas sim ter uma quantidade razoável de observações.

## 10.5 Método de seleção / recrutamento
Explique como os participantes serão escolhidos (amostra de conveniência, sorteio, convite aberto, turma de disciplina, time específico).

O processo de seleção ocorrerá em duas etapas principais. Primeiro, serão escolhidos os repositórios que atendam aos critérios de inclusão, como volume mínimo de PRs rejeitados, atividade contínua e relevância no ecossistema Open Source. Essa seleção poderá ser feita por conveniência, a partir de listas públicas de projetos populares ou bem avaliados, sempre buscando diversidade de domínios e tecnologias. Em seguida, dentro de cada repositório selecionado, os Pull Requests serão coletados via API, utilizando filtros por data, status (aceito ou rejeitado) e outros metadados. Caso seja necessário reduzir o volume para análises qualitativas mais detalhadas, como a rotulagem manual de motivos de rejeição, serão sorteadas amostras aleatórias ou estratificadas a partir do conjunto maior, preservando a representatividade dos grupos de interesse

## 10.6 Treinamento e preparação dos sujeitos
Descreva qual treinamento ou material preparatório será fornecido para nivelar entendimento e reduzir vieses por falta de conhecimento.

Não havera treinamento

### 11. Instrumentação e protocolo operacional
## 11.1 Instrumentos de coleta (questionários, logs, planilhas, etc.)

Os dados serão coletados atrvés de scripts em Pyhton que irão consultar a API do GitHub, e coletar as métricas selecionadas dos repositorios e seus respectivos PRs. Os scripts serão eorganizados em módulos separados para facilitar manutenção. Sendo um módulo para coleta bruta de PRs, ou outro em coleta de comentários e um terceiro voltado à derivação de métricas, como LOC, número de arquivos modificados, experiência do autor e status do PR. Para analise dos dados, serão salvos em arquivos CSV, e gerados a partir de scripts gráficos e tabelas para visualização e compreensão melhor dos dados.

## 11.2 Materiais de suporte (instruções, guias)

Serão documentados, como forma de manual, os passo a passo para conseguir executar os scripts de coletas, quais as versões das dependencias e como instala-las, configuração de tokens de acesso da API do GitHub além do mapa da metodologia para conseguir compreender e replicar todas as partes da pesquisa.

## 11.3 Procedimento experimental (protocolo – visão passo a passo)

Primeiro seleciona os repositórios que possuem no mínimo 2000 PRs rejeitados e que são Open Source. Após essa seleção inicial, o pesquisador configura o ambiente de execução dos scripts, incluindo instalação de dependências, configuração do token de acesso da API do GitHub. Em seguida, são executados os scripts de coleta, que consultam a API, percorrem os PRs de cada repositório, armazenam os dados relevantes e extraem também os comentários associados a cada PR.

Com os dados brutos coletados, é iniciado a etapa de limpeza e preparação, removendo registros duplicados, identificação de PRs automáticos ou de bots, correção de campos inconsistentes e cálculo das métricas como LOC, número de arquivos, commits, experiência do autor tempo até rejeição, etc. Nessa mesma etapa é feita uma exploração dos comentários para verificar se os textos conseguem ser classificados por motivos. Depois seleciona uma  amostra de PRs rejeitados para fazer uma rotulagem semi-automática dos motivos de rejeição.

Após a rotulagem e as métricas em mãos, os dados são organizados em conjuntos adequados para análise estatística, com grupos definidos por tamanho de PR, presença de testes, experiência do autor e projeto. Depois  serão aplicados os testes e análises. Por fim, os resultados são interpretados e comparados com hipóteses formuladas chegando a uma conclusão.

## 11.4 Plano de piloto (se haverá piloto, escopo e critérios de ajuste)

Será realizado um piloto com uma coleta de teste em um conjunto reduzido de repositórios, com o objetivo principal de verificar se todas as métricas estão sendo coletadas e calculadas corretamente. Nessa fase, os scripts serão executados em escala menor para identificar problemas nas requisições à API, como erros de autenticação, campos ausentes ou impactos de rate limit, permitindo ajustar tanto a lógica de coleta quanto mecanismos de retry, paginação e pausas entre requisições.

### 12. Plano de análise de dados (pré-execução)
## 12.1 Estratégia geral de análise (como responderá às questões)

A analise usara métricas quantitativas extraídas dos Pull Requests com avaliação qualitativa dos comentários associados às rejeições. Para analisar os motivos mais recorrentes, será utilizada a classificação temática dos comentários, permitindo identificar padrões, categorias e frequências. Para a analise do impacto do tamanho e do volume de mudanças na rejeição, serão comparadas distribuições de métricas como LOC, número de commits e arquivos modificados entre PRs aceitos e PRs rejeitados. E para as diferenças entre projetos, será respondida por meio da comparação estatística entre repositórios, analisando se a taxa de rejeição, a distribuição dos motivos e as características dos PRs variam de forma significativa entre contextos diferntes.

## 12.2 Métodos estatísticos planejados
Liste os principais testes ou técnicas estatísticas que pretende usar (por exemplo, t-teste, ANOVA, testes não paramétricos, regressão).

Os métodos estatísticos previstos incluem testes não paramétricos como Mann-Whitney U para comparar medidas contínuas entre grupos (por exemplo, LOC de PRs aceitos vs. rejeitados), já que distribuições de PRs tendem a ser assimétricas. Para variáveis categóricas, como presença/ausência de testes ou tipo de motivo de rejeição, serão aplicados testes de qui-quadrado para avaliar associação entre categorias. Caso seja necessário modelar influencers múltiplos simultaneamente, também poderá ser empregada regressão logística para estimar a probabilidade de rejeição com base em múltiplos fatores (tamanho, experiência do autor, número de commits etc.). Para comparações entre projetos, serão utilizadas análises segmentadas por repositório e testes de diferença entre taxas, complementados por visualizações de distribuição e densidade.

## 12.3 Tratamento de dados faltantes e outliers

Caso tenha ausensia de informação estrutural, como PR sem comentário,o valor vai ser considerado ainda como categoria válida. Mas se a ausencia for erro na coleta, o PR será removido da métrica específica, mas não de toda a analise. Em relação aos outliers, serão identificados atraves dos gráficos boxplots e histogramas, dessa forma se caso for identificado comportamentos reais, como por exemplo, PRs muito grandes, serão mantidos na análise específica, mas não deixaram de ser excluidos de analises especificas se houver visivelmente um erro na API ou contagem incorreta.

## 12.4 Plano de análise para dados qualitativos (se houver)

Os comentários dos PRs rejeitados serão analisados por meio de codificação qualitativa, seguindo um processo de atribuição de categorias, como falta de testes, mudança muito grande, violação de padrão, violação da arquitetura, escopo inadequado, etc. A codificação será inicializada de forma aberta, podendo serem criadas novas categorias ou associadas a outras ja existentes em cada analise de PR. A frequência de cada categoria será quantificada, com isso vai ser possível identificar os motivos mais comuns citados pelos revisores e comparar padrões entre projetos.

### 13. Avaliação de validade (ameaças e mitigação)
## 13.1 Validade de conclusão
Liste ameaças que podem comprometer a robustez das conclusões estatísticas (baixo poder, violação de suposições, erros de medida) e como pretende mitigá-las.

## 13.2 Validade interna
Identifique ameaças relacionadas a causas alternativas para os efeitos observados (history, maturation, selection, etc.) e explique suas estratégias de controle.

## 13.3 Validade de constructo
Refleta se as medidas escolhidas realmente representam os conceitos de interesse e descreva como você reduzirá ambiguidades de interpretação.

## 13.4 Validade externa
Discuta em que contextos os resultados podem ser generalizados e quais diferenças de cenário podem limitar essa generalização.

## 13.5 Resumo das principais ameaças e estratégias de mitigação
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