# Roteiro Consolidado — Apresentação TCC V-AGMD
## Versão Final — Alinhada com os Slides Atuais + Alterações da Orientadora (30/07/26)

---

## ESTRUTURA REAL DOS SLIDES (29 slides)

| Seção | Slides | Tempo Estimado |
|-------|--------|----------------|
| Introdução | 1-7 | ~7 min |
| Revisão | 8-10 | ~4 min |
| Fundamentação | 11-16 | ~5 min |
| Metodologia | 17-21 | ~5 min |
| Resultados | 22-26 | ~6 min |
| Conclusões | 27-29 | ~3 min |
| Referências | 30 | — |
| **Total** | | **~30 min** |

---

## SLIDE 1 — Título

Boa tarde. Este é o meu projeto final de graduação, cujo título é **"Modelagem Híbrida com Regularização Física e Seleção de Modelos para Predição de Desempenho em Destilação por Membranas"**.

---

## SLIDE 2 — Sumário

Este é o sumário do TCC: vamos começar com a **introdução**, depois **revisão bibliográfica**, **fundamentação teórica**, **metodologia proposta**, seguindo para **resultados**, **conclusões** e **referências**.

---

## SLIDE 3 — A Crise Global da Água

A crise global da água é tanto de quantidade quanto de qualidade. **4 bilhões** de pessoas enfrentam escassez severa de água, sendo que **2,2 bilhões** não têm acesso a água potável segura. A demanda global deve superar a oferta em **40% até 2030**.

> **Fontes:** Mekonnen & Hoekstra (2016), WHO (2023), IDRA (2026)

---

## SLIDE 4 — O Problema no Brasil

No Brasil, 2026 foi um ano desafiador, com chuvas abaixo da média. O **Sistema Cantareira** operou a aproximadamente **30%** da sua capacidade (ANA — Agência Nacional de Águas). No Nordeste, um cenário de **4 meses de chuva para 8 meses de seca extrema**.

A dessalinização pode reduzir o custo da água em até **10 vezes** — de R$ 2,63 a R$ 4,21/m³, segundo estudo da **CNI (Confederação Nacional da Indústria, 2026)**. A maior planta do Brasil (ES) atende **80 mil pessoas**. Com **8.500 km de costa**, o potencial de expansão é enorme.

> **✅ ALTERAÇÃO IMPLEMENTADA:** Dados referenciados como CNI (fonte oficial), não apenas "notícias".

---

## SLIDE 5 — O V-AGMD no Contexto da Dessalinização

A dessalinização divide-se em duas grandes tecnologias: processos **térmicos** (destilação convencional) e processos de **membrana** (osmose inversa, MD).

A **Destilação por Membrana (MD)** é um processo híbrido termo-membrana: uma membrana hidrofóbica separa o vapor d'água da salmoura aquecida.

A configuração **V-AGMD** combina **espaço de ar** (isolamento térmico) com **vácuo parcial**, que reduz a **resistência à transferência de massa do vapor**, acelerando o transporte.

> **✅ ALTERAÇÃO IMPLEMENTADA:** "Vácuo parcial" + "reduz resistência à transferência de massa do vapor" — não "vácuo de ar".

---

## SLIDE 6 — Ilha de Policogeração Sustentável (LabMEMS/COPPE)

Este trabalho está inserido no projeto **CT2 — Ilha de Policogeração Sustentável**, da COPPE/UFRJ (2022). É um protótipo pioneiro que une **geração de água potável** com **energia solar térmica**.

O sistema produz cerca de **5 kWₑ** (~25 residências) e mais **8 kWₜ** recuperáveis. O dessalinizador V-AGMD produz **1.000 L/dia** de água destilada (>100 pessoas/dia).

O foco são **comunidades remotas** (Semiárido, ilhas, O&G), com potencial complementar ao **Projeto Água Doce** (programa federal para o Semiárido nordestino).

---

## SLIDE 7 — Objetivos

**Objetivo geral:** avaliar e selecionar modelos de regressão supervisionada para predição do desempenho do módulo V-AGMD (fluxo de permeado e temperaturas de saída), combinando aprendizado a partir de dados experimentais (174 pontos, 3 regimes de salinidade) com informação física proveniente de um modelo reduzido 0D já publicado pelo laboratório (LISBOA et al., 2024).

> **✅ ALTERAÇÃO IMPLEMENTADA:** Motivação = o que você apresenta (prever desempenho).

---

## SLIDE 8 — Abordagens de Modelagem em MD

Existem **três principais abordagens** de modelagem em destilação por membranas:

| Abordagem | Tecnologia | Descrição |
|-----------|-----------|-----------|
| **Física** | AGMD, 2D, **V-AGMD** | Modelos 0D, 1D, 2D |
| **Dados** | **AGMD**, VMD | Redes neurais e regressão |
| **Híbridos** | DCMD, **V-AGMD** | PINNs, modelos residuais, PhyLoss |

> **✅ ALTERAÇÃO IMPLEMENTADA:** Deixar claro que existem modelos com dados em outras configurações (V-AGMD, PGMD), não apenas "modelos de dados".

---

## SLIDE 9 — Panorama de Publicações em MD

| Abordagem | Nº | Modelos |
|-----------|----|---------|
| **Física** | 4 | 0D, 1D, 2D |
| **Dados** | 5 | RL, RNA, MLP, RF |
| **Híbrida** | 1 | PINN |
| **Este trabalho** | — | RL, DT, GB, RF, MLP, Residual, PhyLoss |

> **Nota:** Apenas 1 trabalho na literatura de MD explora abordagem híbrida (PINN em DCMD) — e este é o único focado em V-AGMD.

---

## SLIDE 10 — Lacunas e Contribuições

**Lacunas na literatura:**

1. **Ausência de validação cruzada em geral** — partição única ignora grupos experimentais
2. **Seleção por RMSE puro** favorece superparametrização — ignora variabilidade estatística
3. **Modelos híbridos em MD praticamente inexistentes** — apenas Shahouni (2026) aplica PINN em DCMD; nenhum em V-AGMD

**Contribuições deste trabalho:**

1. Validação cruzada por grupos (regimes experimentais)
2. Critério 1-SE + menor complexidade
3. 4 arquiteturas híbridas implementadas

> **✅ ALTERAÇÃO IMPLEMENTADA:** Lacunas e contribuições agora separadas em colunas no mesmo slide (não há redundância).

---

## SLIDE 11 — Princípios da Destilação por Membranas

A destilação por membranas é um processo térmico de separação com membrana **hidrofóbica** e **porosa**. A força motriz é o **gradiente térmico** (diferença de pressão parcial de vapor).

**Mecanismo:** evaporação na interface quente → difusão nos poros → condensação no lado frio.

**Vantagens do processo MD:**
- Opera em temperaturas médias (60-80°C)
- Compatível com calor residual e cogeração
- Elevada tolerância à salinidade — adequada onde a osmose inversa é limitada

> **✅ ALTERAÇÕES IMPLEMENTADAS:**
> - "Filtrar" → "membrana hidrofóbica e porosa"
> - Vantagens atribuídas ao **processo MD**, não à configuração específica

---

## SLIDE 12 — Fundamentos de Aprendizado de Máquinas

| Conceito | Definição | Propósito |
|----------|-----------|-----------|
| **Métricas** | RMSE, R² | RMSE: magnitude do erro; R²: variância explicada |
| **Divisão dos dados** | Hold-out (80/20) | Evitar contaminação treino/teste |
| **Validação Cruzada** | Repetir divisão, agrupando por regimes | Estimar estabilidade e extrapolação |
| **Pré-processamento** | Z-score | Colocar variáveis em escala comparável |
| **Correlação** | Pearson (linear), Spearman (monotônica) | Identificar relações entre variáveis |

> **✅ ALTERAÇÃO IMPLEMENTADA:** Tabela organizada com propósito de cada conceito.

---

## SLIDE 13 — Famílias de Modelos I — Regressão Linear

**OLS:** sem regularização — minimiza erro quadrado.

**Ridge:** penaliza L2 — encolhe coeficientes sem zerá-los.

**Lasso:** penaliza L1 — pode zerar coeficientes (seleção de features).

**ElasticNet:** combina L1 + L2.

> **✅ ALTERAÇÃO IMPLEMENTADA:** Ao falar de L1/L2, apontar explicitamente na figura.

---

## SLIDE 14 — Famílias de Modelos II — Árvores de Decisão

**Decision Tree:** partições binárias recursivas — propensa a overfitting.

**Random Forest:** várias árvores em paralelo (bagging) — reduz variância.

**Gradient Boosting:** árvores em sequência — cada uma corrige resíduos da anterior.

---

## SLIDE 15 — Famílias de Modelos III — Redes Neurais

**MLP:** camadas fully connected, ativação não linear (ReLU/tanh), backpropagation.

**Hiperparâmetros:** camadas, neurônios, ativação, learning rate, L2, dropout.

---

## SLIDE 16 — Famílias de Modelos IV — Arquiteturas Híbridas

**4 arquiteturas** que incorporam o modelo físico 0D:

- **PhyInput:** adiciona predições do 0D como features extras
- **PhyResidual:** aprende o resíduo — saída = Y_físico + Δ
- **PhyHybrid:** combina PhyInput + PhyResidual
- **PhyLoss:** física na função de perda (regularização)

> **Ação:** Apontar cada arquitetura na figura enquanto fala.

---

## SLIDE 17 — Visão Geral dos Procedimentos

**Fluxo:** Dados Experimentais → Preparação (Z-score) → Análise Exploratória → Validação e Seleção → Stage 0 (Clássicos) → Stage 1 (Redes Neurais) → Stage 2 (Híbridos) → Selecionado vs 0D

---

## SLIDE 18 — Dados Experimentais

**Fonte:** Tese de Curcino (2025) e Lisboa et al. (2024) — LabMEMS/COPPE

- **174 pontos**, **3 regimes de salinidade** (10, 40, 70 g/L NaCl)
- **5 entradas:** T_in_alim, T_in_ref, vazão_ref, P_vac, C_NaCl
- **3 saídas:** Fluxo de permeado, T_out_alim, T_out_ref

> **✅ ALTERAÇÃO IMPLEMENTADA:** Fonte dos dados citada explicitamente.

---

## SLIDE 19 — Decisões da Preparação dos Dados

| Etapa | Decisão | Justificativa |
|-------|---------|---------------|
| **Escalonamento** | Z-score | Preserva distribuição original; mede em desvios-padrão |

---

## SLIDE 20 — Busca de Hiperparâmetros

Para cada família e cada **variável de saída**, ajuste independente:

| Família | Hiperparâmetros |
|---------|-----------------|
| Lineares | α (Ridge/Lasso/ElasticNet), l1_ratio |
| Árvores | profundidade, n_estimadores, learning_rate |
| Redes | arquitetura, LR, L2, ativação |
| Híbridos | L2 congelado (da baseline), ω (PhyLoss) |

**Métodos:** Random Search (redes neurais) vs GridSearchCV (demais).

---

## SLIDE 21 — Fluxo de Validação Cruzada e Seleção

**GroupKFold** por regimes → RMSE_CV médio com erro padrão → **regra 1-SE** → seleção do modelo mais simples dentro de 1 erro padrão do melhor.

---

## SLIDE 22 — Análise Exploratória

- **Temperaturas de saída:** forte correlação linear com entradas térmicas (|r| > 0,9)
- **Fluxo:** correlações moderadas e distribuídas — justifica modelagem multivariada
- **Pearson ≈ Spearman:** relações dominantes são aproximadamente lineares

---

## SLIDE 23 — Modelo Físico 0D — Referência

O modelo 0D de **Lisboa et al. (2024)** serve como referência fenomenológica para as arquiteturas híbridas. **Não é um modelo desenvolvido neste trabalho.**

*(Gráficos: predição do modelo 0D vs experimental para cada variável)*

> **✅ ALTERAÇÃO IMPLEMENTADA:** Citado explicitamente que o modelo 0D é de Lisboa et al. (2024), não é trabalho seu.

---

## SLIDE 24 — Síntese dos Estágios de Modelagem

- **Stage 0 (lineares e árvores):** regressões lineares similares entre si; árvores sobreajustaram
- **Stage 1 (redes neurais):** baselines MLP melhoraram Test RMSE
- **Stage 2 (híbridos):** PhyResidual apresentou menores perdas, corrigindo viés do 0D

---

## SLIDE 25 — Comparação Final — Consolidado

| Variável | Estágio | Modelo | Test RMSE | CV RMSE | Test R² |
|----------|---------|--------|-----------|---------|---------|
| **T_alim,out** | Stage 1 | Baseline Flux | **0,178** | 0,081 | 0,981 |
| **T_ref,out** | Stage 2 | PhyResidual (Flux) | **0,214** | 0,346 | 0,996 |
| **Flux** | Stage 2 | PhyResidual (Flux) | **0,054** | **0,072** | **0,979** |
| **Flux** | 0D | — | 0,206 | — | 0,631 |
| **T_alim,out** | 0D | — | 1,549 | — | **-0,404** |
| **T_ref,out** | 0D | — | 0,851 | — | 0,948 |

> **Nota:** R² pode ser negativo quando o modelo é pior que a média (scikit-learn).

---

## SLIDE 26 — Predição vs Experimental

*(Overlay com modelos selecionados: Baseline Flux para T_alim, PhyResidual para T_ref e Flux. Quadrados cinza = modelo 0D)*

- **T_alim,out:** Baseline Flux (Stage 1)
- **T_ref,out:** PhyResidual (Stage 2)
- **Flux:** PhyResidual (Stage 2)

---

## SLIDE 27 — Análise por Variável de Saída

| Variável | Modelo | Test RMSE | vs 0D | vs 2º melhor |
|----------|--------|-----------|-------|--------------|
| **T_alim,out** | Baseline Flux | 0,178 | -89,0% | -2,7% vs PhyResidual |
| **T_ref,out** | PhyResidual | 0,214 | -74,9% | -2,3% vs Ridge |
| **Flux** | PhyResidual | 0,054 | -73,8% | -18,2% vs Baseline |

- **T_alim,out:** modelo data-driven melhor — 0D tem R² = -0,404
- **T_ref,out:** diferença marginal (2,3%); Ridge tem melhor CV (0,244 vs 0,346)
- **Flux:** única variável com menor Test **e** CV (0,072) — PhyResidual corrigiu viés do 0D (R² 0,631 → 0,979)

---

## SLIDE 28 — Comentários Finais

1. **Híbridos (PhyResidual)** melhores em Test RMSE para Flux e T_ref — melhora de **até 89%** sobre o modelo 0D
2. **Arquitetura residual** atua como **corretor de viés** do modelo físico
3. **CV:** PhyResidual domina no Flux; lineares (OLS/Ridge) têm CV menor nas temperaturas — mas diferença no Test RMSE é pequena
4. **Seleção por alvo** não garantiu melhor performance para aquele alvo
5. Procedimento **extensível** a outros processos com modelos de referência mais complexos

---

## SLIDE 29 — Trabalhos Futuros

1. **Avaliar modelos** em novas rodadas experimentais (regiões não contempladas no treino)
2. **Substituir modelo 0D pelo 2D** (GITT — Curcino, 2026) como referência física
3. **Construir PINNs** a partir das EDOs do modelo GITT:
   - Modo **surrogate** (apenas física)
   - Modo **híbrido** (física + dados na função de perda)

---

## SLIDE 30 — Referências Bibliográficas

*(Lista completa de referências)*

---

## Checklist de Alterações da Orientadora — Status

| # | Alteração | Status | Slide |
|---|-----------|--------|-------|
| 1 | Dados Brasil como CNI (fonte oficial) | ✅ | 4 |
| 2 | "Vácuo parcial" + "reduz resistência à transferência de massa" | ✅ | 5 |
| 3 | Motivação = o que você apresenta | ✅ | 7 |
| 4 | Deixar claro dados em outras configurações | ✅ | 8 |
| 5 | Separar lacunas de contribuições | ✅ | 10 |
| 6 | "Filtrar" → "membrana hidrofóbica porosa" | ✅ | 11 |
| 7 | Vantagens atribuídas ao processo MD | ✅ | 11 |
| 8 | Reduzir tempo slide 16 (não 5 min) | ✅ | 16 |
| 9 | Explicar L1/L2 apontando na figura | ✅ | 13 |
| 10 | Apontar nos slides o que está falando | ✅ | 16 |
| 11 | Citada fonte dos dados (Lisboa et al.) | ✅ | 18 |
| 12 | Legenda de cores (linear/rede/híbrido) | ✅ | 26 |
| 13 | Não explicar figura rica em detalhes | ✅ | 22 |
| 14 | Modelo 0D citado como referência | ✅ | 23 |
| 15 | Tabelas consolidadas | ✅ | 25 |
| 16 | Discussão cuidadosa do 0D | ✅ | 27 |
| 17 | Gráficos para mostrar resultados | ✅ | 26 |
| 18 | R² negativo com referência | ✅ | 25 |

---

## Notas de Tempo por Slide

| Slide | Tempo | Observação |
|-------|-------|------------|
| 1-2 | 1 min | Abertura |
| 3-4 | 2 min | Contexto água |
| 5 | 1 min | V-AGMD |
| 6-7 | 2 min | Ilha + Objetivos |
| 8-10 | 3 min | Revisão |
| 11 | 1 min | Princípios MD |
| 12-16 | 4 min | Fundamentos ML |
| 17-21 | 4 min | Metodologia |
| 22-26 | 5 min | Resultados |
| 27-29 | 3 min | Conclusões |
| **Total** | **~26 min** | + perguntas |
