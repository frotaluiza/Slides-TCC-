# Roteiro Consolidado — Apresentação TCC V-AGMD
## Versão Final — Alterações da Orientadora (30/07/26) Incorporadas

---

## SLIDE 1 — Título

Boa tarde. Este é o meu projeto final de graduação, cujo título é **"Modelagem Híbrida com Regularização Física e Seleção de Modelos para Predição de Desempenho em Destilação por Membranas"**.

---

## SLIDE 2 — Sumário

Este é o sumário do TCC: vamos começar com a **introdução**, depois **revisão bibliográfica**, **fundamentação teórica**, **metodologia proposta**, seguindo para **resultados**, **conclusões** e **referências**.

---

## SLIDE 3 — A Crise Global da Água

A crise global da água é tanto de quantidade quanto de qualidade. **4 bilhões** de pessoas enfrentam escassez severa de água, sendo que **2,2 bilhões** não têm acesso a água potável segura. A demanda global deve superar a oferta em **40% até 2030**.

> **Fontes:** WHO (2023), IDRA (2026), Mekonnen & Hoekstra (2016)

---

## SLIDE 4 — O Problema no Brasil

No Brasil, 2026 foi um ano desafiador, com chuvas abaixo da média. O **Sistema Cantareira** operou a aproximadamente **30%** da sua capacidade. No Nordeste, um cenário de **4 meses de chuva para 8 meses de seca extrema**.

A dessalinização pode reduzir o custo da água em até **10 vezes** — de R$ 2,63 a R$ 4,21/m³, segundo a **Confederação Nacional da Indústria (CNI)**. Para referência, tarifas industriais no RJ chegam a R$ 43,29/m³. A maior planta do Brasil (ES) atende **80 mil pessoas**. Com **8.500 km de costa**, o potencial de expansão é enorme.

> **ALTERAÇÃO IMPLEMENTADA:** Dados referenciados como CNI (fonte oficial), não apenas "notícias".  
> **Fontes:** ANA/CNI (2026), IBGE

---

## SLIDE 5 — Dessalinização: Contexto Global

A dessalinização já é uma realidade consolidada globalmente. Mais de **150 países** usam a tecnologia. Na Arábia Saudita, responde por **86%** do abastecimento; em Israel, **80%**.

> **Fontes:** Banco Mundial, IDA Desalination Yearbook

---

## SLIDE 6 — V-AGMD no Contexto da Dessalinização

A dessalinização divide-se em duas grandes famílias: processos **térmicos** (destilação convencional) e processos de **membrana** (osmose inversa, MD). A **Destilação por Membrana (MD)** é um processo híbrido termo-membrana: uma membrana hidrofóbica separa o vapor d'água da salmoura aquecida.

A configuração **V-AGMD** combina um **espaço de ar** (que funciona como isolante térmico) com **vácuo parcial**. O vácuo parcial reduz a **resistência à transferência de massa do vapor** em relação à operação atmosférica, compensando o impedimento causado pelo air gap.

> **ALTERAÇÃO IMPLEMENTADA:** "vácuo parcial reduz a resistência à transferência de massa do vapor" — não "vácuo de ar".  
> **Fontes:** Cath et al. (2010), Warsinger et al. (2017)

---

## SLIDE 7 — Ilha de Policogeração Sustentável

Este trabalho está inserido no projeto **CT2 — Ilha de Policogeração Sustentável**, do LabMEMS, COPPE/UFRJ, inaugurado em 2022. É um protótipo pioneiro que une **geração de água potável** com **energia solar térmica**.

O sistema produz cerca de **5 kWₑ** — suficiente para aproximadamente **25 residências** — e mais **8 kWₜ** recuperáveis em micro-trocadores. O dessalinizador V-AGMD produz **1.000 L/dia** de água destilada, para **mais de 100 pessoas/dia**.

O foco são **comunidades remotas** do Semiárido nordestino, em articulação com o **Projeto Água Doce**.

---

## SLIDE 8 — Imagem da Instalação

*(Slide apenas para mostrar a instalação física do protótipo V-AGMD na Ilha de Policogeração)*

> **Ação:** Apontar visualmente onde os dados foram coletados.

---

## SLIDE 9 — Motivação e Objetivos

A motivação é a necessidade de **prever o desempenho** desse protótipo V-AGMD para otimizar sua operação em comunidades remotas. Temos **dados experimentais** de aproximadamente **174 pontos** em **3 regimes de salinidade**.

Já existe um **modelo físico de 0 dimensões** disponível na literatura (Lisboa et al., 2024), que serviu de referência física para este trabalho.

O **objetivo geral** é avaliar estratégias de modelagem — de regressões lineares a arquiteturas híbridas — para prever o desempenho do V-AGMD.

> **ALTERAÇÃO IMPLEMENTADA:** Motivação agora é o que você apresenta (necessidade de prever desempenho), não uma justificativa externa.

---

## SLIDE 10 — Revisão Bibliográfica: Abordagens de Modelagem

Existem **três principais abordagens** de modelagem em destilação por membranas:

1. **Abordagem física:** usa princípios e leis físicas para modelar o sistema. Inclui modelos distribuídos (1D, 2D) e modelos reduzidos 0D.

2. **Abordagem data-driven:** usa apenas dados experimentais para aprender a função que mapeia entradas e saídas.

3. **Abordagens híbridas:** combinam conhecimento físico com aprendizado de máquina, usando a física como regularizador para restringir o espaço de busca e melhorar a generalização com poucos dados.

> **ALTERAÇÃO IMPLEMENTADA:** Deixar claro que existem modelos com dados em outras configurações (V-AGMD, PGMD), não apenas "modelos de dados".

---

## SLIDE 11 — Panorama de Publicações

Neste panorama, encontrei aproximadamente **4 publicações** usando abordagem física para V-AGMD/AGMD. A abordagem **data-driven** foi mais comum: redes neurais, regressões lineares, árvores de decisão.

Especificamente em V-AGMD com air gap, abordagens **híbridas** encontrei **uma** — uma PINN aplicada a dessalinização (mas para osmose reversa, não MD).

> **PENDENTE:** Confirmar referência do artigo PINN com a orientadora.

---

## SLIDE 12 — Lacunas Identificadas

**Lacunas na literatura:**

1. **Ausência de validação cruzada** — a maioria usa partição única, ignorando a estrutura dos grupos experimentais
2. **Seleção por métrica absoluta** — baseada apenas em RMSE, sem considerar a variabilidade estatística
3. **Híbridos praticamente inexistentes** em V-AGMD com air gap

> **ALTERAÇÃO IMPLEMENTADA:** Este slide foca APENAS nas lacunas (contribuições vão para o próximo slide).

---

## SLIDE 13 — Contribuições deste Trabalho

**Contribuições:**

1. **Validação cruzada estruturada** por regime de salinidade (GroupKFold)
2. **Critério de seleção 1-SE** — favorece modelos menos complexos dentro da margem estatística
3. **Experimentação inédita** de 4 arquiteturas híbridas no V-AGMD

> **ALTERAÇÃO IMPLEMENTADA:** Contribuições agora em slide separado, eliminando redundância com o slide 12.

---

## SLIDE 14 — Sumário da Apresentação

A apresentação está dividida em **5 blocos**. Vamos agora para a **fundamentação teórica**.

---

## SLIDE 15 — Princípios da Destilação por Membranas

A destilação por membranas é um processo térmico de separação. A água salgada é aquecida e circula por um lado de uma **membrana hidrofóbica porosa** — ela não permite a passagem de líquido, mas o vapor consegue atravessar os poros.

A força motriz é a **diferença de temperatura**: do lado quente a água evapora, o vapor migra pelos poros e condensa do lado frio.

**Vantagens do processo MD:**
- Opera em **temperaturas médias** (60-80°C)
- Compatível com **calor residual** e **cogeração**
- **Alta tolerância à salinidade** — não limitada por pressão osmótica como a osmose inversa

> **ALTERAÇÕES IMPLEMENTADAS:**
> - "Filtrar" → "membrana hidrofóbica porosa"
> - "Vácuo de ar" → "vácuo parcial"
> - Vantagens agora explicitamente atribuídas ao **processo MD**, não à configuração V-AGMD específica

---

## SLIDE 16 — Configuração V-AGMD

A configuração **V-AGMD** adiciona duas modificações à MD convencional:

1. **Espaço de ar (Air Gap):** funciona como **isolante térmico**, reduzindo perdas de calor entre os lados quente e frio

2. **Vácuo parcial:** aplicado no espaço de ar para **reduzir a resistência ao transporte de vapor**, compensando o impedimento causado pelo ar

> **TEMPO:** Reduzir para ~2 minutos (não gastar 5 min aqui)

---

## SLIDE 17 — Modelo Físico: Três Níveis

É importante distinguir **três níveis** de modelos físicos:

| Nível | Descrição | Custo |
|-----|-----------|-------|
| **Distribuídos** (1D, 2D) | Discretizam o módulo, resolvem equações em cada ponto | Alto |
| **Balanços globais** | Estado estacionário, sem discretização | Médio |
| **Reduzidos 0D** | Volume único, grandezas médias | Baixo |

O modelo **0D de Lisboa (2024)** é usado neste trabalho como referência física.

> **ALTERAÇÃO IMPLEMENTADA:** Falar claramente o que cada nível faz, sem gastar tempo excessivo.

---

## SLIDE 18 — Fundamentos de Machine Learning

O aprendizado de máquina busca **aproximar Y ≈ f(X)** minimizando o erro.

**Métricas:**
- **RMSE:** raiz do erro quadrático médio
- **R²:** coeficiente de determinação (pode ser negativo quando o modelo é pior que a média)

**Pré-processamento — Z-score:** transforma cada variável subtraindo sua média e dividindo pelo desvio padrão, colocando todas na mesma escala.

> **ALTERAÇÃO IMPLEMENTADA:** Quando falar de L1/L2 (regularização), apontar explicitamente na figura/diagrama o que está sendo referenciado.

---

## SLIDE 19 — Famílias de Modelos

**Quatro famílias** foram comparadas:

1. **Lineares:** OLS, Ridge (L2), Lasso (L1), ElasticNet (L1+L2)
2. **Árvores:** Decision Tree, Random Forest, Gradient Boosting
3. **Redes Neurais (MLPs):** camadas fully connected com ativação não linear
4. **Híbridas:** PhyInput, PhyResidual, PhyHybrid, PhyLoss

> **Ação:** Apontar cada família no diagrama enquanto fala.

---

## SLIDE 20 — Visão Geral dos Procedimentos

Começo com os **dados experimentais**, preparação (padronização, análise de correlações). A modelagem segue **3 estágios**: Stage 0 (clássicos), Stage 1 (redes neurais), Stage 2 (híbridos). Finalmente, o modelo selecionado é comparado com o **modelo 0D**.

---

## SLIDE 21 — Dados Experimentais

**Fonte dos dados:** Campanha experimental do LabMEMS/COPPE (Lisboa et al., 2024)

- **174 pontos**, **3 regimes de salinidade** (10, 40, 70 g/L)
- **5 entradas:** temperatura alimentação, temperatura refrigeração, vazão refrigeração, pressão vácuo, concentração salina
- **3 saídas:** fluxo permeado, temperatura saída alimentação, temperatura saída refrigeração

> **ALTERAÇÃO IMPLEMENTADA:** Citada a fonte dos dados explicitamente.

---

## SLIDE 22 — Decisões da Preparação dos Dados

- **Escalonamento:** Z-score (preserva distribuição, mede em desvios-padrão)
- **Validação:** GroupKFold (separa folds por regime operacional)

---

## SLIDE 23 — Fluxo de Validação Cruzada e Seleção

**GroupKFold** → RMSE médio com erro padrão → **regra 1-SE** → modelo de menor complexidade

---

## SLIDE 24 — Busca de Hiperparâmetros

Busca personalizada por target — **3 fits independentes** por alvo.

| Família | Hiperparâmetros buscados |
|---------|-------------------------|
| Lineares | alpha (Ridge/Lasso/ElasticNet), l1_ratio |
| Árvores | profundidade, n_estimadores, learning_rate |
| Redes | camadas, neurônios, LR, L2, ativação |
| Híbridos | L2 congelado (da baseline), ω (PhyLoss) |

---

## SLIDE 25 — Esquema das Arquiteturas Híbridas

*(Figura mostrando as 4 arquiteturas: PhyInput, PhyResidual, PhyHybrid, PhyLoss)*

> **ALTERAÇÕES IMPLEMENTADAS:**
> - Colocar **legenda das cores**: Linear (azul), Rede Neural (verde), Híbrido (laranja)
> - Não explicar detalhadamente a figura — apenas mostrar o que foi feito

---

## SLIDE 26 — Resultados: Modelos Lineares e Árvores

Tabelas de resultados para modelos lineares e árvores de decisão.

> **ALTERAÇÃO IMPLEMENTADA:** Manter apenas tabelas que serão efetivamente discutidas. Remover tabelas intermediárias não essenciais.

---

## SLIDE 27 — Resultados: Redes Neurais e Seleção

*(Tabela consolidada com os 3 targets e modelos selecionados)*

> **ALTERAÇÃO IMPLEMENTADA:** Reunir em um único slide o que é importante — evitar vai e volta de slides.

---

## SLIDE 28 — Comparação com Modelo 0D

O **modelo físico 0D** (Lisboa et al., 2024) captura tendências mas apresenta dispersão significativa, especialmente para as temperaturas.

> **ALTERAÇÃO IMPLEMENTADA:** Citado explicitamente que o modelo 0D é de Lisboa et al. (2024), não é trabalho seu.

---

## SLIDE 29 — Resultados por Variável de Saída

| Target | Modelo Selecionado | Test RMSE | Observação |
|--------|-------------------|-----------|------------|
| **T_alim_out** | Baseline Flux (Stage 1) | 0,178 | 2,7% melhor que PhyResidual |
| **T_ref_out** | PhyResidual (base Flux) | 0,214 | Marginal sobre Ridge (2,3%) |
| **Fluxo** | PhyResidual (base Flux) | 0,054 | **73,8% melhor que modelo 0D** |

> **ALTERAÇÃO IMPLEMENTADA:** Discussão do modelo 0D mais cuidadosa — não criticar, mas mostrar que a hibridização corrige limitações do modelo simplificado.

---

## SLIDE 30 — Gráficos de Desempenho

*(Gráficos de dispersão: experimental vs. predito para os 3 targets)*

> **ALTERAÇÃO IMPLEMENTADA:** Adicionar gráficos que mostrem visualmente o que está sendo discutido (não apenas texto).

---

## SLIDE 31 — Discussão: O que a Hibridização Corrige

O ganho dos híbridos não é capturar relações não lineares — a região é aproximadamente linear. O ganho é **corrigir o viés** dos modelos data-driven usando a física como referência.

O **R² negativo** do modelo 0D para temperaturas indica que ele tem viés sistemático que as arquiteturas híbridas conseguem corrigir.

> **ALTERAÇÃO IMPLEMENTADA:** Referência ao R² negativo marcada como "extensa" (ver documentação scikit-learn).

---

## SLIDE 32 — Comparação Final

| | T_alim_out | T_ref_out | Fluxo |
|---|---|---|---|
| **Modelo 0D** | 1,613 | — | 0,206 |
| **Melhor Data-Driven** | 0,178 | 0,219 | 0,066 |
| **Melhor Híbrido** | 0,183 | 0,214 | **0,054** |
| **Selecionado** | Baseline Flux | PhyResidual | **PhyResidual** |

---

## SLIDE 33 — Conclusões

**Conclusões principais:**

1. **PhyResidual (base Flux)** selecionado para **Fluxo** (73,8% melhor que modelo 0D) e **T_ref_out**
2. **Baseline Flux** selecionado para **T_alim_out**
3. O critério **1-SE** com validação por grupos permitiu seleção parcimoniosa de modelos
4. A hibridização física-dados mostrou-se mais efetiva para variáveis com maior complexidade (fluxo)

---

## SLIDE 34 — Trabalhos Futuros

1. **Substituir modelo 0D pelo modelo 2D** como referência física
2. **Construir PINNs** a partir das EDOs do modelo 2D:
   - Modo surrogate (apenas física)
   - Modo híbrido (física + dados na função de perda)

---

## SLIDE 35 — Referências Bibliográficas

*(Lista de referências completa)*

---

## Notas de Tempo

| Seção | Slides | Tempo Estimado |
|-------|--------|----------------|
| Introdução | 1-9 | ~9 min |
| Revisão | 10-13 | ~4 min |
| Fundamentação | 14-19 | ~6 min |
| Metodologia | 20-25 | ~6 min |
| Resultados | 26-32 | ~7 min |
| Conclusões | 33-35 | ~3 min |
| **Total** | | **~35 min** |
