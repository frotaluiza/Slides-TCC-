# Roteiro Consolidado — Apresentação TCC V-AGMD

---

## Abrir / Slide de Título

Boa tarde. Este é o meu projeto final de graduação, cujo título é **"Modelagem Híbrida com Regularização Física e Seleção de Modelos para Predição de Desempenho em Destilação por Membranas"**.

---

## Sumário

Este é o sumário do TCC: vamos começar com a **introdução**, depois **revisão bibliográfica**, **fundamentação teórica**, **metodologia proposta**, seguindo para **resultados**, **conclusões** e **referências**.

---

## 1. A Crise Global da Água

A crise global da água é tanto de quantidade quanto de qualidade. **4 bilhões** de pessoas enfrentam escassez severa de água, sendo que **2,2 bilhões** não têm acesso a água potável segura. A demanda global deve superar a oferta em **40% até 2030**.

---

## 2. O Problema no Brasil

No Brasil, 2026 foi um ano desafiador, com chuvas abaixo da média. O **Sistema Cantareira** operou a aproximadamente **30%** da sua capacidade. No Nordeste, um cenário de **4 meses de chuva para 8 meses de seca extrema**.

A dessalinização pode reduzir o custo da água em até **10 vezes** — de R$ 2,63 a R$ 4,21/m³, segundo a Confederação Nacional da Indústria (CNI). Para referência, tarifas industriais no RJ chegam a R$ 43,29/m³. O ganho vem do fato de a indústria deixar de depender da concessionária e tratar a água bruta por conta própria. A maior planta do Brasil (ES) atende **80 mil pessoas**. Com **8.500 km de costa**, o potencial de expansão é enorme.

---

## 3. Dessalinização — Contexto Global

A dessalinização já é uma realidade consolidada globalmente. Mais de **150 países** usam a tecnologia. Na Arábia Saudita, responde por **86%** do abastecimento; em Israel, **80%**.

---

## 4. V-AGMD no Contexto da Dessalinização

Nesse sentido, este trabalho estuda uma configuração específica de tecnologia de dessalinização, que se divide em duas grandes famílias: processos **térmicos** (destilação convencional) e processos de **membrana** (osmose inversa, MD). A **Destilação por Membrana (MD)** é um processo híbrido termo-membrana: uma membrana hidrofóbica separa o vapor d'água da salmoura aquecida.

A configuração **V-AGMD** combina um **espaço de ar** (que funciona como isolante térmico) com **vácuo parcial** (que reduz a resistência ao transporte de vapor). O ar impede a troca de calor entre os lados quente e frio, tornando o sistema energeticamente eficiente. O vácuo compensa o impedimento ao transporte de massa causado pelo air gap. É uma tecnologia particularmente adequada para águas de alta salinidade, pois — diferentemente da osmose inversa — não é limitada pelo aumento da pressão osmótica.

---

## 5. Ilha de Policogeração Sustentável

Este trabalho está inserido no projeto **CT2 — Ilha de Policogeração Sustentável**, do LabMEMS, COPPE/UFRJ, inaugurado em 2022. É um protótipo pioneiro que une **geração de água potável** com **energia solar térmica**.

O sistema produz cerca de **5 kWₑ** — suficiente para aproximadamente **25 residências** — e mais **8 kWₜ** recuperáveis em micro-trocadores. O dessalinizador V-AGMD produz **1.000 L/dia** de água destilada, o que pode prover água para **mais de 100 pessoas/dia**.

O foco são **comunidades remotas** do Semiárido nordestino, em articulação com o **Projeto Água Doce** — programa do governo federal que expande acesso à água potável no Semiárido nordestino por meio de dessalinização, atendendo comunidades remotas não cobertas pelo sistema tradicional de abastecimento.

---

## 6. Imagem da Instalação

(Slide apenas para mostrar a instalação física do protótipo V-AGMD na Ilha de Policogeração, do artigo de Naveira-Cotta et al.)

---

## 7. Motivação e Objetivos

Prever o desempenho do módulo V-AGMD é importante por dois motivos principais: permite **avaliar a produção de água dessalinizada** (fluxo de permeado) e **estimar indicadores energéticos** associados ao processo (temperaturas de saída). Ter um modelo confiável ajuda a simular e otimizar a operação, projetar sistemas mais eficientes e tomar decisões sem depender exclusivamente de medições experimentais contínuas.

Temos **dados experimentais** de aproximadamente **174 pontos** em **3 regimes de salinidade**. Além disso, já existe um **modelo físico reduzido 0D** disponível na literatura, publicado pelo laboratório (LISBOA et al., 2024), que serve como referência para o sistema.

O **objetivo geral** é avaliar e selecionar modelos de regressão supervisionada para predição do desempenho do V-AGMD, combinando aprendizado a partir de dados com a informação física proveniente do modelo reduzido.

---

## 8. Revisão Bibliográfica — Abordagens de Modelagem

Existem **três principais abordagens** de modelagem em destilação por membranas. A **abordagem física** usa princípios e leis físicas para modelar o sistema. A **abordagem data-driven** usa apenas dados experimentais para aprender a função que mapeia entradas e saídas.

E as **abordagens híbridas**, que combinam conhecimento físico com aprendizado de máquina, usando a física como regularizador para restringir o espaço de busca e melhorar a generalização com poucos dados. Existem diferentes estratégias: **PINNs** (Redes Neurais Integradas à Física), **modelos residuais** (a rede aprende o resíduo — Y_físico + Y_residual) e **regularização na função de perda** (PhyLoss), que penaliza desvios das leis físicas durante o treinamento.

Dentro dos modelos físicos, temos modelos **distribuídos** (1D, 2D) e modelos **reduzidos de 0 dimensões**, que é o utilizado neste trabalho.

---

## 9. Panorama de Publicações — Lacunas e Contribuições

Neste panorama, encontrei aproximadamente **4 publicações** usando abordagem física para V-AGMD/AGMD. A abordagem **data-driven** foi mais comum: redes neurais, regressões lineares, árvores de decisão.

Especificamente em V-AGMD com air gap, abordagens **híbridas** eu só encontrei **uma** — uma PINN. Neste trabalho, trabalhei com **todas essas arquiteturas**, incluindo **4 arquiteturas híbridas**.

**Lacunas identificadas:**
1. **Ausência de validação cruzada** — a maioria usa partição única, ignorando a estrutura dos grupos experimentais
2. **Seleção por métrica absoluta** — baseada apenas em RMSE, sem considerar a variabilidade estatística, favorecendo modelos complexos desnecessários
3. **Híbridos praticamente inexistentes** em V-AGMD com air gap

**Contribuições:** validação cruzada estruturada por regime de salinidade, critério de seleção 1-SE, e experimentação inédita de 4 arquiteturas híbridas no V-AGMD.

---

## 10. Sumário da Apresentação / Transição

A apresentação está dividida em **5 blocos**. Vamos agora para a **fundamentação teórica**.

---

## 11. Princípios da Destilação por Membranas

Aqui estão os princípios que regem a destilação por membranas. Você tem **dois fluxos principais**: um fluxo de **água quente** e um fluxo de **água fria**, separados por uma **membrana** e um **air gap**.

A membrana é **hidrofóbica** — ela só permite a passagem de **vapor**. A diferença de temperatura entre os dois lados gera um **gradiente térmico**, que aumenta a pressão de vapor do lado quente, fazendo com que as moléculas de água evaporem e atravessem a membrana.

O **air gap** funciona como **isolante térmico** — o ar é um ótimo isolante, então impede a troca de calor entre os dois lados, tornando o sistema energeticamente eficiente.

O **vácuo parcial** é aplicado para compensar o impedimento ao transporte de massa causado pelo air gap, incentivando o fluxo de vapor.

**Vantagens:** opera em temperaturas médias (60-80°C), compatível com calor residual e cogeração, e tem elevada tolerância à salinidade — é adequada para soluções de alta concentração onde a osmose inversa é limitada pelo aumento da pressão osmótica.

---

## 12. Fundamentos de Aprendizado de Máquinas

O aprendizado de máquina é voltado ao **aprendizado a partir dos dados**, identificando padrões e relações. Se divide em **regressão** e **classificação**. Em **regressão**, aproximamos Y ≈ f(X) minimizando o erro.

**Métricas:**
- **RMSE**: raiz do erro quadrático médio — penaliza erros maiores
- **R²**: coeficiente de determinação — no scikit-learn pode ser **negativo** quando o modelo tem viés elevado. O cálculo é `1 - (S_res / S_tot)`: se o modelo é pior que a média (como o modelo 0D para temperaturas), S_res > S_tot e R² fica negativo

**Divisão dos dados:** treino (ajusta parâmetros) + validação (escolhe hiperparâmetros) + teste (avalia final).

**Pré-processamento — Z-score:** transforma cada variável subtraindo sua média e dividindo pelo desvio padrão. O resultado é uma variável com média 0 e desvio 1. Por exemplo, se a temperatura de alimentação varia entre 60 e 80°C com média 70°C e desvio 5°C, um valor de 75°C vira (75-70)/5 = +1 (um desvio acima da média). Isso coloca todas as variáveis na **mesma escala**, evitando que uma grandeza como temperatura (dezenas de °C) domine o modelo sobre outra como concentração salina (unidades de g/L).

**Correlação — Pearson vs Spearman:**
- **Pearson (r)**: mede a **relação linear** entre duas variáveis. Se o gráfico de dispersão forma uma reta, o Pearson captura bem.
- **Spearman (ρ)**: mede a **relação monotônica** — se uma variável aumenta quando a outra aumenta, mesmo que não seja linear (ex: exponencial), o Spearman captura.
- Ambos variam de -1 a +1. Usamos os dois na análise exploratória porque relações no sistema V-AGMD podem ser não lineares.

---

## 13. Famílias de Modelos

**Quatro famílias** de modelos foram comparadas.

**Primeira: modelos lineares.** O **OLS** é a regressão linear clássica — minimiza os resíduos, sem regularização. A regularização controla a **flexibilidade** do modelo: quanto maior o alpha, menos flexível o modelo fica aos dados, reduzindo a complexidade e evitando overfitting. O **Ridge** usa penalidade L2: reduz os coeficientes sem zerá-los (todos contribuem um pouco). O **Lasso** usa L1: pode zerar coeficientes, funcionando como seleção automática. O **ElasticNet** combina L1 + L2.

**Segunda: árvores de decisão.** A **Decision Tree** faz partições binárias recursivas nos dados — cada nó divide o espaço em regiões, e a previsão é a média dos pontos em cada região (folha). É intuitiva mas overfitta facilmente. O **Random Forest** treina várias árvores em paralelo com bootstrap — a média reduz a variância. O **Gradient Boosting** treina árvores em sequência, cada uma corrigindo o resíduo da anterior. Testei todas essas três arquiteturas de árvore.

**Terceira: redes neurais (MLPs).** Redes fully connected com ativação não linear (ReLU ou tanh). O ajuste é por backpropagation. Hiperparâmetros: camadas, neurônios, ativação, taxa de aprendizado (LR), regularização L2, early stopping.

**Quarta: arquiteturas híbridas.**
- **PhyInput**: adiciona predições do modelo 0D como features extras
- **PhyResidual**: aprende o resíduo — saída = Y_físico + ε. A rede só precisa corrigir o desvio do modelo físico
- **PhyHybrid**: combina PhyInput + PhyResidual
- **PhyLoss**: incorpora a física na função de perda como regularização, penalizando desvios das leis físicas

---

## 14. Visão Geral dos Procedimentos

Começo com os **dados experimentais**, preparação (padronização, análise de correlações). A modelagem segue **3 estágios**: Stage 0 (clássicos), Stage 1 (redes neurais), Stage 2 (híbridos). Finalmente, o modelo selecionado é comparado com o **modelo 0D**.

---

## 15. Dados Experimentais

174 pontos, 3 regimes de salinidade (10, 40, 70 g/L). 5 entradas, 3 saídas.

---

## 16. Decisões da Preparação dos Dados

**Escalonamento: Z-score** — preserva a distribuição original, cada ponto medido em desvios-padrão da média.

**Validação: GroupKFold** — separa folds por regime operacional, orientando a busca para extrapolação.

---

## 17. Fluxo de Validação Cruzada e Seleção

GroupKFold → RMSE médio com erro padrão → regra 1-SE → modelo de menor complexidade.

---

## 18. Busca de Hiperparâmetros

Busca personalizada por target (3 fits por modelo). Famílias: Lineares (alpha), Árvores (profundidade, estimadores, LR), Redes Neurais (arquitetura, LR, L2, ativação), Híbridos (L2 congelados ou ω + L2 para PhyLoss).

---

## 19. Resultados — Modelos Lineares

Para cada target, RMSE de validação cruzada e de teste.

---

## 20. Árvores de Decisão — Eliminadas

Não foram melhores para nenhum target. Restaram: regressão linear, rede neural, híbridos.

---

## 21. Resultados — Análise por Variável de Saída

**T_alim_out:** Entre as híbridas, a melhor foi a **PhyResidual (base Flux)** com Test RMSE 0,183 — superando a Baseline Alim (0,215). O modelo 0D tem R² negativo para esta variável, mas a arquitetura residual com baseline Flux conseguiu corrigir parte do viés.

**T_ref_out:** Nenhum modelo superou a regressão linear (**Ridge**, 0,219). Entre as híbridas, a melhor foi a PhyResidual (base Alim), mas ainda acima do Ridge.

**Fluxo:** Principal demonstração da hibridização. **PhyResidual (base Flux)** obteve Test RMSE 0,054 — o menor entre todos os modelos — elevando o R² de 0,951 (Stage 0) para 0,979.

---

## 22. Arquiteturas Híbridas — Explicação

Combinam o modelo físico 0D com redes neurais. A rede aprende correções sistemáticas — como o viés de aproximadamente 1,58°C que o modelo 0D tem para T_alim. O modelo físico representa o conhecimento da física, e a rede corrige o que o modelo simplificado não captura.

Este papel de **corretor de viés** é a principal contribuição mensurável da arquitetura residual.

---

## 23. Comparação Final

**PhyResidual (base Flux)** foi o melhor híbrido para **Fluxo** e **T_alim_out**. **PhyResidual (base Alim)** foi o melhor híbrido para **T_ref_out**. Considerando todos os estágios, a seleção final pelo critério 1-SE foi: Baseline Alim para T_alim (Stage 1), Ridge para T_ref (Stage 0), PhyResidual Flux para Fluxo (Stage 2).

---

## 24. Conclusões

Conclusões principais: a hibridização **demonstrou ganho mensurável para o fluxo** (PhyResidual, RMSE 0,054). Para as temperaturas, modelos mais simples (regressão linear e rede neural) tiveram performance comparável ou superior às híbridas.

**Trabalhos futuros:** substituir o modelo 0D pelo modelo 2D como referência física; construir PINNs a partir das EDOs do modelo 2D.
