# Roteiro de Apresentação — 30 min

## 1. Introdução (~5 min) — 8 slides

### Slide 1: A Crise Global da Água (~45s)
"Bom dia a todos. Meu nome é Luiza Frota e hoje vou apresentar meu trabalho de conclusão de curso.

A escassez de água é uma crise global: 4 bilhões de pessoas enfrentam escassez severa ao menos um mês por ano, 2,2 bilhões não têm acesso a água potável segura, e 1,7 bilhão bebem água contaminada — causando cerca de 1 milhão de mortes por ano. A demanda deve superar a oferta em 40% até 2030. É um problema urgente que demanda soluções."

### Slide 2: O Problema no Brasil (~45s)
"No Brasil, o cenário também é crítico. 2026 é um ano desafiador para a gestão hídrica, com chuvas abaixo da média. O Cantareira está com cerca de 30% da capacidade. No Nordeste, são 4 meses de chuva contra 8 de seca extrema.

A boa notícia: a dessalinização pode reduzir o custo da água em até 10 vezes — de R$ 2,63 a R$ 4,21 por m³ segundo a CNI. A maior planta do Brasil, no Espírito Santo, já atende 80 mil pessoas. Com 8.500 km de costa, nosso potencial é enorme."

### Slide 3: Dessalinização — Realidade Global (~45s)
"A dessalinização já é realidade consolidada no mundo. Na Arábia Saudita, responde por 86% do abastecimento. Em Israel, 80%. Mais de 150 países usam a tecnologia, atendendo 300 milhões de pessoas.

No Brasil, Fernando de Noronha aumentou a oferta de água em 122% com osmose reversa, eliminando o racionamento. Segundo a CNI, a indústria ganha autonomia: a tecnologia desvincula o crescimento da oferta limitada de água doce."

### Slide 4: Ilha de Policogeração Sustentável — LabMEMS/COPPE (~1 min)
"É neste contexto que surge o projeto onde este trabalho está inserido: a Ilha de Policogeração Sustentável da COPPE/UFRJ, inaugurada em 2022.

O sistema integra painéis solares de alta concentração que geram 5 kW de eletricidade — suficiente para cerca de 25 residências — e mais 8 kW de calor recuperável. O dessalinizador V-AGMD produz 1.000 litros de água potável por dia, atendendo mais de 100 pessoas. O foco são comunidades remotas e off-grid, como o semiárido nordestino.

O projeto está alinhado aos ODS 6 — água potável, ODS 7 — energia limpa, e ODS 13 — ação climática."

### Slide 5: V-AGMD — Inovação Tecnológica (~45s)
"A tecnologia central é a destilação por membrana, ou MD. Diferente da osmose reversa — que domina o mercado mas exige altas pressões — a MD usa calor como força motriz.

A configuração V-AGMD inova ao adicionar vácuo na lacuna de ar, aumentando o fluxo sem perder o isolamento térmico. Suas vantagens: opera a baixas temperaturas e pressões, atinge mais de 99,9% de rejeição de sais, trata salmouras que a RO não consegue, e pode usar calor solar ou residual.

O desafio: como modelar e prever o desempenho desse sistema com dados experimentais limitados?"

### Slide 6: Motivação e Objetivos (~1 min)
"Um modelo preditivo confiável permite duas coisas: primeiro, ser usado em etapas de otimização para maximizar o fluxo de permeado; segundo, operar comunidades remotas com supervisão mínima.

O objetivo geral é avaliar estratégias de modelagem — de regressões lineares a arquiteturas híbridas — para prever o desempenho do V-AGMD. Os objetivos específicos incluem estruturar dados por regimes, comparar 4 famílias de modelos, aplicar GroupKFold, e selecionar o modelo por desempenho e complexidade."

### Slide 7: Organização da Apresentação (~20s)
"A apresentação está organizada em 5 blocos. Vamos à revisão bibliográfica."

---

## 2. Revisão Bibliográfica (~3 min) — 3 slides

### Slide 8: Abordagens de Modelagem em MD (~1,5 min)
"A modelagem de MD pode ser dividida em três grandes abordagens, como mostra a tabela.

Modelos físicos, como o de Alsaadi e Ansari para AGMD e Lisboa para V-AGMD, são interpretáveis mas têm alto custo computacional. Modelos data-driven, como os de Requena e Kim para V-AGMD, são flexíveis mas têm generalização limitada. Já os híbridos combinam física com dados — as PINNs de Andrés-Mañas para VMD e o CFD+ANN de Abdulrahim para AGMD.

A grande lacuna: arquiteturas híbridas residuais para V-AGMD ainda não foram publicadas na literatura."

### Slide 9: Panorama V-AGMD/AGMD (~1 min)
"Esta tabela consolida os principais trabalhos específicos em AGMD e V-AGMD. Destaque para Requena, que usou uma MLP simples com split 70/15/15, e Kim, que comparou regressão linear, GNN e MLP para V-AGMD.

Nosso trabalho se diferencia por ser o único híbrido para V-AGMD, combinando 4 famílias de modelos com 4 arquiteturas híbridas, prevendo simultaneamente fluxo e temperaturas de saída."

### Slide 10: Lacunas e Contribuições (~30s)
"As principais lacunas da literatura: divisão aleatória simples, validação cruzada raramente usada, e seleção heurística de hiperparâmetros. Este trabalho contribui com GroupKFold por regimes, busca sistemática, critério 1-SE com complexidade, e 4 arquiteturas híbridas."

---

## 3. Fundamentação (~4 min) — 4 slides

### Slide 11: MD Física e Modelo Reduzido 0D (~1,5 min)
"A fundamentação começa com a física da MD: uma membrana hidrofóbica separa água quente de uma câmara fria. O vapor migra impulsionado pelo gradiente térmico — evapora na interface quente, atravessa os poros e condensa no lado frio.

A configuração V-AGMD adiciona vácuo na lacuna de ar, reduzindo a resistência ao transporte e aumentando o fluxo.

O modelo físico reduzido 0D, baseado em Lisboa 2024, simplifica o sistema com balanços globais de massa e energia. Suas vantagens: baixo custo computacional e consistência termodinâmica. Suas limitações: ignora gradientes axiais, polarização e fouling — o que justifica as abordagens híbridas."

### Slide 12: Fundamentos de ML (~1,5 min)
"O problema é de regressão supervisionada multi-saída: queremos aprender uma função que mapeie 5 entradas em 3 saídas — fluxo de permeado e duas temperaturas.

A métrica principal é o RMSE. Três estratégias contra overfitting: regularização L1/L2, GroupKFold, e o critério 1-SE com complexidade.

O GroupKFold separa os dados por regimes experimentais — 10, 40 e 70 g/L — garantindo que amostras do mesmo regime não vazem entre treino e teste."

### Slide 13: Famílias de Modelos (~1 min)
"Quatro famílias foram comparadas. Modelos lineares — OLS, Ridge, Lasso — servem como referência de menor complexidade. Árvores e ensembles capturam não linearidades. Redes neurais têm alta flexibilidade. E os híbridos — PhyResidual, PhyHybrid, PhyLoss e BaselineHibrido — combinam física com dados.

O vencedor foi o PhyResidual, uma arquitetura de conexão residual: a rede aprende a correção em torno da predição do modelo físico 0D. Redução de 31% no RMSE do fluxo frente ao melhor modelo linear."

### Slide 14: Resumo da Fundamentação (~30s)
"Em resumo: a física da MD com modelo 0D, os fundamentos de ML — regressão multi-saída, métricas, validação — e as quatro famílias de modelos. Vamos à metodologia."

---

## 4. Metodologia (~6 min) — 5 slides

### Slide 15: Pipeline e Dados (~1,5 min)
"O pipeline começa com dados experimentais do V-AGMD piloto em 3 regimes de salinidade. O modelo físico 0D é executado para cada observação, gerando previsões que alimentam as arquiteturas híbridas.

O pré-processamento usa padronização Z-score, ajustada apenas no treino de cada fold para evitar vazamento. A modelagem segue 3 etapas de complexidade crescente: primeiro modelos clássicos, depois redes neurais, e por fim os híbridos."

### Slide 16: Validação e Seleção (~1,5 min)
"A validação usa GroupKFold com 3 partições — cada fold reserva um regime de salinidade inteiro para validação.

O critério de seleção é hierárquico em três passos: primeiro, escolhe-se o modelo com melhor RMSE no fluxo; segundo, considera-se todos os modelos dentro de 1 desvio padrão do melhor; terceiro, entre eles, seleciona-se o de menor complexidade.

A métrica final é calculada sobre predições Out-of-Fold — ou seja, o modelo é retreinado do zero em cada partição."

### Slide 17: Busca de Hiperparâmetros (~1,5 min)
"Cada família teve espaços de busca específicos. Modelos lineares variam o parâmetro de regularização alpha. Árvores controlam profundidade máxima e amostras por folha. Redes neurais buscam arquitetura e taxa de aprendizado.

Os híbridos têm busca restrita — apenas o parâmetro L2 varia, mantendo a baseline fixa. Isso reduz custo computacional e permite isolar o efeito da incorporação da física."

### Slide 18: Arquiteturas Híbridas (~1 min)
"Quatro arquiteturas foram implementadas. A BaselineHibrido é a referência neural sem física. A PhyInput — ZohanHPD — adiciona a saída do modelo físico como uma feature extra na entrada.

A PhyResidual — vencedora — aprende a correção residual: a rede prevê o desvio entre a predição física e o valor real. A PhyHybrid combina as duas abordagens anteriores. E a Luc usa regularização física na função de perda."

### Slide 19: Resumo da Metodologia (~30s)
"Resumo: dados de 3 regimes, GroupKFold, critério 1-SE com complexidade, 4 famílias de modelos, busca sistemática. Vamos aos resultados."

---

## 5. Resultados (~8 min) — 7 slides

### Slide 20: Análise Exploratória (~1 min)
"A análise exploratória mostra que as temperaturas de saída têm forte correlação linear com variáveis térmicas — como esperado pela troca de calor entre correntes. Já o fluxo de permeado apresenta correlações mais moderadas e distribuídas entre múltiplas variáveis, indicando um comportamento mais complexo que justifica a modelagem multivariada."

### Slide 21: Correlações (~40s)
"Os mapas de correlação de Pearson e Spearman confirmam: temperaturas com correlações fortes (acima de 0,9), fluxo com correlações moderadas (em torno de 0,7). A proximidade entre Pearson e Spearman indica relações aproximadamente lineares na faixa estudada."

### Slide 22: Modelo 0D vs Experimental (~1 min)
"O modelo físico 0D captura as tendências gerais, mas com dispersão considerável — RMSE de 0,215 para o fluxo. O modelo híbrido PhyResidual reduz esse erro para 0,061 — uma redução de 72%. As temperaturas também melhoram significativamente."

### Slide 23: Desempenho Consolidado (~1,5 min)
"A tabela mostra o desempenho OOF de todos os modelos. O PhyResidual é o melhor para o fluxo — RMSE 0,061, R² 0,978. O MLP sklearn fica em segundo com 0,071. Já nas temperaturas, o OLS tem o melhor desempenho — RMSE 0,246 para T_alim e 0,251 para T_ref.

Isso revela um trade-off importante: o modelo híbrido concentra seu ganho no fluxo, mas perde um pouco nas temperaturas. Modelos lineares continuam sendo uma boa opção para as variáveis térmicas."

### Slide 24: Seleção do Modelo Vencedor (~1,5 min)
"O PhyResidual foi selecionado pelo critério hierárquico: tem o melhor RMSE no fluxo, está dentro de 1 desvio padrão, e tem complexidade adequada. A redução é de 31% frente ao melhor modelo linear — OLS com 0,089 — e de 72% frente ao modelo 0D com 0,215.

As curvas de aprendizado mostram que o treinamento foi estável, com early stopping atuando adequadamente. A análise de sensibilidade ao L2 mostra que o modelo é robusto — o erro se mantém estável na região de baixa regularização."

### Slide 25: Comparação Final — PhyResidual vs Modelo 0D (~1 min)
"Os gráficos overlay mostram claramente a superioridade do PhyResidual em relação ao modelo 0D para as três variáveis. O modelo híbrido consegue acompanhar muito melhor os dados experimentais.

Na tabela comparativa: PhyResidual tem RMSE 0,061 para o fluxo, contra 0,089 do OLS e 0,215 do modelo 0D. Para as temperaturas, o OLS ainda lidera, mas o híbrido fica muito próximo."

### Slide 26: Resumo dos Resultados (~30s)
"Resumo: o modelo híbrido PhyResidual foi o vencedor para predição do fluxo. Modelos lineares continuam sendo a melhor opção para temperaturas. A validação com GroupKFold garantiu uma avaliação realista."

---

## 6. Conclusões e Contribuições (~3 min) — 2 slides

### Slide 27: Conclusões (~1,5 min)
"Concluindo: o modelo híbrido PhyResidual obteve o melhor desempenho para predição do fluxo de permeado, com RMSE de 0,061 — uma redução de 31% em relação ao melhor modelo linear.

Modelos lineares, especialmente a OLS, tiveram o melhor desempenho para as temperaturas de saída. Isso sugere que o comportamento térmico é aproximadamente linear na faixa operacional estudada.

O pipeline com GroupKFold por regimes e critério 1-SE com complexidade é mais robusto do que a abordagem de hold-out simples usada na maioria dos estudos de V-AGMD, como Requena 2023 e Kim 2022.

A principal limitação é que o modelo híbrido piorou o desempenho nas temperaturas em relação ao OLS, o que sugere que uma seleção multi-objetivo ou modelos distintos por variável podem ser explorados no futuro."

### Slide 28: Contribuições e Trabalhos Futuros (~1,5 min)
"As principais contribuições deste trabalho são: primeiro, um pipeline completo de modelagem com validação cruzada agrupada por regimes experimentais — algo inédito para V-AGMD. Segundo, a implementação e comparação de quatro arquiteturas híbridas físico-dados. Terceiro, um critério de seleção parcimoniosa que combina a regra 1-SE com penalização de complexidade. E quarto, o modelo PhyResidual, que atingiu RMSE de 0,061 para o fluxo de permeado.

Para trabalhos futuros, sugiro duas abordagens com PINNs: uma com função de perda híbrida combinando dados e regularização física, e outra com uma PINN treinada exclusivamente com dados sintéticos do modelo 0D, que poderia substituir o próprio modelo físico na arquitetura residual. Além disso, uma otimização multi-objetivo considerando simultaneamente fluxo e temperaturas seria um avanço natural.

Agradeço a atenção de todos e estou aberta a perguntas."
