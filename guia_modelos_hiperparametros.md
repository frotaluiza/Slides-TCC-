# Guia Detalhado — Modelos e Hiperparâmetros
## Material de Apoio para Apresentação TCC V-AGMD

---

## 1. MODELOS LINEARES

### 1.1 OLS (Ordinary Least Squares) — Regressão Linear Clássica

**O que faz:** Encontra a reta (ou hiperplano) que minimiza a soma dos quadrados das diferenças entre valores reais e previstos.

**Fórmula:** min Σ(yᵢ - ŷᵢ)²

**Vantagens:**
- Simples e interpretável
- Solução analítica (não iterativa)
- Base para entender modelos mais complexos

**Limitações:**
- Sem regularização → overfitting com muitas variáveis
- Assume relação linear entre variáveis
- Sensível a outliers

---

### 1.2 Ridge Regression (L2)

**O que faz:** OLS + penalidade L2 nos coeficientes. Encolhe os coeficientes em direção a zero, mas sem zerá-los completamente.

**Fórmula:** min [Σ(yᵢ - ŷᵢ)² + α·Σ(βⱼ²)]

**Hiperparâmetro:**

| Parâmetro | Descrição | Valores Testados | Efeito |
|-----------|-----------|------------------|--------|
| **alpha (α)** | Força da regularização L2 | [0.001, 0.01, 0.1, 1, 10, 100] | α=0 → OLS; α↑ → coeficientes menores, modelo mais simples |

**Quando usar:** Multicolinearidade entre variáveis (coeficientes instáveis).

---

### 1.3 Lasso Regression (L1)

**O que faz:** OLS + penalidade L1. Pode zerar coeficientes de variáveis irrelevantes — funciona como seleção automática de features.

**Fórmula:** min [Σ(yᵢ - ŷᵢ)² + α·Σ|βⱼ|]

**Hiperparâmetro:**

| Parâmetro | Descrição | Valores Testados | Efeito |
|-----------|-----------|------------------|--------|
| **alpha (α)** | Força da regularização L1 | [0.001, 0.01, 0.1, 1, 10, 100] | α=0 → OLS; α↑ → mais coeficientes zerados |

**Quando usar:** Suspeita de que muitas variáveis são irrelevantes.

---

### 1.4 ElasticNet

**O que faz:** Combina penalidades L1 e L2. Herda a seleção de features do Lasso e a estabilidade do Ridge.

**Fórmula:** min [Σ(yᵢ - ŷᵢ)² + α·ρ·Σ|βⱼ| + α·(1-ρ)/2·Σ(βⱼ²)]

**Hiperparâmetros:**

| Parâmetro | Descrição | Valores Testados | Efeito |
|-----------|-----------|------------------|--------|
| **alpha (α)** | Força total da regularização | [0.001, 0.01, 0.1, 1, 10] | Controla intensidade geral |
| **l1_ratio (ρ)** | Proporção L1 vs L2 | [0.1, 0.3, 0.5, 0.7, 0.9] | ρ=1 → Lasso puro; ρ=0 → Ridge puro |

**Quando usar:** Variáveis correlacionadas + necessidade de seleção de features.

---

## 2. ÁRVORES DE DECISÃO E ENSEMBLES

### 2.1 Decision Tree (DT)

**O que faz:** Particiona o espaço de features em regiões retangulares, criando regras do tipo "se X > valor, então...". Estrutura de fluxograma.

**Hiperparâmetros:**

| Parâmetro | Descrição | Valores Testados | Efeito |
|-----------|-----------|------------------|--------|
| **max_depth** | Profundidade máxima da árvore | [3, 5, 7, 10, None] | Limita complexidade; None = sem limite |
| **min_samples_split** | Mínimo de amostras para dividir nó | [2, 5, 10] | Evita divisões com poucos dados |
| **min_samples_leaf** | Mínimo de amostras em folha | [1, 2, 4] | Controla granularidade das folhas |
| **max_features** | Features consideradas por divisão | ['sqrt', 'log2', None] | Introduz aleatoriedade |

**Vantagens:** Interpretável, não assume distribuição, captura não-linearidades.

**Limitações:** Overfitting fácil, instável (pequenas mudanças nos dados → árvore muito diferente).

---

### 2.2 Random Forest (RF)

**O que faz:** Treina N árvores em paralelo, cada uma com subconjunto aleatório dos dados (bootstrap) e das features. Predição = média das árvores.

**Hiperparâmetros:**

| Parâmetro | Descrição | Valores Testados | Efeito |
|-----------|-----------|------------------|--------|
| **n_estimators** | Número de árvores | [50, 100, 200, 300] | Mais árvores = mais estável, mais custo |
| **max_depth** | Profundidade máxima | [3, 5, 7, 10, None] | Controla complexidade individual |
| **min_samples_split** | Mínimo para dividir | [2, 5, 10] | Regularização |
| **max_features** | Features por árvore | ['sqrt', 'log2'] | Diversidade entre árvores |
| **bootstrap** | Amostragem com reposição | [True, False] | True = bagging tradicional |

**Vantagens:** Robusto, reduz overfitting da DT única, importância de features.

**Limitações:** Menos interpretável que DT única, pode ser lento com muitas árvores.

---

### 2.3 Gradient Boosting (GB)

**O que faz:** Treina árvores sequencialmente. Cada nova árvore corrige os erros (resíduos) da combinação anterior.

**Fórmula:** Fₘ(x) = Fₘ₋₁(x) + ν·hₘ(x), onde ν = learning rate

**Hiperparâmetros:**

| Parâmetro | Descrição | Valores Testados | Efeito |
|-----------|-----------|------------------|--------|
| **n_estimators** | Número de árvores (estágios) | [50, 100, 200] | Mais estágios = mais capacidade, risco overfitting |
| **learning_rate (ν)** | Taxa de aprendizado | [0.01, 0.05, 0.1, 0.2] | Controla contribuição de cada árvore; ν↓ precisa mais árvores |
| **max_depth** | Profundidade de cada árvore | [3, 5, 7] | Árvores rasas (3-5) funcionam bem |
| **subsample** | Fração de dados por árvore | [0.8, 0.9, 1.0] | <1.0 introduz aleatoriedade (Stochastic GB) |
| **min_samples_split** | Mínimo para dividir nó | [2, 5, 10] | Regularização |

**Vantagens:** Estado da arte em dados tabulares, alta capacidade preditiva.

**Limitações:** Mais sensível a overfitting que RF, mais hiperparâmetros para ajustar.

---

## 3. REDES NEURAIS (MLP)

### 3.1 MLP (Multi-Layer Perceptron)

**O que faz:** Camadas de neurônios conectados. Cada neurônio: soma ponderada das entradas + ativação não linear. Aprende por backpropagation.

**Arquitetura:**
```
Entrada → [Camada Oculta 1] → [Camada Oculta 2] → ... → Saída
```

**Hiperparâmetros:**

| Parâmetro | Descrição | Valores Testados | Efeito |
|-----------|-----------|------------------|--------|
| **hidden_layer_sizes** | Neurônios por camada | [(64,), (128,), (256,), (128,64), (256,128), (256,128,64)] | Mais neurônios = mais capacidade; mais camadas = hierarquia |
| **activation** | Função de ativação | ['relu', 'tanh', 'logistic'] | ReLU: zera negativos; tanh: [-1,1]; logistic: [0,1] |
| **alpha (L2)** | Regularização L2 nos pesos | [0.0001, 0.001, 0.01, 0.1] | Penaliza pesos grandes, evita overfitting |
| **learning_rate_init** | Taxa de aprendizado inicial | [0.0001, 0.001, 0.01] | Tamanho do passo na descida do gradiente |
| **batch_size** | Tamanho do batch | [16, 32, 64, 'auto'] | Amostras por atualização de peso |
| **max_iter** | Máximo de épocas | [500, 1000, 2000] | Limite de iterações |
| **early_stopping** | Parada antecipada | [True, False] | Interrompe se validação não melhora |
| **validation_fraction** | Fração para validação | [0.1, 0.2] | Dados usados para early stopping |
| **n_iter_no_change** | Paciência do early stopping | [10, 20] | Épocas sem melhoria para parar |

**Funções de Ativação:**

| Função | Fórmula | Intervalo | Uso |
|--------|---------|-----------|-----|
| **ReLU** | max(0, x) | [0, ∞) | Padrão em redes profundas |
| **tanh** | (eˣ - e⁻ˣ)/(eˣ + e⁻ˣ) | (-1, 1) | Dados normalizados, gradientes mais suaves |
| **logistic (sigmoid)** | 1/(1 + e⁻ˣ) | (0, 1) | Saídas binárias |

---

## 4. ARQUITETURAS HÍBRIDAS

### 4.1 PhyInput (Hybrid Physics Data)

**Ideia:** Concatena predições do modelo físico como features extras.

**Arquitetura:**
```
Entrada: [X, Y_phy] → MLP → Ŷ
```

**Hiperparâmetros:** Mesmos da MLP baseline (L2 congelado).

---

### 4.2 PhyResidual (Residual)

**Ideia:** Aprende a correção do modelo físico.

**Arquitetura:**
```
Entrada: X → MLP → ε
Saída: Ŷ = Y_phy + ε
```

**Hiperparâmetros:**

| Parâmetro | Descrição | Valores | Efeito |
|-----------|-----------|---------|--------|
| **L2 (congelado)** | Regularização da baseline | Valor da MLP baseline | Isola efeito da arquitetura híbrida |

---

### 4.3 PhyHybrid

**Ideia:** Combina PhyInput + PhyResidual.

**Arquitetura:**
```
Entrada: [X, Y_phy] → MLP → ε
Saída: Ŷ = Y_phy + ε
```

---

### 4.4 PhyLoss

**Ideia:** Regularização física na função de perda.

**Função de Perda:**
```
Loss = (1-ω) · MSE_dados + ω · MSE_física
```

**Hiperparâmetro:**

| Parâmetro | Descrição | Valores Testados | Efeito |
|-----------|-----------|------------------|--------|
| **ω (omega)** | Peso da física na perda | [0.0, 0.1, 0.3, 0.5, 0.7] | ω=0: MLP pura; ω=1: apenas física; 0<ω<1: balanço |

---

## 5. HIPERPARÂMETROS DE VALIDAÇÃO

### 5.1 GroupKFold

| Parâmetro | Descrição | Valor |
|-----------|-----------|-------|
| **n_splits** | Número de folds | 3 (um por regime: 10, 40, 70 g/L) |
| **groups** | Variável de agrupamento | Regime de salinidade |

### 5.2 Critério 1-SE

| Parâmetro | Descrição |
|-----------|-----------|
| **SE (Standard Error)** | Desvio padrão do RMSE entre folds / √n_folds |
| **Regra** | Selecionar modelo mais simples com RMSE ≤ (melhor RMSE + 1 SE) |

---

## 6. RESUMO — BUSCA DE HIPERPARÂMETROS POR FAMÍLIA

| Família | Hiperparâmetros | Método |
|---------|-----------------|--------|
| **Ridge** | α | GridSearchCV |
| **Lasso** | α | GridSearchCV |
| **ElasticNet** | α, l1_ratio | GridSearchCV |
| **Decision Tree** | max_depth, min_samples_split, min_samples_leaf | GridSearchCV |
| **Random Forest** | n_estimators, max_depth, min_samples_split, max_features | GridSearchCV |
| **Gradient Boosting** | n_estimators, learning_rate, max_depth, subsample | GridSearchCV |
| **MLP** | hidden_layer_sizes, activation, α, learning_rate_init, batch_size | Random Search |
| **Híbridos** | L2 (congelado), ω (PhyLoss) | GridSearchCV (limitado) |

---

## 7. COMO EXPLICAR NA APRESENTAÇÃO

### Slide 13 — Modelos Lineares

**Fala:** "Os modelos lineares partem do OLS, que é a regressão clássica. O Ridge adiciona uma penalização L2 — apontar na figura — que encolhe os coeficientes sem zerá-los. O Lasso usa L1 — apontar — que pode zerar coeficientes, fazendo seleção automática de variáveis. O ElasticNet combina os dois."

**Tempo:** ~45 segundos

### Slide 14 — Árvores

**Fala:** "A Decision Tree faz perguntas binárias — apontar nó raiz e folhas. O Random Forest treina várias árvores em paralelo com amostras diferentes — apontar múltiplas árvores — e faz a média. O Gradient Boosting treina em sequência, cada uma corrigindo o erro da anterior — apontar setas sequenciais."

**Tempo:** ~45 segundos

### Slide 15 — Redes Neurais

**Fala:** "A MLP tem camadas de neurônios — apontar camadas. Cada neurônio faz uma soma ponderada seguida de ativação não linear — apontar função. O aprendizado ajusta os pesos por backpropagation. Os principais hiperparâmetros são: número de camadas e neurônios — apontar arquitetura —, taxa de aprendizado, e regularização L2."

**Tempo:** ~45 segundos

### Slide 16 — Híbridos

**Fala:** "As quatro arquiteturas híbridas incorporam o modelo físico de formas diferentes. O PhyInput adiciona a predição física como entrada — apontar seta do modelo 0D. O PhyResidual aprende a correção — apontar soma Y_phy + ε. O PhyHybrid combina as duas. O PhyLoss — apontar função de perda — penaliza desvios da física durante o treinamento."

**Tempo:** ~30 segundos
