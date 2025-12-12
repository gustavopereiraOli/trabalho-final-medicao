# Plano de Experimento – Scoping e Planejamento

## 1. Identificação básica

### 1.1 Título do experimento

Avaliação de Técnicas de Detecção de Code Smells: Ferramenta Automática vs Inspeção Humana.

### 1.2 ID / código

EXP-CS-01

### 1.3 Versão do documento e histórico de revisão

Versão atual: v3.1 (11/12/2025)

Histórico:

- v1.0 (21/11/2025): Criação inicial do plano para Entrega 1 (Identificação, Contexto e Problema).
- v2.0 (25/11/2025): Atualização do documento de acordo com a Entrega 2 (Escopo, Objetivo, Stakeholders/Impacto, Riscos de alto nível, premissas e critérios de sucesso).
- v3.0 (11/12/2025): Revisão global do texto, correção de inconsistências e preenchimento completo de todas as seções do template.
- v3.1 (11/12/2025): Definição final de ferramentas (DesigniteJava), refinamento de metas amostrais e ajustes de formatação para execução.

### 1.4 Datas (criação, última atualização)

Criação: 21/11/2025
Última atualização: 11/12/2025 (v3.0 – versão consolidada do plano de experimento)

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

Contexto acadêmico aplicado a repositórios de código aberto (ex.: projetos Java médios de GitHub). Participantes: estudantes com experiência intermediária em desenvolvimento e revisão de código. Tecnologias: linguagem Java, detector automático de code smells **DesigniteJava** (versão Community/Academic), IDE padrão (IntelliJ/Eclipse), controle de versão Git. Processo experimental: aplicação da ferramenta em um conjunto fixo de módulos seguido de inspeção humana independente.

[Nota: Ferramenta DesigniteJava selecionada por ser referência atual na detecção de smells em Java e possuir versão acadêmica acessível.]

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

Os sujeitos do experimento serão, predominantemente, estudantes de graduação em Engenharia de Software e cursos correlatos, matriculados em disciplinas de programação ou qualidade de software e com experiência prévia em desenvolvimento Java. Esses participantes atuam como revisores de código em um contexto acadêmico controlado, simulando o papel de desenvolvedores que realizam inspeções em projetos de porte médio. Não haverá, neste estudo, contratação de profissionais de mercado, mas o perfil de experiência buscado (nível intermediário) procura aproximar o comportamento observado daquele de desenvolvedores em início de carreira.

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

Plano preliminar: Meta de recrutamento de 30 participantes (mínimo viável de 20). O foco principal é obter 30–40 pares válidos de avaliações módulo×técnica para as análises principais. O número final será ajustado com base no piloto e na disponibilidade de participantes.

[Nota: Meta de 30 participantes definida para garantir poder estatístico suficiente para testes pareados com tamanho de efeito médio.]

### 10.5 Método de seleção / recrutamento

Recrutamento por convite em disciplinas relacionadas, listas de e-mail da faculdade e grupos de estudo; amostra por conveniência com tentativa de balanceamento por nível de experiência.

### 10.6 Treinamento e preparação dos sujeitos

Treinamento:

- Sessão de orientação (~30–45 minutos) com definição de code smells, exemplos anotados e prática guiada (2–3 exemplos) antes das sessões reais.
- Material de apoio: guia rápido (1–2 páginas) com definições e checklist que os participantes usarão durante inspeção.
- Teste de conhecimento rápido (p.ex., 5 questões) para verificar assimilação do treinamento.

Esse treinamento tem como objetivo nivelar o conhecimento mínimo necessário sobre o conceito de code smells, padronizar o entendimento das definições operacionais utilizadas no estudo e reduzir vieses decorrentes de falta de familiaridade com a tarefa ou com a ferramenta de apoio. Somente participantes que concluírem o treinamento e atingirem um desempenho mínimo no teste de verificação (por exemplo, acerto de pelo menos 60% das questões) serão considerados aptos a participar das sessões experimentais.

---

## 11. Instrumentação e protocolo operacional

### 11.1 Instrumentos de coleta (questionários, logs, planilhas, etc.)

Instrumentos previstos:

- **Ferramenta automática (DesigniteJava)**: gerar relatórios de detecções por arquivo (export CSV/JSON) — registra local das detecções e tipo de smell.
- **Checklist/planilha de inspeção humana (Google Sheets)**: formulário para que participantes registrem detecções, tipo de smell, justificativa breve e tempo inicial/final.
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

A principal ameaça à validade de conclusão é o baixo poder estatístico decorrente de tamanho de amostra reduzido (número limitado de módulos e de participantes). Isso pode ser mitigado por meio de: (i) desenho pareado, que reduz a variabilidade entre unidades de análise; (ii) planejamento prévio para obter número mínimo de pares de observações (≈ 30–40); e (iii) reporte sistemático de tamanhos de efeito e intervalos de confiança, evitando interpretações baseadas exclusivamente em p-valores.

Outra ameaça relevante é a violação de suposições dos testes estatísticos (normalidade, independência, homocedasticidade), o que pode enviesar os resultados. Para mitigar, serão realizadas verificações exploratórias (histogramas, testes de normalidade, inspeção gráfica de resíduos) e, quando apropriado, serão utilizados testes não-paramétricos (por exemplo, Wilcoxon em vez de t pareado).

Erros de medida nas variáveis de tempo e na classificação de TP/FP/FN também podem comprometer a robustez das conclusões. Para reduzir esse risco, o protocolo estabelece: (i) medição de tempo com apoio de cronômetro ou registro automático sempre que possível; (ii) definição clara das regras de rotulagem de cada instância de smell; e (iii) uso de um conjunto de referência (ground truth) revisado por especialistas para calibrar as análises.

### 13.2 Validade interna

Entre as ameaças à validade interna destacam-se:

- **History / Maturation:** fadiga, aprendizado ou perda de motivação dos participantes ao longo da sessão podem afetar desempenho e tempo de execução. Para mitigar, serão utilizadas sessões de duração limitada, com pausas programadas, e contrabalanço da ordem dos tratamentos (parte dos módulos avaliada primeiro pela técnica automática, parte pela inspeção humana).
- **Selection:** diferenças sistemáticas de experiência entre participantes podem influenciar os resultados da inspeção humana. Essa ameaça será controlada por meio de critérios de inclusão, caracterização prévia de experiência (questionário) e, quando possível, balanceamento dos níveis de experiência entre sessões.
- **Instrumentation:** mudanças na configuração da ferramenta automática ou na forma de registrar dados podem introduzir viés. A mitigação consiste em fixar a versão e as configurações da ferramenta, utilizar scripts padronizados de execução e adotar um único modelo de planilha/checklist para registro das inspeções humanas.
- **Testing / Order effects:** o contato prévio com os módulos em um tratamento pode influenciar o desempenho no segundo tratamento. O desenho pareado com ordem contrabalançada, além de intervalos entre as técnicas, reduz esse risco.

### 13.3 Validade de constructo

A validade de constructo depende de as métricas adotadas refletirem adequadamente os conceitos de interesse (qualidade da detecção de code smells, esforço, concordância). Precisão, recall, F1, contagens de TP/FP/FN e tempo por arquivo são medidas amplamente aceitas na literatura para avaliar desempenho de detectores e esforço de análise.

Para reduzir ambiguidades, serão definidas operacionalmente as categorias de smells contempladas (por exemplo, God Class, Long Method, Feature Envy), com exemplos positivos e negativos discutidos no treinamento. As instruções de registro para humanos explicitarão quando uma detecção deve ser considerada uma instância válida, bem como como registrar casos de dúvida. O constructo de "concordância" será operacionalizado pelo coeficiente Kappa, calculado sobre a matriz de detecções/ausências por smell e por módulo, alinhado ao entendimento de concordância além do acaso.

### 13.4 Validade externa

A generalização dos resultados é limitada principalmente pelo contexto experimental: uso de estudantes em ambiente acadêmico, análise de projetos Java de código aberto de porte moderado e foco em um conjunto específico de smells. Entretanto, o perfil dos participantes (experiência intermediária) se aproxima de desenvolvedores júnior de mercado, permitindo inferências prudentes para cenários de manutenção em equipes em formação.

A extrapolação para projetos industriais de grande porte, outras linguagens de programação ou organizações com processos de revisão maduros deve ser feita com cautela. Para facilitar a avaliação da transferibilidade, o plano documenta claramente o contexto, as características dos projetos analisados e o perfil dos participantes, de modo que outros pesquisadores possam comparar com seus próprios cenários.

### 13.5 Resumo das principais ameaças e estratégias de mitigação

Principais ameaças e respectivas estratégias de mitigação:

- **Baixo poder estatístico:** uso de desenho pareado, definição de número mínimo de pares de observações e reporte de tamanhos de efeito.
- **Fadiga e efeitos de ordem:** limitação da duração das sessões, pausas programadas e contrabalanço da ordem de aplicação das técnicas.
- **Diferenças de experiência entre participantes:** critérios de inclusão, caracterização prévia de experiência e balanceamento entre sessões, além de análise estratificada por nível de experiência.
- **Erros de medida (tempo e classificação de smells):** padronização de instrumentos de coleta, treinamento prévio, checklist claro e uso de ground truth para calibração.
- **Baixa generalização:** documentação detalhada do contexto, dos projetos e do perfil dos participantes, permitindo avaliação crítica da extrapolação para outros ambientes.

---

## 14. Ética, privacidade e conformidade

### 14.1 Questões éticas (uso de sujeitos, incentivos, etc.)

O experimento envolve sujeitos humanos (estudantes), o que exige atenção a possíveis pressões indevidas para participação, riscos de exposição de desempenho individual e eventuais conflitos com avaliação acadêmica. A participação será estritamente voluntária, sem qualquer vínculo direto com notas ou aprovação nas disciplinas, e os estudantes poderão desistir a qualquer momento sem prejuízo acadêmico.

Caso sejam oferecidos incentivos (por exemplo, horas de atividades complementares), isso será comunicado de forma transparente, garantindo que o incentivo não configure coerção. Não serão coletadas informações sensíveis além de dados demográficos básicos e experiência profissional/acadêmica. Os resultados serão analisados e divulgados apenas em formato agregado, sem identificação nominal dos participantes.

### 14.2 Consentimento informado

Antes de participar, cada sujeito receberá um termo de consentimento informado contendo: objetivos do estudo, procedimentos previstos, duração estimada da sessão, riscos e desconfortos potenciais (por exemplo, fadiga, frustração com a tarefa), benefícios esperados (aprendizado, contribuição para pesquisa) e informações sobre privacidade e uso dos dados.

O termo destacará que a participação é voluntária e que o participante pode retirar seu consentimento a qualquer momento. O consentimento será registrado por meio de assinatura física ou aceite eletrônico, conforme práticas institucionais da universidade. Apenas participantes que assinarem o termo serão incluídos na amostra.

### 14.3 Privacidade e proteção de dados

Serão coletados apenas dados pessoais estritamente necessários: identificação mínima (p.ex., código ou e-mail institucional), informações demográficas básicas (sem dados sensíveis) e métricas de experiência em desenvolvimento. Para análise, os dados serão pseudoanonimizados por meio de códigos de participante, de modo que relatórios e conjuntos de dados não contenham nomes ou identificadores diretos.

Os arquivos contendo a chave de reidentificação e os dados brutos ficarão armazenados em repositório controlado (por exemplo, área restrita em serviço de nuvem institucional), com acesso limitado ao pesquisador principal e, se necessário, ao orientador. O período de retenção dos dados seguirá as políticas institucionais (por exemplo, até 5 anos após conclusão do TCC), após o qual os dados identificáveis poderão ser descartados ou anonimizados de forma permanente.

### 14.4 Aprovações necessárias (comitê de ética, jurídico, DPO, etc.)

Por envolver seres humanos, o estudo deverá seguir as diretrizes éticas da instituição de ensino. Quando aplicável, o protocolo será submetido ao comitê de ética em pesquisa ou órgão equivalente, incluindo descrição de instrumentos, termos de consentimento e forma de armazenamento de dados.

Além disso, o plano será revisado e aprovado pelo orientador do TCC e pelo professor responsável pela disciplina na qual o experimento estiver inserido. Não se espera envolvimento direto de áreas jurídicas ou DPO, uma vez que os dados são de natureza acadêmica e de baixo risco, mas qualquer exigência institucional adicional será atendida antes do início da coleta.

---

## 15. Recursos, infraestrutura e orçamento

### 15.1 Recursos humanos e papéis

Os principais recursos humanos previstos são:

- **Pesquisador principal (PI – estudante):** responsável pelo desenho detalhado do experimento, preparação dos instrumentos, condução das sessões com os participantes, consolidação e análise dos dados e elaboração dos relatórios.
- **Orientador acadêmico:** supervisiona o desenho do estudo, garante aderência a princípios metodológicos e éticos, revisa o plano, os instrumentos e os resultados, e apoia a interpretação dos achados.
- **Co-orientador ou monitores (se aplicável):** auxiliam na condução prática das sessões (organização do laboratório, esclarecimento de dúvidas operacionais, aplicação do treinamento) e na conferência de consistência dos dados coletados.
- **Participantes (estudantes):** executam as tarefas de inspeção humana, interagem com os instrumentos de coleta e respondem aos questionários pré e pós sessão.

### 15.2 Infraestrutura técnica necessária

A infraestrutura técnica necessária inclui:

- Laboratório de informática ou ambiente equivalente com máquinas padronizadas (ou notebooks pessoais previamente configurados), dotados de JDK, IDE Java (IntelliJ/Eclipse) e acesso à internet.
- Ferramenta automática de detecção de code smells selecionada (**DesigniteJava**), instalada e validada previamente.
- Repositório Git contendo os projetos Java selecionados, preferencialmente hospedado em plataforma como GitHub.
- Planilhas eletrônicas (Google Sheets/Excel) para registro das inspeções humanas e consolidação dos dados.
- Scripts e/ou ferramentas auxiliares para execução padronizada da ferramenta e coleta de logs de tempo.

### 15.3 Materiais e insumos

Materiais e insumos necessários:

- Computadores ou notebooks devidamente configurados para todos os participantes.
- Licenças de software, se a ferramenta automática ou IDE utilizada não for gratuita (idealmente, ferramentas gratuitas ou academicamente licenciadas).
- Formulários de consentimento informado impressos ou em formato digital.
- Cópias digitais do guia rápido de smells, slides de treinamento e checklists de inspeção.
- Acesso a contas institucionais de e-mail ou plataformas de comunicação para envio de instruções e links.

### 15.4 Orçamento e custos estimados

Espera-se que o experimento tenha baixo custo incremental, uma vez que utiliza principalmente infraestrutura e ferramentas já disponíveis na instituição (laboratórios, IDEs gratuitas e repositórios públicos). Os principais custos potenciais concentram-se em:

- Tempo dedicado do pesquisador, orientador e eventuais monitores.
- Eventuais licenças de ferramentas ou plugins pagos, caso a versão gratuita não seja suficiente (não previsto como obrigatório neste estudo).
- Custos de impressão de materiais (termos de consentimento, guias rápidos) se não forem utilizados apenas meios digitais.

Os custos serão, em princípio, cobertos pela própria instituição (infraestrutura existente) e pelo esforço voluntário dos envolvidos no TCC, sem necessidade de orçamento financeiro específico.

---

## 16. Cronograma, marcos e riscos operacionais

### 16.1 Macrocronograma (até o início da execução)

O macrocronograma até o início da execução pode ser sintetizado em fases:

- **Fase 1 – Planejamento e revisão do plano (nov/2025 – dez/2025):** elaboração inicial do plano de experimento, revisões sucessivas com o orientador e aprovação interna.
- **Fase 2 – Seleção de projetos e preparação de instrumentos (dez/2025 – jan/2026):** escolha dos repositórios Java, configuração da ferramenta automática, construção das planilhas e questionários e preparação do material de treinamento.
- **Fase 3 – Piloto (jan/2026):** realização de 1–2 sessões piloto com pequeno grupo de participantes, ajustes finos no protocolo e nos instrumentos.
- **Fase 4 – Revisão pós-piloto e prontidão (fev/2026):** consolidação de ajustes, verificação de infraestrutura e confirmação da disponibilidade de participantes.
- **Fase 5 – Início da execução plena (após fev/2026):** realização das sessões experimentais conforme cronograma detalhado a ser alinhado com a agenda acadêmica.

### 16.2 Dependências entre atividades

As principais dependências são:

- A submissão/aprovação ética (quando requerida) deve ocorrer antes do início do recrutamento formal de participantes.
- A seleção definitiva dos projetos Java depende da confirmação da ferramenta automática escolhida e de sua compatibilidade com os repositórios candidatos.
- A preparação do treinamento e dos materiais de apoio deve ser concluída antes da realização do piloto.
- As sessões piloto devem ocorrer antes das sessões experimentais principais, pois seus resultados podem demandar ajustes no protocolo.
- A confirmação de datas e horários das sessões com os participantes depende da disponibilidade do laboratório/infraestrutura e da agenda das disciplinas envolvidas.

### 16.3 Riscos operacionais e plano de contingência

Riscos operacionais identificados e estratégias de contingência:

- **Baixa adesão ou desistência de participantes:** ampliar canais de divulgação (turmas adicionais, lista de e-mails), flexibilizar horários de sessão e, se necessário, estender o período de coleta.
- **Indisponibilidade de laboratório ou problemas de infraestrutura:** prever janelas alternativas de uso do laboratório, possibilitar uso de notebooks pessoais previamente configurados e manter cópias locais dos repositórios e ferramentas.
- **Atrasos na aprovação ética ou institucional:** iniciar a preparação de instrumentos e materiais em paralelo e ajustar o cronograma de execução caso a aprovação demore mais que o previsto.
- **Falhas técnicas na ferramenta automática:** realizar testes extensivos antes da coleta, manter versão estável da ferramenta e documentar qualquer limitação, podendo substituir a ferramenta ou ajustar o escopo caso problemas críticos persistam.

---

## 17. Governança do experimento

### 17.1 Papéis e responsabilidades formais

A governança do experimento será estruturada da seguinte forma:

- **Decisão (accountable):** orientador acadêmico, em conjunto com o pesquisador principal, é responsável por aprovar o desenho final do experimento, eventuais mudanças relevantes e o início da execução.
- **Execução (responsible):** pesquisador principal conduz as atividades operacionais (recrutamento, treinamento, sessões de coleta, consolidação de dados) e coordena o apoio de monitores.
- **Revisão (consulted):** orientador e, se houver, co-orientador revisam instrumentos, resultados parciais e relatórios, fornecendo feedback metodológico.
- **Informados (informed):** participantes, coordenação de curso e demais stakeholders acadêmicos são mantidos informados sobre cronograma, eventuais alterações relevantes e resultados de alto nível.

### 17.2 Ritos de acompanhamento pré-execução

Serão adotados os seguintes ritos de acompanhamento antes da execução propriamente dita:

- Reuniões periódicas (por exemplo, quinzenais) entre pesquisador principal e orientador para revisar o progresso do plano, discutir decisões de desenho e avaliar riscos.
- Checkpoints específicos para: (i) validação dos instrumentos de coleta; (ii) conclusão da preparação do material de treinamento; e (iii) aprovação final do protocolo antes da submissão ética (quando aplicável).
- Registro sucinto das decisões e pendências em ata ou documento compartilhado, garantindo rastreabilidade das mudanças realizadas no plano.

### 17.3 Processo de controle de mudanças no plano

Qualquer alteração relevante no desenho experimental, escopo, instrumentos ou protocolo operacional deverá seguir um processo explícito de controle de mudanças:

1. O pesquisador principal documenta a proposta de mudança (justificativa, impacto esperado, riscos) em um registro de alterações.
2. A proposta é discutida com o orientador (e co-orientador, se houver), que avaliam impactos metodológicos e éticos.
3. Mudanças aprovadas são incorporadas ao plano de experimento, com atualização de versão e histórico de revisão na seção de identificação básica.
4. Quando necessário, participantes e demais stakeholders são informados das alterações, especialmente se impactarem procedimentos de coleta.
5. Se a mudança alterar aspectos éticos relevantes, uma emenda pode ser submetida ao comitê de ética antes de sua implementação.

---

## 18. Plano de documentação e reprodutibilidade

### 18.1 Repositórios e convenções de nomeação

O plano de experimento, scripts, instrumentos de coleta e dados consolidados serão mantidos em um repositório Git (por exemplo, GitHub) associado ao TCC. Serão adotadas convenções de nomeação que facilitem a identificação do conteúdo, como:

- `docs/` para documentos de planejamento (plano de experimento, protocolos, termos de consentimento em formato modelo).
- `instruments/` para questionários, checklists, planilhas de coleta em branco.
- `scripts/` para automações de execução da ferramenta e tratamento inicial de dados.
- `data/` com subpastas `raw/` (dados brutos) e `processed/` (dados preparados para análise), respeitando as regras de privacidade definidas.

### 18.2 Templates e artefatos padrão

Serão utilizados os seguintes templates e artefatos padrão:

- Modelo de questionário demográfico e de experiência dos participantes.
- Template de checklist de inspeção humana por módulo/arquivo, com campos para tipo de smell, justificativa sucinta e tempo.
- Modelo de questionário pós-sessão para percepção e fadiga.
- Script padrão para execução da ferramenta automática e exportação dos resultados em formato tabular.
- Planilha-mestre para consolidação de TP/FP/FN, tempos e variáveis de contexto.

Todos esses artefatos serão mantidos na estrutura de pastas acordada no repositório e versionados junto com o restante do material.

### 18.3 Plano de empacotamento para replicação futura

Para favorecer a reprodutibilidade, o experimento será empacotado com:

- Documentação clara de instalação e uso da ferramenta automática, incluindo versões utilizadas e parâmetros de configuração.
- Guia passo a passo para replicar o protocolo (desde a seleção de projetos até a análise estatística), com exemplos de comandos e instruções para geração do dataset final.
- Scripts de análise (por exemplo, em R ou Python) documentados, permitindo recalcular as principais métricas e testes estatísticos a partir dos dados processados.
- Versões anonimizadas dos dados (quando permitido) e exemplos de saída dos instrumentos, facilitando a compreensão do formato esperado.

Esses materiais permitirão que outros pesquisadores reproduzam ou adaptem o experimento em contextos semelhantes, avaliando a robustez dos resultados.

---

## 19. Plano de comunicação

### 19.1 Públicos e mensagens-chave pré-execução

Os principais públicos e mensagens pré-execução são:

- **Participantes potenciais (estudantes):** objetivos gerais do estudo, escopo das atividades, carga horária estimada, natureza voluntária da participação e eventuais benefícios (aprendizado, certificado, horas complementares).
- **Coordenação de curso e professores das disciplinas envolvidas:** motivação acadêmica, alinhamento com objetivos de aprendizagem, cronograma proposto e uso da infraestrutura.
- **Orientador e co-orientador:** versões atualizadas do plano, riscos identificados e necessidade de decisões ou aprovações adicionais.

### 19.2 Canais e frequência de comunicação

Serão utilizados principalmente os seguintes canais de comunicação:

- E-mail institucional para convites formais, envio de instruções e links para instrumentos online.
- Ambientes virtuais de aprendizagem (por exemplo, Moodle ou sistema da universidade) e/ou grupos de mensagens (Teams/Slack) para avisos complementares aos alunos.
- Reuniões presenciais ou virtuais periódicas entre pesquisador e orientador para acompanhamento do progresso do experimento.

A frequência de comunicação com os participantes será maior nas fases de recrutamento e imediatamente antes das sessões (lembretes), reduzindo-se após a conclusão das atividades para comunicações pontuais sobre resultados agregados.

### 19.3 Pontos de comunicação obrigatórios

Serão considerados pontos de comunicação obrigatórios:

- Divulgação da aprovação e versão final do plano de experimento antes do início do recrutamento.
- Comunicação de qualquer mudança relevante de cronograma, escopo ou procedimentos que impacte diretamente os participantes (por exemplo, alteração de datas ou formato das sessões).
- Notificações de adiamento ou cancelamento de sessões experimentais já agendadas.
- Comunicação, ao final do estudo, de um resumo dos resultados agregados aos participantes e à coordenação do curso, reforçando o caráter científico e educacional da iniciativa.

---

## 20. Critérios de prontidão para execução (Definition of Ready)

### 20.1 Checklist de prontidão (itens que devem estar completos)

Os principais itens que devem estar concluídos e aprovados antes do início da execução são:

- Plano de experimento revisado e aprovado pelo orientador (e, se aplicável, pelo comitê de ética).
- Instrumentos de coleta (questionários, planilhas, checklists) finalizados, revisados e testados em piloto.
- Ferramenta automática instalada, configurada e validada nos ambientes que serão utilizados.
- Seleção definitiva dos projetos Java e preparação dos repositórios em estado estável (snapshot congelado).
- Infraestrutura técnica confirmada (laboratório reservado, máquinas configuradas, acesso a redes e repositórios).
- Materiais de treinamento finalizados e revisados.
- Mensagens e canais de comunicação preparados para recrutamento e instruções aos participantes.

### 20.2 Aprovações finais para iniciar a operação

Para o início da operação, serão necessárias as seguintes aprovações formais:

- Aceite do orientador acadêmico quanto à versão final do plano e dos instrumentos, registrado por meio de e-mail ou assinatura em documento específico.
- Aprovação, quando exigida, do comitê de ética em pesquisa ou órgão institucional equivalente, com protocolo devidamente registrado.
- Concordância do professor responsável pela disciplina em que o experimento será conduzido, especialmente no que diz respeito ao uso de tempo de aula ou atividades extraclasse.

Somente após o registro explícito dessas aprovações o experimento será considerado "pronto para execução" e o recrutamento/agenda das sessões será efetivamente iniciado.
