# Plano de Experimento – Scoping e Planejamento

## 1. Identificação básica

### 1.1 Título do experimento

Avaliação de Técnicas de Detecção de Code Smells: Ferramenta Automática vs Inspeção Humana.

### 1.2 ID / código

EXP-CS-01

### 1.3 Versão do documento e histórico de revisão

Versão: v1.0 (21/11/2025)

Histórico:

- v1.0: Criação inicial do plano para Entrega 1 (Identificação, Contexto e Problema).

Versão: v2.0 (25/11/2025)

Histórico:

- v2.0: Atualização do documento de a cordo com a Entrega 2 (Escopo, Objetivo, Stakeholders/Impacto, Riscos de alto nível, premissas e critérios de sucesso).

### 1.4 Datas (criação, última atualização)

Criação: 21/11/2025
Última atualização: 21/11/2025 (Entregável 1)

### 1.5 Autores (nome, área, contato)

Autor principal: Gustavo Pereira Oliveira – Estudante (Engenharia de Software) – contato: [gustavo.oliveira.1403216@sga.pucminas.br].

### 1.6 Responsável principal (PI / dono do experimento)

Responsável (PI): Gustavo Pereira Oliveira

### 1.7 Projeto / produto / iniciativa relacionada

Relacionado ao Trabalho de Conclusão de Curso em Engenharia de Software com foco em Qualidade de Código / Manutenibilidade. Insere-se na iniciativa acadêmica de comparação entre abordagens automatizadas e humanas de revisão de código.

---

## 2. Contexto e problema

### 2.1 Descrição do problema / oportunidade

Organizações dependem de revisões de código para identificar code smells que impactam manutenção, desempenho e evolução. Ferramentas automáticas prometem acelerar o processo, mas pode haver discrepâncias relevantes em recall (smells não detectados) ou precisão (falsos positivos), afetando decisões de refatoração e custo de qualidade. Há oportunidade de quantificar se a ferramenta analisada substitui ou apenas complementa a inspeção humana.

### 2.2 Contexto organizacional e técnico

Contexto acadêmico aplicado a repositórios de código aberto (ex.: projetos Java médios de GitHub). Participantes: estudantes com experiência intermediária em desenvolvimento e revisão de código. Tecnologias: linguagem Java, detector automático de code smells (Ferramenta X – a definir, ex.: DesigniteJava / JDeodorant), IDE padrão (IntelliJ/Eclipse), controle de versão Git. Processo experimental: aplicação da ferramenta em um conjunto fixo de módulos seguido de inspeção humana independente.

### 2.3 Trabalhos e evidências prévias (internos e externos)

Literatura sobre code smells (Fowler 1999; Lanza & Marinescu), estudos comparativos de detectores (ex.: trabalhos avaliando precisão/recall de JDeodorant, PMD, SonarQube). Evidências mostram variação significativa de concordância entre ferramentas e especialistas humanos, especialmente em smells de design (God Class, Feature Envy). Poucos estudos recentes focam custo operacional (tempo) junto com métricas clássicas de desempenho (TP/FP/FN).

### 2.4 Referencial teórico e empírico essencial

Base conceitual: code smells como indicadores de dívida técnica; métricas de avaliação (precisão, recall, F1) aplicadas à detecção; teoria da revisão de código e limitação cognitiva humana vs automação. Empírico: evidências de variabilidade de recall em smells complexos e tendência de ferramentas gerarem falsos positivos em certos padrões. O desenho considera análise pareada (mesmo módulo avaliado por ambos) para permitir teste de McNemar em discordâncias binárias (detecção vs não detecção) e t-test para comparação de tempo médio por arquivo.

---

## 3. Objetivos e questões (Goal / Question / Metric)

### 3.1 Objetivo geral (Goal template)

- **Objeto de estudo:** Técnicas de detecção de *code smells* (Ferramenta Automática vs Inspeção Humana).  
- **Propósito:** Avaliar a eficácia, precisão e custo operacional de ambas as abordagens.  
- **Foco da análise:** Precisão, recall, esforço (tempo) e concordância entre métodos.  
- **Ponto de vista:** Pesquisador acadêmico e desenvolvedores responsáveis por revisões de código.  
- **Contexto:** Projetos Java de código aberto e participantes com experiência intermediária em revisão de código.

Avaliar comparativamente a eficácia e o custo de uso de uma ferramenta automática de detecção de *code smells* em relação à inspeção humana, visando compreender diferenças de desempenho e esforço em um contexto de repositórios Java de código aberto.

### 3.2 Objetivos específicos

- **O1:** Comparar a precisão da ferramenta automática com a inspeção humana.  
- **O2:** Analisar o recall de cada abordagem para diferentes tipos de *code smells*.  
- **O3:** Avaliar o tempo necessário para a realização da inspeção humana e da análise automatizada.  
- **O4:** Medir a concordância entre a classificação da ferramenta e dos participantes humanos.

### 3.3 Questões de pesquisa / de negócio

| Objetivo | Perguntas | Métricas |
|---------|-----------|----------|
| **O1** | Q1. A precisão da ferramenta é maior, igual ou menor que a precisão humana? | M1, M2 |
| | Q2. Quais tipos de *code smells* apresentam maior divergência de precisão entre métodos? | M3, M4 |
| | Q3. Há diferença estatisticamente significativa na precisão? | M1, M5 |
| **O2** | Q4. Qual abordagem detecta mais *code smells* reais? | M6, M7 |
| | Q5. Em quais *smells* o recall humano é superior ao da ferramenta? | M7, M8 |
| | Q6. Existe diferença de recall por categoria de smell? | M6, M9 |
| **O3** | Q7. Quanto tempo cada abordagem leva em média? | M10, M11 |
| | Q8. Há variação de tempo entre participantes? | M11, M12 |
| | Q9. A ferramenta reduz esforço operacional? | M10, M12 |
| **O4** | Q10. Qual o nível de concordância entre ferramenta e humanos? | M13, M14 |
| | Q11. Quais smells têm maior discordância? | M14, M3 |
| | Q12. A concordância varia por complexidade do módulo analisado? | M15, M13 |

### 3.4 Métricas associadas (GQM)

| Métrica | Descrição | Unidade |
|--------|-----------|---------|
| **M1 – Precisão (Precision)** | TP / (TP + FP) | % |
| **M2 – Falsos Positivos** | Smells apontados indevidamente | contagem |
| **M3 – Precisão por tipo de smell** | Precisão específica por categoria | % |
| **M4 – Divergência por tipo de smell** | Discordância entre humano e ferramenta | contagem |
| **M5 – p-valor (teste estatístico)** | Significância da diferença de precisão | p |
| **M6 – Recall** | TP / (TP + FN) | % |
| **M7 – Detecções totais corretas** | Número total de smells realmente encontrados | contagem |
| **M8 – Recall por tipo de smell** | Análise por categoria | % |
| **M9 – FN por categoria** | Falsos negativos por smell | contagem |
| **M10 – Tempo total por método** | Duração total da análise | minutos |
| **M11 – Tempo médio por arquivo** | Tempo dividido por número de arquivos | minutos |
| **M12 – Variação do tempo (desvio padrão)** | Dispersão entre participantes | minutos |
| **M13 – Coeficiente Kappa** | Concordância estatística | índice (-1 a 1) |
| **M14 – Discordância total** | Casos em que humano e ferramenta divergem | contagem |
| **M15 – Complexidade (McCabe)** | Complexidade ciclomática do módulo | valor inteiro |

---

## 4. Escopo e contexto do experimento

### 4.1 Escopo funcional / de processo (incluído e excluído)

#### Incluído no escopo

- Avaliação comparativa entre ferramenta automática e inspeção humana para detecção de code smells.
- Análise de módulos Java provenientes de repositórios de código aberto.
- Coleta de métricas de precisão, recall, tempo de execução e concordância.
- Execução padronizada da ferramenta automática em ambiente controlado.
- Inspeção humana realizada por participantes previamente selecionados.

#### Excluído do escopo

- Avaliação de qualidade das recomendações de refatoração.
- Comparação entre múltiplas ferramentas automáticas.
- Análise histórica dos repositórios ou mineração longitudinal.
- Estudos de percepção qualitativa aprofundada.
- Avaliação de smells de linguagens não Java.
- Qualquer processo de CI/CD ou execução em ambiente produtivo.

### 4.2 Contexto do estudo (tipo de organização, projeto, experiência)

O estudo é conduzido em um contexto acadêmico de Engenharia de Software, com participantes estudantes de nível intermediário. Os projetos analisados são repositórios Java de código aberto, com módulos de complexidade média e tamanho adequado para inspeção manual. A criticidade é baixa, pois não envolve código de produção, porém o estudo possui relevância científica. Os participantes possuem experiência intermediária em programação Java e revisão de código, permitindo execução confiável das atividades.

### 4.3 Premissas

- Participantes possuem nível intermediário de programação e revisão de código.  
- A ferramenta selecionada é estável e funcional.  
- O conjunto de smells selecionados é suficientemente representativo.  
- Ambiente de execução permanece estável durante a coleta.

### 4.4 Restrições

- Tempo disponível reduzido para execução das sessões experimentais.
- Amostra limitada ao número de estudantes participantes da disciplina.
- Dependência de um ambiente computacional padronizado.
- Uso obrigatório de apenas uma ferramenta automática.
- Acesso exclusivamente a repositórios públicos.
- Ausência de orçamento para ferramentas pagas ou ambientes premium.

### 4.5 Limitações previstas

- Baixa generalização devido ao uso de estudantes, não profissionais.
- Restrição à linguagem Java, não abrangendo outros ecossistemas.
- Projetos selecionados podem não representar sistemas de larga escala.
- Variabilidade na interpretação humana dos smells, mesmo com treinamento.
- Tamanho reduzido da amostra impede testes estatísticos complexos.

---

## 5. Stakeholders e impacto esperado

### 5.1 Stakeholders principais

- Estudantes / participantes do experimento  
- Pesquisadores / autor do estudo  
- Comunidade acadêmica  
- Times de desenvolvimento e qualidade (usuários de ferramentas de detecção)

### 5.2 Interesses e expectativas dos stakeholders

- **Estudantes / Participantes:** experiência prática em inspeção de código e uso de ferramentas automáticas.
- **Pesquisadores / Autor:** evidências empíricas para análise comparativa de técnicas e apoio ao TCC.
- **Comunidade acadêmica:** dados replicáveis e contribuição ao corpo de conhecimento sobre code smells.
- **Times de desenvolvimento:** subsídios para avaliar adoção ou melhoria de ferramentas de detecção.

### 5.3 Impactos potenciais no processo / produto

- Suporte à decisão sobre uso de ferramentas de detecção automática.
- Melhoria potencial de processos de revisão de código.
- Evidências sobre eficácia relativa HUMANO × FERRAMENTA.
- Redução de esforço operacional caso a ferramenta apresente bom desempenho.
- Identificação de gaps ou inconsistências na automação.

---

## 6. Riscos de alto nível, premissas e critérios de sucesso

### 6.1 Riscos de alto nível (negócio, técnicos, etc.)

- **R1:** Participantes com conhecimento insuficiente → risco de baixa validade interna.  
- **R2:** Ferramenta automática com falhas ou bugs durante execução.  
- **R3:** Código-fonte selecionado não representar bem a diversidade de smells.  
- **R4:** Tempo insuficiente dos participantes para completar tarefas.

### 6.2 Critérios de sucesso globais (go / no-go)

- Coleta completa de todos os dados planejados.  
- Concordância mínima entre observadores ≥ 0,6 (Kappa).  
- Pelo menos 80% dos participantes completam todas as tarefas.  
- Variação de tempo dentro do intervalo esperado (< 20% de desvio padrão).

### 6.3 Critérios de parada antecipada (pré-execução)

O experimento deverá ser adiado ou cancelado antes de sua execução caso qualquer uma das seguintes condições ocorra:

- Indisponibilidade de participantes suficientes, impossibilitando a formação de grupos equilibrados ou reduzindo o poder estatístico abaixo do mínimo aceitável.
- Falhas críticas na ferramenta automática, como erros de execução recorrentes, incompatibilidades com o ambiente ou resultados inconsistentes que inviabilizem a coleta de dados.
- Reprovação ética ou pendência de aprovação institucional, impedindo a realização do estudo conforme normas da organização ou comitê responsável.
- Indisponibilidade do ambiente técnico, incluindo falhas em máquinas, IDEs, repositórios, sistema de controle de versão ou perda de acesso aos projetos analisados.
- Mudança significativa no escopo ou no contexto acadêmico, como alteração de calendário, realocação de disciplinas ou cancelamento de aulas que inviabilizem a logística planejada.
- Ausência de recursos mínimos, como instrutores, monitores ou infraestrutura de apoio necessária para orientar os participantes.
- Identificação de inconsistências graves no protocolo experimental, detectadas durante revisão prévia ou execução do piloto, que comprometam a validade interna ou externa do estudo.

---

## 7. Modelo conceitual e hipóteses

### 7.1 Modelo conceitual do experimento

Modelo proposto: a técnica de detecção (automática vs inspeção humana) influencia diretamente as medidas de desempenho (precisão, recall, F1), bem como o esforço (tempo) requerido. Espera-se que a ferramenta automática apresente menor esforço por arquivo e maior consistência (menor variância de tempo), mas que possa apresentar menor recall em smells subjetivos e maior taxa de falsos positivos em alguns casos. A experiência do sujeito e a complexidade do módulo atuam como covariáveis/variáveis de bloqueio que modulam tanto a performance humana quanto a concordância com a ferramenta.

Esquematicamente:

- Fatores: Técnica (Automática / Humana), Tipo de smell, Complexidade do módulo, Experiência do revisor
- Respostas: Precisão, Recall, Falsos Positivos, Tempo por arquivo, Coeficiente Kappa (concordância)

Interpretação causal esperada:

- A escolha da técnica altera a sensibilidade (recall) e a especificidade (1 - falsos positivos).
- A complexidade do módulo aumenta a probabilidade de falsos negativos para ambas as técnicas, especialmente para humanos em módulos muito complexos.
- A experiência reduz o tempo e pode aumentar a precisão humana.

### 7.2 Hipóteses formais (H0, H1)

Serão formuladas hipóteses principais alinhadas aos objetivos O1–O4:

- H01 (Precisão): H0: A precisão média da ferramenta automática é igual à precisão média da inspeção humana. H1: A precisão média difere (bilateral).
- H02 (Recall): H0: O recall médio da ferramenta automática é igual ao recall médio da inspeção humana. H1: O recall médio difere (bilateral). Em análises secundárias podemos testar direcionalmente (por exemplo, H1a: humano > ferramenta para smells de design complexos).
- H03 (Tempo): H0: O tempo médio por arquivo é igual entre as técnicas. H1: O tempo médio por arquivo é menor para a técnica automática (unilateral: ferramenta < humano).
- H04 (Concordância): H0: O coeficiente Kappa entre ferramenta e humanos é igual a 0 (concordância por acaso). H1: Kappa > 0 (concordância maior que acaso). Para interpretação prática requeremos Kappa ≥ 0,6 como limiar de aceitabilidade.

Nível de significância: α = 0,05. Para testes pareados (ex.: McNemar) e testes de diferenças de médias (t pareado ou Wilcoxon), reportaremos também intervalos de confiança de 95%.

### 7.3 Nível de significância e considerações de poder

Nível de significância: α = 0,05.

Considerações de poder: dado o caráter prático do estudo (amostra de conveniência com estudantes), espera-se poder moderado. Planeja-se coletar um número de observações (arquivos/módulos analisados) suficiente para detectar diferenças médias de efeito médio (d ≈ 0.5) com poder ≈ 0.8 em testes pareados — isso implica aproximadamente 34 pares de observações. Para a comparação entre técnicas com sujeitos múltiplos, estimativas de poder serão detalhadas no protocolo final e/ou ajustadas após piloto.

Observação: onde o poder for insuficiente usaremos testes não-paramétricos e reportaremos tamanho de efeito e intervalos de confiança em vez de apenas p-valor.

---

## 8. Variáveis, fatores, tratamentos e objetos de estudo

### 8.1 Objetos de estudo

Objetos de estudo: módulos/arquivos Java selecionados em repositórios open-source de complexidade média (por exemplo, classes com 100–800 linhas, ou métodos com McCabe entre 5–20). Cada objeto será a unidade avaliada quanto à presença/ausência de instâncias de um conjunto predefinido de code smells (p.ex., God Class, Long Method, Feature Envy, Data Class, Shotgun Surgery).

### 8.2 Sujeitos / participantes (visão geral)

Caracterize em alto nível quem serão os participantes (desenvolvedores, testadores, estudantes, etc.), sem ainda entrar em detalhes de seleção.

### 8.3 Variáveis independentes (fatores) e seus níveis

As principais variáveis independentes (fatores):

- **Técnica (fator principal)**: níveis = {`Automática` (ferramenta X), `Humana` (inspeção manual)}.
- **Tipo de smell**: níveis = {`God Class`, `Long Method`, `Feature Envy`, `Data Class`, `Shotgun Surgery`} — cada observação será classificada por tipo(es) de smell detectados.
- **Complexidade do módulo**: níveis = {`Baixa`, `Média`, `Alta`} (baseado em McCabe e tamanho em linhas).
- **Experiência do avaliador** (para inspeção humana): níveis = {`Baixa` (≤1 ano), `Intermediária` (1–3 anos), `Alta` (>3 anos)} — usada como variável de bloqueio/covariável.

### 8.4 Tratamentos (condições experimentais)

Tratamentos:

- **T1 – Ferramenta Automática**: executar a ferramenta selecionada (ex.: JDeodorant/DesigniteJava) com configuração padrão; registrar todas as detecções por arquivo, exportar relatórios e medir o tempo de execução.
- **T2 – Inspeção Humana**: participantes realizam inspeção manual por arquivo seguindo um guia e checklist padronizado; registram detecções e tempo gasto.

Combinação/estrutura: desenho pareado (cada objeto de estudo é avaliado por ambos os tratamentos), contrabalançando a ordem (metade dos casos primeiro recebe T1 depois T2; a outra metade T2→T1) para controlar efeitos de ordem/aprendizado.

### 8.5 Variáveis dependentes (respostas)

Principais variáveis dependentes:

- `Precisão (precision)` por técnica (%).
- `Recall` por técnica (%).
- `Falsos Positivos` (contagem) por técnica.
- `Falsos Negativos` (contagem) por técnica.
- `Tempo total` e `Tempo médio por arquivo` (minutos).
- `Coeficiente Kappa` (índice de concordância entre técnica automática e humana).
- `Número de detecções corretas` (TP) por tipo de smell.
- `Complexidade (McCabe)` — usada como variável auxiliar para análise estratificada.

### 8.6 Variáveis de controle / bloqueio

Variáveis de controle / bloqueio:

- Ambiente de execução da ferramenta (mesma versão, máquina padronizada).
- Versão do código (snapshot fixo dos repositórios).
- Checklist/instruções para revisores humanos (mesmo material de suporte).
- Ordem de avaliação (contrabalançada).
- Duração máxima permitida por sessão.

### 8.7 Possíveis variáveis de confusão conhecidas

Possíveis variáveis de confusão:

- Motivação e fadiga dos participantes (monitorar por questionário curto pré/ pós sessão).
- Familiaridade prévia com o projeto analisado (avaliar no formulário de perfil).
- Configurações da ferramenta não equivalentes a práticas reais (usar configurações padrão e documentar).
- Ambiguidade na definição de smell — mitigar com treinamento e exemplos anotados.

#### Tabela 1 — Variáveis e descrições

| Variável | Tipo | Descrição |
|---|---:|---|
| Precisão (Precision) | Dependente | Proporção de detecções corretas sobre todas as detecções (TP / (TP+FP)) |
| Recall | Dependente | Proporção de defeitos reais detectados (TP / (TP+FN)) |
| Falsos Positivos | Dependente | Contagem de detecções incorretas atribuídas como smell |
| Falsos Negativos | Dependente | Contagem de smells reais não detectados |
| Tempo por arquivo | Dependente | Minutos gastos analisando cada arquivo |
| Coeficiente Kappa | Dependente | Medida de concordância entre técnica e humanos |
| Técnica | Independente (fator) | `Automática` vs `Humana` |
| Tipo de smell | Independente (fator) | Categorias analisadas (God Class, Long Method, etc.) |
| Complexidade do módulo | Independente (fator/controle) | Baixa/Média/Alta baseada em McCabe |
| Experiência | Bloqueio | Nível de experiência do revisor humano |

#### Tabela 2 — Fatores, tratamentos e combinações

| Fator | Níveis / Tratamentos | Combinações / Observações |
|---|---|---|
| Técnica | `Automática` (T1), `Humana` (T2) | Cada módulo é avaliado por ambos (pareado); ordem contrabalançada |
| Tipo de smell | `God Class`, `Long Method`, `Feature Envy`, `Data Class`, `Shotgun Surgery` | Análises por categoria (estratificadas) e contagem de detecções por técnica |
| Complexidade do módulo | `Baixa`, `Média`, `Alta` | Análise estratificada; verificar interação Técnica × Complexidade |
| Experiência | `Baixa`, `Intermediária`, `Alta` | Usada em análises como covariável e para formar blocos de comparação |

Combinações: o desenho primário é pareado (T1 × T2) aplicado a objetos com variação em Tipo de smell e Complexidade; teremos então observações para cada combinação de (módulo, técnica) e analisaremos interações com Tipo de smell e Complexidade.

---

## 9. Desenho experimental

### 9.1 Tipo de desenho (completamente randomizado, blocos, fatorial, etc.)

Desenho: pareado (within-subjects) com blocos e contrabalanço. Cada objeto de estudo (módulo) será avaliado por ambas as técnicas (Automática e Humana) — isso reduz variabilidade entre módulos e aumenta poder estatístico. Haverá blocos formados por nível de complexidade e experiência; a ordem de aplicação das técnicas será randomizada/contrabalançada para controlar efeitos de ordem e aprendizagem.

### 9.2 Randomização e alocação

Randomização:

- Ordem de aplicação das técnicas por módulo será randomizada (uso de gerador pseudo-aleatório ou planilha com permutações balanceadas).
- A seleção dos módulos será por amostragem estratificada (por complexidade) a partir do conjunto de repositórios candidatos.
- Alocação de participantes a sessões será por sorteio/inscrição, buscando balanceamento por nível de experiência.

### 9.3 Balanceamento e contrabalanço

Contrabalanço:

- Metade dos módulos será avaliada primeiro pela ferramenta e depois pelo humano; a outra metade pela ordem inversa.
- Se houver N módulos, pareá-los em N/2 pares equivalentes por complexidade e por número esperado de smells, então aplicar ordens opostas.

Balanceamento por experiência:

- Distribuir participantes entre sessões de forma a manter similaridade de média de experiência por sessão.

### 9.4 Número de grupos e sessões

Número de grupos/sessões previstos:

- Sessões práticas/piloto: 1–2 sessões com 4–6 participantes para validar protocolo.
- Sessões experimentais: repetidas em blocos de 4–6 participantes por vez, dependendo da disponibilidade; cada participante realiza inspeção em um subconjunto de módulos (para limitar fadiga) e contribui para observações pareadas.

Cada participante fará inspeção manual de X módulos (ex.: 8–12) e revisará resultados da ferramenta para os mesmos módulos conforme contrabalanço; o número X será definido considerando tempo disponível e objetivo de obter pelo menos 30–40 pares válidos pós-piloto.

## 10. População, sujeitos e amostragem

### 10.1 População-alvo

População-alvo: desenvolvedores Java que realizam revisões de código em projetos de porte médio, especialmente aqueles envolvidos em manutenção evolutiva; na prática, a amostra será composta por estudantes de Engenharia de Software com experiência prática em Java (amostra de conveniência ligada à disciplina/projeto).

### 10.2 Critérios de inclusão de sujeitos

Critérios de inclusão (sujeitos):

- Experiência mínima com Java (programação acadêmica / prática) — preferencialmente ao menos 6 meses de uso.
- Disponibilidade para completar a sessão experimental (tempo estimado por participante informado no consentimento).
- Assinatura do termo de consentimento informado.

### 10.3 Critérios de exclusão de sujeitos

- Falta de conhecimento básico em Java (auto-relatado e verificado por breve questionário).
- Conflito de interesse com os repositórios analisados (ex.: autor/colaborador direto dos projetos selecionados).

### 10.4 Tamanho da amostra planejado (por grupo)

Plano preliminar: recrutar entre 20–40 participantes (amostra de conveniência). O foco principal é obter 30–40 pares válidos de avaliações módulo×técnica para as análises principais. O número final será ajustado com base no piloto e na disponibilidade de participantes.

### 10.5 Método de seleção / recrutamento

Recrutamento por convite em disciplinas relacionadas, listas de e-mail da faculdade e grupos de estudo; amostra por conveniência com tentativa de balanceamento por nível de experiência.

### 10.6 Treinamento e preparação dos sujeitos

Treinamento:

- Sessão de orientação (~30–45 minutos) com definição de code smells, exemplos anotados e prática guiada (2–3 exemplos) antes das sessões reais.
- Material de apoio: guia rápido (1–2 páginas) com definições e checklist que os participantes usarão durante inspeção.
- Teste de conhecimento rápido (p.ex., 5 questões) para verificar assimilação do treinamento.

Especifique os requisitos mínimos para um participante ser elegível (experiência, conhecimento, papel, disponibilidade, etc.).

### 10.3 Critérios de exclusão de sujeitos

Liste condições que impedem participação (conflitos de interesse, falta de skills essenciais, restrições legais ou éticas).

### 10.4 Tamanho da amostra planejado (por grupo)

Defina quantos participantes você pretende ter no total e em cada grupo, relacionando a decisão com poder, recursos e contexto.

### 10.5 Método de seleção / recrutamento

Explique como os participantes serão escolhidos (amostra de conveniência, sorteio, convite aberto, turma de disciplina, time específico).

### 10.6 Treinamento e preparação dos sujeitos

Descreva qual treinamento ou material preparatório será fornecido para nivelar entendimento e reduzir vieses por falta de conhecimento.

---

## 11. Instrumentação e protocolo operacional

### 11.1 Instrumentos de coleta (questionários, logs, planilhas, etc.)

Instrumentos previstos:

- **Ferramenta automática (ex.: JDeodorant / DesigniteJava)**: gerar relatórios de detecções por arquivo (export CSV/JSON) — registra local das detecções e tipo de smell.
- **Checklist/planilha de inspeção humana (Google Sheets / Excel)**: formulário para que participantes registrem detecções, tipo de smell, justificativa breve e tempo inicial/final.
- **Script de logging**: script simples para padronizar a execução da ferramenta e coletar tempo de execução (quando aplicável).
- **Questionários pré e pós sessão**: coleta de dados demográficos, experiência, fadiga e percepção sobre a tarefa/ferramenta.
- **Planilha-mestre (dataset)**: consolida TP/FP/FN por observação, tempo, complexidade e demais variáveis para análises.
- **Ferramenta de anotação de verdade-terreno (ground truth)**: para o piloto, equipe de referência fará anotações manuais consenso para gerar o ground-truth usado em cálculo de TP/FN.

### 11.2 Materiais de suporte (instruções, guias)

Materiais de suporte:

- Guia rápido de identificação de smells (definições e exemplos) — entregue aos participantes.
- Slides de treinamento com exemplos anotados.
- Script passo-a-passo para execução da ferramenta (para administradores).
- Formulário de consentimento informado.
- Cronograma de sessões e instruções logísticas.

### 11.3 Procedimento experimental (protocolo – visão passo a passo)

Procedimento operacional (passo a passo):

1. Recrutamento e inscrição: envio de convite, triagem por critérios e coleta do consentimento informado.
2. Pré-sessão: participante responde questionário demográfico e de experiência; recebe material de apoio.
3. Treinamento: sessão de 30–45 minutos com exemplos e exercício prático (piloto) — validação mínima de entendimento.
4. Alocação de módulos: atribuir subconjunto de módulos a cada participante, com ordem contrabalançada de tratamentos.
5. Execução da primeira técnica: participante realiza a atividade (ou a ferramenta é executada) — registra-se tempo e resultados.
6. Intervalo curto (5–10 minutos) para reduzir efeitos de fadiga quando aplicável.
7. Execução da segunda técnica para os mesmos módulos (contrabalanço garante ordem inversa para parte do conjunto).
8. Pós-sessão: participante responde questionário de percepção/fadiga; verificação de dados coletados e upload de planilha.
9. Consolidação: equipe gera ground-truth (pelo menos para subconjunto) e consolida TP/FP/FN.
10. Análise preliminar e verificação de qualidade dos dados; se necessário, recontato do participante para esclarecimentos.

#### Fluxograma operacional (visão geral)

![Fluxograma](fluxograma.PNG)

### 11.4 Plano de piloto (se haverá piloto, escopo e critérios de ajuste)

Piloto:

- Escopo: 1–2 sessões com 4–6 participantes representativos (níveis variados de experiência).
- Objetivos: validar tempo por tarefa, clareza do guia, funcionamento dos instrumentos (planilhas, scripts e export da ferramenta), e estimar variância para cálculo de tamanho de amostra.
- Critérios de ajuste: se tempo médio por participante exceder 90 minutos, reduzir número de módulos por sessão; ajustar checklist se alta variabilidade de interpretação; ajustar configuração da ferramenta se gerar muitos resultados irrelevantes.

---

## 12. Plano de análise de dados (pré-execução)

### 12.1 Estratégia geral de análise (como responderá às questões)

Estratégia geral:

- Calcular métricas por observação (arquivo × técnica): TP, FP, FN, Precision, Recall, F1, Tempo.
- Para comparação entre técnicas usar análises pareadas (mesmo módulo): McNemar para discrepâncias binárias (detectou/não detectou por smell) e teste t pareado ou Wilcoxon para diferenças de tempo/precision quando apropriado.
- Calcular Kappa para concordância entre ferramenta e humano em nível de detecção por smell.
- Realizar análises estratificadas por Tipo de smell e por Complexidade do módulo para identificar interações e padrões.
- Reportar p-valores, intervalos de confiança de 95% e tamanhos de efeito (Cohen's d ou odds ratio conforme o caso).

### 12.2 Métodos estatísticos planejados

Testes e técnicas:

- **McNemar test**: comparar detecção binária (presença/ausência) entre técnicas no nível do par (mesmo módulo).
- **Teste t pareado** ou **Wilcoxon signed-rank**: comparar tempos médios e métricas contínuas pareadas.
- **Chi-square / Fisher Exact**: comparar proporções quando amostras não emparelhadas ou contagens por categoria.
- **Coeficiente Kappa**: avaliar concordância categórica entre técnica e humanos.
- **Regressão logística** (modelos mistos se necessário): modelar probabilidade de detecção correta com covariáveis (técnica, complexidade, experiência).
- **ANOVA / modelos mistos**: para analisar efeitos de interação (Técnica × Tipo de smell × Complexidade) quando apropriado.
- **Correções para múltiplos testes** (p.ex., Benjamini-Hochberg) quando necessário.

### 12.3 Tratamento de dados faltantes e outliers

Política para dados faltantes e outliers:

- Dados faltantes por participante: tentar recuperação por contato; se não possível, excluir as observações incompletas da análise pareada, reportando o número de exclusões e realizar análise de sensibilidade.
- Outliers de tempo: definir limites plausíveis (p.ex., z-score > 3 ou tempo > 3× mediana) e investigar manualmente; manter ou excluir com justificativa documentada.
- Missing-at-random: considerar imputação simples (média/median) apenas para variáveis auxiliares; para variáveis resposta evitar imputação e tratar por análise de sensibilidade.

### 12.4 Plano de análise para dados qualitativos (se houver)

Análise qualitativa:

- Comentários livres dos participantes serão codificados por dois revisores independentes (codificação aberta → axial → categorias), buscando temas recorrentes (dificuldades, percepções de utilidade, sugestões).
- Relatórios de discrepância entre ferramenta e humano terão análise qualitativa para identificar padrões de erro (ex.: tipos de código que confundem a ferramenta).
- Sumário descritivo e citações exemplares serão incluídos no relatório final.

--

Fim das adições para Entregas 3 e 4.

---

## 13. Avaliação de validade (ameaças e mitigação)

### 13.1 Validade de conclusão

Liste ameaças que podem comprometer a robustez das conclusões estatísticas (baixo poder, violação de suposições, erros de medida) e como pretende mitigá-las.

### 13.2 Validade interna

Identifique ameaças relacionadas a causas alternativas para os efeitos observados (history, maturation, selection, etc.) e explique suas estratégias de controle.

### 13.3 Validade de constructo

Refleta se as medidas escolhidas realmente representam os conceitos de interesse e descreva como você reduzirá ambiguidades de interpretação.

### 13.4 Validade externa

Discuta em que contextos os resultados podem ser generalizados e quais diferenças de cenário podem limitar essa generalização.

### 13.5 Resumo das principais ameaças e estratégias de mitigação

Faça uma síntese das ameaças mais críticas e das ações planejadas, de preferência em forma de lista ou tabela simples.

---

## 14. Ética, privacidade e conformidade

### 14.1 Questões éticas (uso de sujeitos, incentivos, etc.)

Descreva potenciais questões éticas (pressão para participar, uso de estudantes, incentivos, riscos de exposição) e como serão tratadas.

### 14.2 Consentimento informado

Explique como os participantes serão informados sobre objetivos, riscos, benefícios e como registrarão seu consentimento.

### 14.3 Privacidade e proteção de dados

Indique que dados pessoais serão coletados, como serão protegidos (anonimização, pseudoanonimização, controle de acesso) e por quanto tempo serão mantidos.

### 14.4 Aprovações necessárias (comitê de ética, jurídico, DPO, etc.)

Liste órgãos ou pessoas que precisam aprovar o experimento (comitê de ética, jurídico, DPO, gestores) e o status atual dessas aprovações.

---

## 15. Recursos, infraestrutura e orçamento

### 15.1 Recursos humanos e papéis

Identifique os membros da equipe do experimento e descreva brevemente o papel e responsabilidade de cada um.

### 15.2 Infraestrutura técnica necessária

Liste ambientes, servidores, ferramentas, repositórios e integrações que devem estar disponíveis para executar o experimento.

### 15.3 Materiais e insumos

Relacione materiais físicos ou digitais necessários (máquinas, licenças, formulários, dispositivos) que precisam estar prontos antes da operação.

### 15.4 Orçamento e custos estimados

Faça uma estimativa dos principais custos envolvidos (horas de pessoas, serviços, licenças, infraestrutura) e a fonte de financiamento.

---

## 16. Cronograma, marcos e riscos operacionais

### 16.1 Macrocronograma (até o início da execução)

Defina as principais datas e marcos (conclusão do plano, piloto, revisão, início da operação) com uma visão de tempo realista.

### 16.2 Dependências entre atividades

Indique quais atividades dependem de outras para começar (por exemplo, treinamento após aprovação ética), deixando essas dependências claras.

### 16.3 Riscos operacionais e plano de contingência

Liste riscos ligados a cronograma, disponibilidade de pessoas ou recursos, e descreva ações de contingência caso esses riscos se materializem.

---

## 17. Governança do experimento

### 17.1 Papéis e responsabilidades formais

Defina quem decide, quem executa, quem revisa e quem apenas deve ser informado, deixando claro o fluxo de responsabilidade.

### 17.2 Ritos de acompanhamento pré-execução

Descreva as reuniões, checkpoints e revisões previstos antes da execução, incluindo frequência e participantes.

### 17.3 Processo de controle de mudanças no plano

Explique como mudanças no desenho ou no escopo do experimento serão propostas, analisadas, aprovadas e registradas.

---

## 18. Plano de documentação e reprodutibilidade

### 18.1 Repositórios e convenções de nomeação

Indique onde o plano, instrumentos, scripts e dados (futuros) serão armazenados e quais convenções de nomes serão usadas.

### 18.2 Templates e artefatos padrão

Liste os modelos (questionários, formulários, checklists, scripts) que serão usados e onde podem ser encontrados.

### 18.3 Plano de empacotamento para replicação futura

Descreva o que será organizado desde já (documentos, scripts, instruções) para facilitar a replicação do experimento por outras equipes ou no futuro.

---

## 19. Plano de comunicação

### 19.1 Públicos e mensagens-chave pré-execução

Liste os grupos que precisam ser comunicados e quais mensagens principais devem receber (objetivos, escopo, datas, impactos esperados).

### 19.2 Canais e frequência de comunicação

Defina por quais canais (e-mail, reuniões, Slack/Teams, etc.) e com que frequência as comunicações serão feitas.

### 19.3 Pontos de comunicação obrigatórios

Especifique os eventos que exigem comunicação formal (aprovação do plano, mudanças relevantes, adiamentos, cancelamentos).

---

## 20. Critérios de prontidão para execução (Definition of Ready)

### 20.1 Checklist de prontidão (itens que devem estar completos)

Liste os itens que precisam estar finalizados e aprovados (plano, instrumentos, aprovação ética, recursos, comunicação) para autorizar o início da operação.

### 20.2 Aprovações finais para iniciar a operação

Indique quem precisa dar o “ok final” (nomes ou cargos) e como esse aceite será registrado antes da execução começar.
