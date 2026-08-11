# Roteiro Detalhado — Slides de Famílias de Modelos
## Slides 13-16: Todas as Variações de Modelos Utilizadas

---

## Estrutura deste Roteiro

| Slide | Tema | Variações | Tempo Base | Tempo Expandido |
|-------|------|-----------|------------|-----------------|
| 13 | Regressão Linear | OLS, Ridge, Lasso, ElasticNet | 45s | 1min 30s |
| 14 | Árvores de Decisão | DT, RF, GB | 45s | 1min 30s |
| 15 | Redes Neurais | MLP | 45s | 1min 30s |
| 16 | Arquiteturas Híbridas | PhyInput, PhyResidual, PhyHybrid, PhyLoss | 30s | 1min 30s |
| **Total** | | **12 variações** | **~3min** | **~6min** |

---

# SLIDE 13 — Famílias de Modelos I: Regressão Linear e Regularizadas

## Texto do Slide
> Figura com 4 painéis: OLS, Ridge, Lasso, ElasticNet

## Fala Base (45s)
"Lineares: OLS sem regularização, Ridge penaliza L2 — encolhe coeficientes, Lasso penaliza L1 — zera coeficientes, seleção de variáveis —, ElasticNet combina ambos."

---

## Fala Expandida (1min 30s)

"Começando pelos **modelos lineares**. Todos partem da mesma ideia: encontrar os coeficientes β que minimizam o erro entre o valor real e o predito.

**OLS — Ordinary Least Squares** — *apontar o primeiro painel*
É a regressão linear clássica. Minimiza a soma dos quadrados dos resíduos: Σ(yᵢ - ŷᵢ)². Não tem nenhuma restrição — qualquer ruído nos dados vira inclinação na reta. É o modelo mais simples, mas pode superajustar quando há muitas variáveis.

**Ridge** — *apontar o segundo painel, destacar o termo λΣβ²*
Adiciona uma penalização **L2** — a soma dos quadrados dos coeficientes. O hiperparâmetro **alpha (α)** controla a força: α=0 volta ao OLS; α alto encolhe todos os coeficientes em direção a zero, sem zerá-los. Útil quando há multicolinearidade.

**Lasso** — *apontar o terceiro painel, destacar λΣ|β|*
Usa penalização **L1** — a soma dos valores absolutos. A geometria do L1 faz com que coeficientes de variáveis irrelevantes sejam **exatamente zero** — é seleção automática de features.

**ElasticNet** — *apontar o quarto painel, mostrar os dois termos*
Combina L1 + L2. O hiperparâmetro **l1_ratio (ρ)** controla a mistura: ρ=1 é Lasso puro, ρ=0 é Ridge puro. Herda a seleção do Lasso e a estabilidade do Ridge."

---

## Detalhamento Técnico por Modelo

| Modelo | Função de Custo | Hiperparâmetros | Valores Testados | Quando Usar |
|--------|-----------------|-----------------|------------------|-------------|
| **OLS** | Σ(yᵢ - ŷᵢ)² | — | — | Baseline, poucas variáveis |
| **Ridge** | Σ(yᵢ - ŷᵢ)² + α·Σβⱼ² | α | [0.001, 0.01, 0.1, 1, 10, 100] | Multicolinearidade |
| **Lasso** | Σ(yᵢ - ŷᵢ)² + α·Σ\|βⱼ\| | α | [0.001, 0.01, 0.1, 1, 10, 100] | Seleção de features |
| **ElasticNet** | Σ(yᵢ - ŷᵢ)² + α·ρ·Σ\|βⱼ\| + α·(1-ρ)/2·Σβⱼ² | α, l1_ratio | α: [0.001-10], ρ: [0.1-0.9] | Features correlacionadas + seleção |

---

## Intuição Geométrica

- **L2 (Ridge):** Região de restrição circular — coeficientes encolhem suavemente
- **L1 (Lasso):** Região de restrição em losango — coeficientes podem zerar nos vértices

---

# SLIDE 14 — Famílias de Modelos II: Árvores de Decisão

## Texto do Slide
> Figura com 3 painéis: Decision Tree, Random Forest, Gradient Boosting

## Fala Base (45s)
"Árvores: DT overfitta, RF reduz variância com bagging, GB corrige resíduos sequencialmente."

---

## Fala Expandida (1min 30s)

"**Árvores de decisão** são modelos não lineares que particionam o espaço em regiões.

**Decision Tree** — *apontar o primeiro painel, a estrutura de fluxograma*
Faz perguntas binárias recursivas: 'se temperatura > 70°C, vai para a esquerda...'. Cada nó — *apontar* — é uma pergunta, cada folha — *apontar* — é uma predição. O problema: se deixar crescer sem limite, ela **decora** os dados de treino — overfitting puro.

**Random Forest** — *apontar o segundo painel, as múltiplas árvores*
Resolve o overfitting da DT treinando **N árvores em paralelo** — *apontar as setas do bootstrap*. Cada árvore vê: (1) um subconjunto aleatório dos dados — bootstrap —, (2) um subconjunto aleatório das features. A predição final é a **média** de todas. Isso cancela os erros individuais — reduz a variância.

**Gradient Boosting** — *apontar o terceiro painel, a sequência*
Trabalha **em sequência**, não em paralelo. A primeira árvore faz uma predição ruim. A segunda aprende os **resíduos** — os erros — da primeira. A terceira corrige a combinação das duas... O **learning rate** controla quanto cada árvore contribui: taxa baixa precisa de mais árvores, mas generaliza melhor."

---

## Detalhamento Técnico por Modelo

### Decision Tree

| Hiperparâmetro | Descrição | Valores Testados | Efeito |
|---------------|-----------|------------------|--------|
| `max_depth` | Profundidade máxima | [3, 5, 7, 10, None] | Limita complexidade |
| `min_samples_split` | Mínimo para dividir nó | [2, 5, 10] | Evita divisões espúrias |
| `min_samples_leaf` | Mínimo em folha | [1, 2, 4] | Controla granularidade |

### Random Forest

| Hiperparâmetro | Descrição | Valores Testados | Efeito |
|---------------|-----------|------------------|--------|
| `n_estimators` | Número de árvores | [50, 100, 200, 300] | Mais árvores = mais estável |
| `max_depth` | Profundidade de cada árvore | [3, 5, 7, 10] | Complexidade individual |
| `max_features` | Features por divisão | ['sqrt', 'log2'] | Diversidade entre árvores |

### Gradient Boosting

| Hiperparâmetro | Descrição | Valores Testados | Efeito |
|---------------|-----------|------------------|--------|
| `n_estimators` | Estágios de boosting | [50, 100, 200] | Mais estágios = mais capacidade |
| `learning_rate` | Taxa de aprendizado | [0.01, 0.05, 0.1, 0.2] | Contribuição de cada árvore |
| `max_depth` | Profundidade | [3, 5, 7] | Árvores rasas funcionam melhor |
| `subsample` | Fração de dados por árvore | [0.8, 0.9, 1.0] | <1.0 = Stochastic GB |

---

## Bagging vs Boosting

| | Bagging (RF) | Boosting (GB) |
|---|---|---|
| **Treinamento** | Paralelo | Sequencial |
| **Objetivo** | Reduzir variância | Reduzir viés |
| **Independência** | Árvores independentes | Árvores dependentes |
| **Peso** | Todas iguais | Ponderada pelo erro |

---

# SLIDE 15 — Famílias de Modelos III: Redes Neurais

## Texto do Slide
> Figura: arquitetura MLP com camadas, neurônios, pesos, ativação

## Fala Base (45s)
"MLP: fully connected, backpropagation, ativação não linear. Hiperparâmetros: camadas, neurônios, ativação, lr, L2, dropout."

---

## Fala Expandida (1min 30s)

"A **MLP** — Multi-Layer Perceptron — é uma rede neural artificial.

**Estrutura** — *apontar cada elemento na figura*:
- **Camada de entrada** — *apontar* — recebe as 5 variáveis operacionais
- **Camadas ocultas** — *apontar* — processam a informação
- **Camada de saída** — *apontar* — produz as 3 predições

**Neurônio individual** — *apontar um círculo*:
Faz duas operações: (1) soma ponderada das entradas — *apontar os pesos w* —, (2) aplica **função de ativação** não linear — *apontar a curva*.

**Ativações que testei**:
- **ReLU** — *apontar* — zera valores negativos. Simples, rápida, padrão em redes profundas.
- **tanh** — *apontar* — comprime entre -1 e 1. Adequada para dados normalizados pelo Z-score.
- **logistic/sigmoid** — *apontar* — comprime entre 0 e 1.

**Aprendizado** — *apontar as setas de ida e volta*:
Backpropagation: calcula o erro na saída, propaga o gradiente para trás, ajusta os pesos na direção que reduz o erro. O **learning rate** controla o tamanho do passo."

---

## Detalhamento Técnico — Hiperparâmetros MLP

| Hiperparâmetro | Descrição | Valores Testados | Efeito Prático |
|---------------|-----------|------------------|----------------|
| `hidden_layer_sizes` | Neurônios por camada | (64,), (128,), (256,), (128,64), (256,128), (256,128,64) | Mais neurônios = mais capacidade |
| `activation` | Função de ativação | relu, tanh, logistic | ReLU: rápida; tanh: gradientes suaves |
| `alpha` | Regularização L2 nos pesos | 0.0001, 0.001, 0.01, 0.1 | Penaliza pesos grandes |
| `learning_rate_init` | Taxa de aprendizado | 0.0001, 0.001, 0.01 | Muito alto: diverge; baixo: lento |
| `batch_size` | Amostras por atualização | 16, 32, 64 | Menor: mais ruidoso |
| `max_iter` | Máximo de épocas | 500, 1000, 2000 | Com early stopping, raramente atinge |
| `early_stopping` | Parada antecipada | True | Interrompe se não melhora |
| `validation_fraction` | Dados para validação | 0.1, 0.2 | Usado pelo early stopping |
| `n_iter_no_change` | Paciência | 10, 20 | Épocas sem melhoria para parar |

---

## Arquiteturas Testadas

| Arquitetura | Camadas | Neurônios | Parâmetros Aprox. | Resultado |
|-------------|---------|-----------|-------------------|-----------|
| `(64,)` | 1 | 64 | ~400 | Simples demais |
| `(128,)` | 1 | 128 | ~800 | Intermediário |
| `(256,)` | 1 | 256 | ~1.600 | **Baseline selecionada** |
| `(128, 64)` | 2 | 192 | ~10.000 | Mais profunda |
| `(256, 128)` | 2 | 384 | ~35.000 | Complexa |
| `(256, 128, 64)` | 3 | 448 | ~45.000 | Mais complexa |

---

## Funções de Ativação

| Função | Fórmula | Intervalo | Vantagem | Desvantagem |
|--------|---------|-----------|----------|-------------|
| **ReLU** | max(0, x) | [0, ∞) | Simples, rápida | Neurônios "morrem" |
| **tanh** | (eˣ - e⁻ˣ)/(eˣ + e⁻ˣ) | (-1, 1) | Gradientes suaves | Saturação |
| **logistic** | 1/(1 + e⁻ˣ) | (0, 1) | Interpretável | Saturação, não centrada |

---

# SLIDE 16 — Famílias de Modelos IV: Arquiteturas Híbridas

## Texto do Slide
> Figura com 4 painéis: PhyInput, PhyResidual, PhyHybrid, PhyLoss

## Fala Base (30s)
"Híbridos: quatro arquiteturas que incorporam o modelo físico 0D."

---

## Fala Expandida (1min 30s)

"As **arquiteturas híbridas** combinam o modelo físico 0D com redes neurais. São quatro formas diferentes de fazer essa incorporação.

**PhyInput** — *apontar o primeiro painel*
Simplesmente adiciona as predições do modelo 0D como **features extras** de entrada. O vetor de entrada vira [X, Y_phy]. A rede pode usar a física se for útil, ou aprender a ignorá-la se não for.

**PhyResidual** — *apontar o segundo painel, destacar a soma Y_phy + ε*
Aprende apenas o **resíduo** — o desvio entre o físico e o real. A saída é Y = Y_phy + ε. A rede não precisa aprender o comportamento inteiro do zero — só a correção. É análogo ao ResNet, mas a referência é um modelo físico externo, não uma camada anterior.

**PhyHybrid** — *apontar o terceiro painel*
Combina as duas estratégias: recebe [X, Y_phy] como entrada **E** produz uma correção residual que é somada à física: Y = Y_phy + f(X, Y_phy). É a mais flexível, mas com mais parâmetros — risco de overfitting com 174 amostras.

**PhyLoss** — *apontar o quarto painel, a função de perda*
Não altera a arquitetura. Modifica a **função de perda**: Loss = (1-ω)·Loss_dados + ω·Loss_física. O hiperparâmetro **ω (omega)** controla o compromisso: ω=0 é MLP pura, ω=1 é apenas física."

---

## Detalhamento Técnico — Arquiteturas Híbridas

| Arquitetura | Entrada | Saída | Função de Perda | Hiperparâmetro |
|-------------|---------|-------|-----------------|----------------|
| **PhyInput** | [X, Y_phy] | ŷ = f(X, Y_phy) | MSE(ŷ, y) | L2 (congelado) |
| **PhyResidual** | X | ŷ = Y_phy + f(X) | MSE(ŷ, y) | L2 (congelado) |
| **PhyHybrid** | [X, Y_phy] | ŷ = Y_phy + f(X, Y_phy) | MSE(ŷ, y) | L2 (congelado) |
| **PhyLoss** | X | ŷ = f(X) | (1-ω)·MSE(ŷ,y) + ω·MSE(ŷ, Y_phy) | ω: [0.0, 0.1, 0.3, 0.5, 0.7] |

---

## Estratégia de Busca nos Híbridos

**L2 congelado:** O valor de L2 foi fixado da baseline (Stage 1) para isolar o efeito da arquitetura híbrida.

**Baseline compartilhada:** Todas usam a mesma arquitetura da baseline Alim:
- `hidden_layer_sizes=(256,)`
- `activation='logistic'`
- L2 da baseline

**Ômega (ω) testado:** [0.0, 0.1, 0.3, 0.5, 0.7]
- ω=0: MLP pura (sem física)
- ω=0.3: balanço dados/física
- ω=1: apenas física

---

## Analogia com ResNet

O **PhyResidual** é conceitualmente idêntico ao **ResNet** (He et al., 2015):

| ResNet | PhyResidual |
|--------|-------------|
| Saída da camada anterior como referência | Modelo físico 0D como referência |
| Aprende F(x) = H(x) - x | Aprende ε = Y - Y_phy |
| Skip connection interna | Skip connection externa (física) |

---

# CHECKLIST — O QUE APONTAR EM CADA SLIDE

## Slide 13 (Regressão)
- [ ] Painel OLS: "sem regularização"
- [ ] Painel Ridge: termo λΣβ² na fórmula
- [ ] Painel Lasso: termo λΣ|β| na fórmula
- [ ] Painel ElasticNet: os dois termos juntos

## Slide 14 (Árvores)
- [ ] DT: nó raiz e folhas
- [ ] RF: múltiplas árvores + setas do bootstrap
- [ ] GB: sequência de árvores + setas de correção de resíduos

## Slide 15 (Redes Neurais)
- [ ] Camada de entrada (5 neurônios)
- [ ] Camadas ocultas
- [ ] Camada de saída (3 neurônios)
- [ ] Pesos (conexões)
- [ ] Função de ativação
- [ ] Setas de backpropagation

## Slide 16 (Híbridos)
- [ ] PhyInput: seta do modelo 0D entrando como feature
- [ ] PhyResidual: soma Y_phy + ε
- [ ] PhyHybrid: entrada expandida + soma residual
- [ ] PhyLoss: função de perda com os dois termos

---

# RESUMO — TODAS AS VARIAÇÕES TESTADAS

## Modelos Lineares (4 variações)
1. **OLS** — sem regularização
2. **Ridge** — L2
3. **Lasso** — L1
4. **ElasticNet** — L1 + L2

## Árvores (3 variações)
5. **Decision Tree** — árvore única
6. **Random Forest** — bagging (paralelo)
7. **Gradient Boosting** — boosting (sequencial)

## Redes Neurais (6 arquiteturas × 3 ativações)
8-13. **MLP** com arquiteturas: (64,), (128,), (256,), (128,64), (256,128), (256,128,64)

## Híbridos (4 arquiteturas)
14. **PhyInput** — física como feature
15. **PhyResidual** — aprende resíduo
16. **PhyHybrid** — feature + resíduo
17. **PhyLoss** — física na função de perda

---

**Total: 17 configurações de modelos testadas**
