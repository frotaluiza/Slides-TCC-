# Roteiro Completo para Treino — TCC V-AGMD
## Texto dos Slides + Explicações Expandidas

---

## INTRODUÇÃO AOS CONCEITOS DE MACHINE LEARNING

### O que é Machine Learning?

**Machine Learning (Aprendizado de Máquina)** é uma subárea da Inteligência Artificial que desenvolve algoritmos capazes de **aprender padrões a partir de dados**, sem serem explicitamente programados para cada regra específica.

> **Definição formal (Mitchell, 1997):** "Um programa aprende com a experiência E em relação a uma tarefa T e uma medida de desempenho P, se seu desempenho em T, medido por P, melhora com a experiência E."

### Tipos de Problemas em ML

| Tipo | Descrição | Exemplo | Saída |
|------|-----------|---------|-------|
| **Classificação** | Prever categoria/classe | Email spam ou não | Discreta (0, 1, 2...) |
| **Regressão** | Prever valor contínuo | Preço de imóvel, temperatura | Contínua (R) |
| **Clustering** | Agrupar sem rótulos | Segmentação de clientes | Grupos não supervisionados |

### Por que este TCC é um Problema de Regressão?

**Nosso problema:**
- **Entradas (X):** Temperatura de alimentação (60-80°C), Temperatura de refrigeração (20-35°C), Vazão (20-80 L/h), Pressão de vácuo (-600 a -400 mbar), Concentração salina (10-70 g/L)
- **Saídas (Y):** Fluxo de permeado (L/h), Temperatura de saída da alimentação (°C), Temperatura de saída da refrigeração (°C)

**Por que regressão?**
1. As saídas são **valores contínuos** (não categorias)
2. Queremos prever **quantidades físicas** mensuráveis
3. O erro é medido em **unidades físicas** (°C, L/h)

> **Na apresentação, dizer:** "Este trabalho se enquadra no campo da **regressão supervisionada**: dado um conjunto de variáveis de entrada — as condições operacionais do V-AGMD — queremos prever variáveis de saída contínuas — o fluxo de permeado e as temperaturas de saída."

---

## SLIDE 1 — Título

**Texto do slide:**
> Modelagem Híbrida com Regularização Física e Seleção de Modelos para Predição de Desempenho em Destilação por Membranas

**Fala:**
"Boa tarde. Este é o meu projeto final de graduação, cujo título é 'Modelagem Híbrida com Regularização Física e Seleção de Modelos para Predição de Desempenho em Destilação por Membranas'."

**Tempo:** ~30 segundos

---

## SLIDE 2 — Sumário

**Texto do slide:**
> Introdução, Revisão Bibliográfica, Fundamentação Teórica, Metodologia Proposta, Resultados, Conclusões, Referências

**Fala:**
"Este é o sumário do TCC: vamos começar com a introdução, depois revisão bibliográfica, fundamentação teórica, metodologia proposta, seguindo para resultados, conclusões e referências."

**Tempo:** ~30 segundos

---

## SLIDE 3 — A Crise Global da Água

**Texto do slide:**
> - 4 bilhões de pessoas enfrentam escassez severa ≥1 mês/ano (Mekonnen & Hoekstra, 2016)
> - 2,2 bilhões sem acesso a água potável segura (WHO, 2023)
> - Demanda global deve superar oferta em 40% até 2030 (IDRA, 2026)

**Fala:**
"A crise global da água é tanto de quantidade quanto de qualidade. 4 bilhões de pessoas enfrentam escassez severa de água — apontar o número no slide. 2,2 bilhões não têm acesso a água potável segura. E a demanda global deve superar a oferta em 40% até 2030."

**Tempo:** ~1 minuto

---

## SLIDE 4 — O Problema no Brasil

**Texto do slide:**
> - 2026: ano desafiador — chuvas abaixo da média; Cantareira ≈ 30% (ANA — Agência Nacional de Águas)
> - Nordeste: 4 meses de chuva e 8 meses de seca extrema (ANA)
> - Dessalinização: custo de R$ 2,63–4,21/m³, competitivo com tarifas industriais (estudo CNI, 2026)
> - Maior planta do Brasil (ES): atende demanda de 80 mil pessoas
> - 8.500 km de costa → enorme potencial para expandir (IBGE)

**Fala:**
"No Brasil, 2026 foi um ano desafiador. O Sistema Cantareira operou a aproximadamente 30% da capacidade — apontar o dado. No Nordeste, são 4 meses de chuva para 8 meses de seca extrema. A dessalinização pode reduzir o custo da água em até 10 vezes, de R$ 2,63 a R$ 4,21 por metro cúbico, segundo estudo da CNI — Confederação Nacional da Indústria. A maior planta do Brasil, no Espírito Santo, atende 80 mil pessoas. Com 8.500 km de costa, o potencial de expansão é enorme."

**✅ ALTERAÇÃO DA ORIENTADORA:** Dados referenciados como CNI (fonte oficial), não apenas "notícias".

**Tempo:** ~1 minuto

---

## SLIDE 5 — O V-AGMD no Contexto da Dessalinização

**Texto do slide:**
> - Dessalinização divide-se em: Processos térmicos (destilação convencional) / Processos de membrana (osmose inversa, MD)
> - Destilação por Membrana (MD): processo híbrido termo-membrana — membrana hidrofóbica separa vapor d'água da salmoura aquecida
> - V-AGMD: configuração que combina espaço de ar (isolamento térmico) com vácuo parcial (→ menor resistência à transferência de massa do vapor, acelerando o transporte)

**Fala:**
"A dessalinização se divide em duas grandes tecnologias: processos térmicos — como a destilação convencional — e processos de membrana — como a osmose inversa e a destilação por membrana. A MD é um processo híbrido: é térmico, mas usa membrana. O V-AGMD, que é o foco deste trabalho, combina um espaço de ar — que funciona como isolante térmico — com vácuo parcial. O vácuo parcial reduz a resistência à transferência de massa do vapor, acelerando o transporte."

**✅ ALTERAÇÃO DA ORIENTADORA:** "Vácuo parcial reduz resistência à transferência de massa" — não "vácuo de ar".

**Tempo:** ~45 segundos

---

## SLIDE 6 — Ilha de Policogeração Sustentável

**Texto do slide:**
> - Protótipo pioneiro COPPE/UFRJ (2022): água potável + energia via solar térmica
> - 5 kWₑ (≈ 25 residências) + 8 kWₜ recuperáveis em micro-trocadores
> - Dessalinizador V-AGMD: produz 1.000 L/dia de água destilada (> 100 pessoas/dia)
> - Foco em comunidades remotas/off-grid (Semiárido, ilhas, O&G, áreas de desastre)
> - Potencial complementar a projetos existentes de dessalinização em locais de escassez, como o Projeto Água Doce

**Fala:**
"A Ilha de Policogeração Sustentável da COPPE, inaugurada em 2022, é o projeto que abriga este trabalho. É um sistema que integra painéis solares de alta concentração com um dessalinizador V-AGMD, produzindo eletricidade para 25 residências e água para mais de 100 pessoas por dia. O foco são comunidades remotas — apontar. O projeto tem potencial complementar ao Projeto Água Doce, programa federal para o Semiárido nordestino."

**Tempo:** ~1 minuto

---

## SLIDE 7 — Objetivos

**Texto do slide:**
> Objetivo geral: avaliar e selecionar modelos de regressão supervisionada para predição do desempenho do módulo V-AGMD (fluxo de permeado e temperaturas de saída), combinando aprendizado a partir de dados experimentais (174 pontos, 3 regimes de salinidade) com informação física proveniente de um modelo reduzido 0D já publicado pelo laboratório (LISBOA et al., 2024).

**Fala:**
"O objetivo geral é avaliar e selecionar modelos de regressão supervisionada para predição do desempenho do módulo V-AGMD — fluxo de permeado e temperaturas de saída — combinando dados experimentais — 174 pontos em 3 regimes de salinidade — com informação física de um modelo reduzido 0D já publicado pelo laboratório."

**✅ ALTERAÇÃO DA ORIENTADORA:** Motivação = o que você apresenta (prever desempenho).

**Tempo:** ~1 minuto

---

## SLIDE 8 — Abordagens de Modelagem em MD

**Texto do slide:**
> Tabela: Física (AGMD, 2D, V-AGMD) / Dados (AGMD, VMD) / Híbridos (DCMD, V-AGMD)

**Fala:**
"A revisão mostra três grandes abordagens para modelagem em MD. A abordagem física usa princípios e leis físicas — é interpretável mas cara computacionalmente. A abordagem data-driven usa apenas dados experimentais — é flexível mas dependente da qualidade dos dados. E as abordagens híbridas combinam o melhor dos dois mundos: conhecimento físico com aprendizado de máquina."

**✅ ALTERAÇÃO DA ORIENTADORA:** Deixar claro que existem modelos com dados em outras configurações (V-AGMD, PGMD), não apenas "modelos de dados".

**Tempo:** ~1,5 minutos

---

## SLIDE 9 — Panorama de Publicações

**Texto do slide:**
> Tabela: Física (4), Dados (5), Híbrida (1 - PINN), Este trabalho (RL, DT, GB, RF, MLP, Residual, PhyLoss)

**Fala:**
"Panorama consolidado das publicações. Encontrei 4 publicações usando abordagem física, 5 usando dados — redes neurais, regressões, árvores — e apenas 1 trabalho híbrido na literatura de MD: uma PINN aplicada a DCMD. Este trabalho é o único focado em V-AGMD, testando todas essas arquiteturas."

**Tempo:** ~1,5 minutos

---

## SLIDE 10 — Lacunas e Contribuições

**Texto do slide:**
> **Lacunas:** 1) Ausência de validação cruzada em geral 2) Seleção por RMSE puro favorece superparametrização 3) Híbridos em MD praticamente inexistentes
> **Contribuições:** 1) Validação cruzada por grupos 2) Critério 1-SE + menor complexidade 3) 4 arquiteturas híbridas implementadas

**Fala:**
"Identifiquei três lacunas principais na literatura. Primeira: ausência de validação cruzada em geral — a maioria usa partição única, ignorando a estrutura dos grupos experimentais. Segunda: seleção por RMSE puro, que favorece modelos desnecessariamente complexos. Terceira: modelos híbridos em MD são praticamente inexistentes. As contribuições deste trabalho respondem a essas lacunas: validação cruzada por grupos, critério 1-SE para seleção parcimoniosa, e 4 arquiteturas híbridas implementadas."

**Tempo:** ~2 minutos

---

## SLIDE 11 — Princípios da Destilação por Membranas

**Texto do slide:**
> - Processo de separação térmico com membrana hidrofóbica e porosa
> - Força motriz: gradiente térmico → diferença de pressão parcial de vapor
> - Apenas a fase vapor atravessa os poros da membrana
> - Mecanismo: evaporação na interface quente → difusão nos poros → condensação no lado frio
> - Vantagens do processo MD: temperaturas médias (60-80°C), calor residual, cogeração, tolerância à salinidade

**Fala:**
"A destilação por membranas é um processo térmico de separação. A membrana é hidrofóbica e porosa — não é filtração, a membrana não é molhada. A força motriz é o gradiente térmico: a diferença de temperatura gera diferença de pressão parcial de vapor. O mecanismo é: evaporação na interface quente — apontar —, difusão pelos poros — apontar —, e condensação no lado frio — apontar. As vantagens são do processo MD em geral: opera em temperaturas médias, compatível com calor residual e cogeração, e tem alta tolerância à salinidade."

**✅ ALTERAÇÕES DA ORIENTADORA:**
- "Filtrar" → "membrana hidrofóbica e porosa"
- Vantagens atribuídas ao **processo MD**, não à configuração específica

**Tempo:** ~1 minuto

---

## SLIDE 12 — Fundamentos de Aprendizado de Máquinas

**Texto do slide:**
> Tabela: Métricas (RMSE, R²) / Divisão dos dados / Validação Cruzada / Pré-processamento (Z-score) / Correlação (Pearson, Spearman)

**Fala expandida:**
"Machine Learning é uma subárea da IA que aprende padrões a partir de dados. Dentro do ML, temos problemas de **classificação** — prever categorias — e **regressão** — prever valores contínuos. Este trabalho é um problema de **regressão supervisionada**: queremos prever fluxo e temperaturas, que são valores contínuos, não categorias.

A tabela mostra os fundamentos. As **métricas**: RMSE mede o erro na mesma unidade dos dados; R² mede a proporção da variância explicada — e pode ser negativo quando o modelo é pior que a média. A **divisão dos dados** separa treino, validação e teste. A **validação cruzada** repete essa divisão múltiplas vezes para estimar estabilidade. O **pré-processamento** por Z-score coloca todas as variáveis na mesma escala. E a **correlação** de Pearson mede relações lineares, enquanto Spearman captura relações monotônicas."

**Tempo:** ~1,5 minutos

---

## SLIDE 13 — Famílias de Modelos I — Regressão Linear

**Texto do slide:**
> Figura: Regressão linear e regularizações (OLS, Ridge, Lasso, ElasticNet)

**Fala expandida:**
"Os modelos lineares partem do OLS — Ordinary Least Squares — que é a regressão clássica. Ela minimiza a soma dos quadrados dos erros, sem nenhuma restrição. O problema é que, com muitas variáveis ou ruído, o OLS pode superajustar.

O **Ridge** adiciona uma penalização L2 — apontar na figura o termo λΣβ². Isso encolhe os coeficientes em direção a zero, mas sem zerá-los completamente. É útil quando há multicolinearidade.

O **Lasso** usa penalização L1 — apontar λΣ|β|. A diferença crucial é que o L1 pode zerar coeficientes, funcionando como seleção automática de variáveis. Se uma variável não é importante, seu coeficiente vira zero.

O **ElasticNet** combina L1 e L2 — apontar os dois termos. Herda a seleção de features do Lasso e a estabilidade do Ridge. O hiperparâmetro l1_ratio controla a mistura: 1 é Lasso puro, 0 é Ridge puro."

**✅ ALTERAÇÃO DA ORIENTADORA:** Ao falar de L1/L2, apontar explicitamente na figura.

**Tempo:** ~45 segundos a 1 minuto

---

## SLIDE 14 — Famílias de Modelos II — Árvores de Decisão

**Texto do slide:**
> Figura: Árvores de decisão (DT, RF, GB)

**Fala expandida:**
"A **Decision Tree** faz partições binárias recursivas — apontar o nó raiz e as folhas. É intuitiva, mas muito propensa a overfitting: se deixar crescer demais, decora os dados de treino.

O **Random Forest** resolve isso treinando N árvores em paralelo — apontar múltiplas árvores. Cada uma vê um subconjunto aleatório dos dados — bootstrap — e das features. A predição final é a média de todas. Isso reduz a variância e evita overfitting.

O **Gradient Boosting** trabalha em sequência — apontar as setas. Cada nova árvore é treinada para corrigir os erros — os resíduos — da combinação anterior. O learning rate controla quanto cada árvore contribui. É mais poderoso que o RF, mas mais sensível a overfitting."

**Tempo:** ~45 segundos

---

## SLIDE 15 — Famílias de Modelos III — Redes Neurais

**Texto do slide:**
> Figura: Rede neural MLP (camadas, neurônios, ativação)

**Fala expandida:**
"A **MLP** — Multi-Layer Perceptron — é uma rede neural fully connected. Temos a camada de entrada — apontar —, camadas ocultas — apontar —, e a camada de saída — apontar.

Cada neurônio faz duas operações: uma soma ponderada das entradas — apontar os pesos — seguida de uma função de ativação não linear — apontar a função. As ativações comuns são ReLU — que zera valores negativos — e tanh — que comprime entre -1 e 1, adequada para dados normalizados.

O aprendizado ajusta os pesos por **backpropagation**: calcula o erro na saída, propaga para trás, e ajusta os pesos na direção que reduz o erro. Os principais hiperparâmetros são: número de camadas e neurônios — apontar a arquitetura —, taxa de aprendizado, e regularização L2 nos pesos."

**Tempo:** ~45 segundos a 1 minuto

---

## SLIDE 16 — Famílias de Modelos IV — Arquiteturas Híbridas

**Texto do slide:**
> Figura: 4 arquiteturas híbridas (PhyInput, PhyResidual, PhyHybrid, PhyLoss)

**Fala expandida:**
"As quatro arquiteturas híbridas incorporam o modelo físico 0D de formas diferentes — apontar cada uma.

O **PhyInput** — apontar — simplesmente adiciona as predições do modelo 0D como features extras de entrada. A rede pode usar ou ignorar essa informação.

O **PhyResidual** — apontar — aprende o resíduo: a saída é Y_físico mais delta. A rede só precisa corrigir o desvio do modelo físico, não aprender o comportamento inteiro do zero.

O **PhyHybrid** — apontar — combina as duas: usa a física como entrada E produz uma correção residual.

O **PhyLoss** — apontar a função de perda — não altera a arquitetura. Em vez disso, modifica a função de perda: penaliza desvios da física durante o treinamento. O hiperparâmetro ômega controla o compromisso entre ajuste aos dados e fidelidade à física."

**Tempo:** ~30 a 45 segundos

---

## SLIDE 17 — Visão Geral dos Procedimentos

**Texto do slide:**
> Fluxograma: Dados → Preparação → Análise Exploratória → Validação e Seleção → Stage 0 → Stage 1 → Stage 2 → Selecionado vs 0D

**Fala:**
"Visão geral dos procedimentos: começo com os dados experimentais, realizo a preparação — padronização Z-score —, análise exploratória, e depois a modelagem em 3 estágios: Stage 0 com modelos clássicos, Stage 1 com redes neurais, Stage 2 com híbridos. Finalmente, o modelo selecionado é comparado com o modelo físico 0D."

**Tempo:** ~1,5 minutos

---

## SLIDE 18 — Dados Experimentais

**Texto do slide:**
> 174 pontos, 3 regimes (10, 40, 70 g/L), 5 entradas, 3 saídas

**Fala:**
"O conjunto de dados tem 174 pontos experimentais do sistema V-AGMD piloto, disponibilizado pela tese de Curcino (2025) e Lisboa et al. (2024). Foram testados 3 regimes de salinidade: 10, 40 e 70 g/L. As 5 variáveis de entrada incluem temperaturas, vazão, pressão de vácuo e concentração salina. As 3 saídas são o fluxo de permeado e as duas temperaturas de saída."

**✅ ALTERAÇÃO DA ORIENTADORA:** Citada a fonte dos dados explicitamente.

**Tempo:** ~1 minuto

---

## SLIDE 19 — Decisões da Preparação dos Dados

**Texto do slide:**
> Z-score: preserva distribuição original, mede em desvios-padrão

**Fala:**
"Escalonamento por Z-score: preserva a distribuição original dos dados e mede cada ponto em desvios-padrão da média, evitando compressão artificial na presença de valores extremos."

**Tempo:** ~1 minuto

---

## SLIDE 20 — Busca de Hiperparâmetros

**Texto do slide:**
> Busca por família e por target

**Fala expandida:**
"A busca de hiperparâmetros foi feita por família e por variável de saída — são 3 fits independentes por modelo.

Para os **lineares** — Ridge, Lasso, ElasticNet — o hiperparâmetro principal é o **alpha**, que controla a força da regularização. Alpha igual a zero equivale a OLS; alpha alto torna o modelo mais simples.

Para as **árvores**, controlamos a **profundidade máxima** — que limita a complexidade —, o **número de estimadores** no Random Forest e Gradient Boosting, e o **learning rate** no GB.

Para as **redes neurais**, a busca envolve **arquitetura** — número de camadas e neurônios —, **taxa de aprendizado**, **regularização L2** e **função de ativação**.

Para os **híbridos**, o L2 foi **congelado** da baseline — para isolar o efeito da arquitetura híbrida. O PhyLoss tem o **ômega**, que pondera física versus dados na função de perda.

Redes usaram **Random Search** — amostragem aleatória da grade — porque o espaço de busca é grande. As demais famílias usaram **GridSearchCV** — busca exaustiva — porque o espaço é menor."

**Tempo:** ~1,5 a 2 minutos

---

## SLIDE 21 — Fluxo de Validação Cruzada e Seleção

**Texto do slide:**
> GroupKFold → RMSE_CV → 1-SE → modelo mais simples

**Fala:**
"O fluxo completo: GroupKFold separa os folds por regime operacional — apontar. Calculamos o RMSE médio de validação cruzada com erro padrão. A regra do 1-SE considera todos os modelos dentro de 1 erro padrão do melhor. Entre esses, selecionamos o mais simples — o de menor complexidade."

**Tempo:** ~1 minuto

---

## SLIDE 22 — Análise Exploratória

**Texto do slide:**
> Dispersão: T_out correlacionada com entradas térmicas; fluxo com múltiplas variáveis
> Pearson: T_out |r|>0,9; fluxo |r|≈0,7
> Spearman: próximo a Pearson → relações aproximadamente lineares

**Fala:**
"Análise exploratória: as temperaturas de saída têm forte correlação linear com as entradas térmicas — |r| maior que 0,9. O fluxo é mais complexo, com correlações moderadas e distribuídas — |r| em torno de 0,7. Pearson e Spearman próximos indicam que as relações dominantes são aproximadamente lineares, o que justifica a modelagem multivariada."

**Tempo:** ~1 minuto

---

## SLIDE 23 — Modelo Físico 0D — Referência

**Texto do slide:**
> Modelo 0D de Lisboa et al. (2024) — referência fenomenológica. Não é modelo deste trabalho.

**Fala:**
"O modelo 0D de Lisboa et al. (2024) serve como referência fenomenológica para as arquiteturas híbridas. É importante deixar claro: **não é um modelo desenvolvido neste trabalho**. As arquiteturas híbridas aprendem a corrigir sistematicamente suas predições a partir dos dados experimentais."

**✅ ALTERAÇÃO DA ORIENTADORA:** Citado explicitamente que o modelo 0D é de Lisboa et al. (2024), não é trabalho seu.

**Tempo:** ~30 segundos

---

## SLIDE 24 — Síntese dos Estágios de Modelagem

**Texto do slide:**
> Stage 0: lineares similares, árvores sobreajustaram
> Stage 1: MLP melhorou Test RMSE
> Stage 2: PhyResidual menores perdas

**Fala:**
"Síntese dos três estágios: no Stage 0, as regressões lineares apresentaram desempenho similar entre si; as árvores de decisão sobreajustaram nos regimes de treino. No Stage 1, as baselines MLP melhoraram o Test RMSE em relação às regressões e árvores. No Stage 2, o PhyResidual apresentou as menores perdas, corrigindo o viés do modelo 0D."

**Tempo:** ~1 minuto

---

## SLIDE 25 — Comparação Final

**Texto do slide:**
> Tabela: T_alim (Baseline Flux 0,178), T_ref (PhyResidual 0,214), Flux (PhyResidual 0,054), 0D (1,549 / 0,851 / 0,206)

**Fala:**
"Comparação final: para T_alim_out, a Baseline Flux foi selecionada com Test RMSE de 0,178. Para T_ref_out, o PhyResidual com 0,214. Para o Flux, o PhyResidual com 0,054 — uma melhora de 73,8% sobre o modelo 0D. Note que o modelo 0D tem R² negativo para T_alim — apontar -0,404 — o que significa que ele é pior que simplesmente prever a média."

**Tempo:** ~2 minutos

---

## SLIDE 26 — Predição vs Experimental

**Texto do slide:**
> Overlay: Baseline Flux (T_alim), PhyResidual (T_ref, Flux). Quadrados cinza = modelo 0D

**Fala:**
"Overlay com os modelos selecionados: Baseline Flux para T_alim — apontar azul —, PhyResidual para T_ref — apontar laranja — e Flux — apontar verde. Os quadrados cinza representam o modelo físico 0D. Vejam como os modelos híbridos se aproximam da linha y=x — apontar — enquanto o modelo 0D apresenta dispersão, especialmente para as temperaturas."

**Tempo:** ~1 minuto

---

## SLIDE 27 — Análise por Variável de Saída

**Texto do slide:**
> Tabela: T_alim (-89,0% vs 0D), T_ref (-74,9%), Flux (-73,8%)

**Fala:**
"Análise por variável: para T_alim_out, o modelo data-driven puro foi melhor — o modelo 0D tem R² de -0,404, tornando a correção residual menos eficaz. Para T_ref_out, a diferença sobre o Ridge é marginal — 2,3% — mas o Ridge tem melhor CV, indicando melhor extrapolação. Para o Flux, o PhyResidual apresentou o menor Test e o menor CV — foi a única variável onde isso aconteceu — mostrando que aprendeu a corrigir o viés do 0D."

**Tempo:** ~2 minutos

---

## SLIDE 28 — Comentários Finais

**Texto do slide:**
> 1) Híbridos melhores em 2/3 variáveis (até 89% vs 0D)
> 2) Residual = corretor de viés
> 3) CV: PhyResidual no Flux; lineares nas temperaturas
> 4) Seleção por alvo não garante melhor performance
> 5) Extensível a outros processos

**Fala:**
"Comentários finais: as redes híbridas PhyResidual apresentaram as melhores performances para Flux e T_ref, com melhora de até 89% sobre o modelo 0D. A arquitetura residual atua como corretor de viés do modelo físico. Em capacidade de generalização, o PhyResidual domina no Flux, enquanto os lineares têm CV menor nas temperaturas — mas a diferença no Test é pequena. A seleção de hiperparâmetros por alvo não garantiu a melhor performance para aquele alvo. E o procedimento é extensível a outros processos físicos do laboratório."

**Tempo:** ~1,5 minutos

---

## SLIDE 29 — Trabalhos Futuros

**Texto do slide:**
> 1) Novos dados experimentais
> 2) Modelo 2D GITT como referência
> 3) PINNs a partir das EDOs (surrogate + híbrido)

**Fala:**
"Trabalhos futuros: primeiro, avaliar os modelos selecionados sobre novas rodadas experimentais que explorem regiões não contempladas no treinamento. Segundo, substituir o modelo 0D pelo modelo 2D GITT — de Curcino (2026) — como referência física. Terceiro, construir PINNs a partir das EDOs do modelo GITT — tanto como surrogate, apenas física, quanto no modo híbrido que incorpora dados experimentais na função de perda."

**Tempo:** ~1 minuto

---

## RESUMO — TEMPO TOTAL

| Seção | Slides | Tempo |
|-------|--------|-------|
| Introdução | 1-7 | ~6 min |
| Revisão | 8-10 | ~4 min |
| Fundamentação | 11-16 | ~5 min |
| Metodologia | 17-21 | ~6 min |
| Resultados | 22-26 | ~7 min |
| Conclusões | 27-29 | ~4 min |
| **Total** | 29 | **~32 min** |

---

## DICAS DE APRESENTAÇÃO

### Sempre apontar nos slides:
- Slide 4: número 30% (Cantareira)
- Slide 5: "vácuo parcial" e "resistência à transferência de massa"
- Slide 11: mecanismo (evaporação → difusão → condensação)
- Slide 13: termos L1 e L2 na figura
- Slide 16: cada uma das 4 arquiteturas
- Slide 25: valores de RMSE e R² negativo
- Slide 26: cores dos modelos e linha y=x

### Termos corrigidos:
| ❌ Errado | ✅ Correto |
|-----------|-----------|
| Filtrar | Membrana hidrofóbica porosa |
| Vácuo de ar | Vácuo parcial |
| Dados de notícias | Dados CNI (fonte oficial) |
| Meu modelo 0D | Modelo 0D de Lisboa et al. (2024) |

### Tempo a evitar:
- Não gastar mais de 1 minuto no Slide 11 (Princípios MD)
- Não explicar detalhadamente a figura rica do Slide 26
