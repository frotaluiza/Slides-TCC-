# Roteiro da Apresentação

## A Crise Global da Água

A crise global da água é tanto de quantidade quanto de qualidade. 4 bilhões sofrem com escassez, 1,7 bilhão bebem água contaminada, causando mais de 500 mil mortes por ano. É um problema que demanda soluções urgentes e inovadoras. [~1 min]


---

## O Problema no Brasil

No Brasil, 2026 é desafiante para a gestão de água. O Cantareira está pouco acima de 30\%. No Nordeste, 4 meses de chuva contra 8 de seca extrema. A dessalinização pode reduzir o custo da água em até 10 vezes: de R\$ 2,63 a R\$ 4,21/m³ segundo estudo da CNI. A maior planta do Brasil, no ES, atende 80 mil pessoas. Com 8.500 km de costa, o potencial de expansão é enorme. [~1 min]


---

## Dessalinização: Realidade Global

A dessalinização já é realidade global consolidada. Na Arábia Saudita, responde por 86\% do abastecimento. Em Israel, 80\%. Mais de 150 países usam a tecnologia, atendendo 300 milhões de pessoas. No Brasil, Fernando de Noronha aumentou a oferta em 122\% e eliminou o racionamento. [~45s]


---

## Ilha de Policogeração Sustentável (LabMEMS/COPPE)

A Ilha de Policogeração Sustentável da COPPE, inaugurada em 2022, é o projeto que abriga este trabalho. É um sistema que integra painéis solares de alta concentração com um dessalinizador V-AGMD, produzindo eletricidade para 25 residências e água para mais de 100 pessoas por dia. O foco são comunidades remotas. O projeto atende aos ODS 6, 7 e 13. [~1 min]


---

## 

(sem nota)


---

## V-AGMD: Inovação Tecnológica

A destilação por membrana é a tecnologia central deste trabalho. Ela combina princípios térmicos com membrana: o vapor passa por uma membrana hidrofóbica impulsionado por diferença de temperatura. A configuração V-AGMD adiciona vácuo na lacuna de ar para aumentar o fluxo de permeado. A grande inovação é operar com calor solar ou residual, sem precisar de altas pressões como a osmose reversa. O desafio é modelar esse sistema com dados limitados. [~1 min]


---

## Motivação e Objetivos

A motivação para este trabalho é que um modelo preditivo confiável permite otimizar a operação do dessalinizador, reduzir a necessidade de experimentos caros, e viabilizar a operação autônoma em comunidades remotas. O objetivo geral é avaliar estratégias de modelagem — de regressões lineares a arquiteturas híbridas — para prever o desempenho do V-AGMD. [~1,5 min]


---

## Organização da Apresentação

Apresentação dividida em 5 blocos. Vamos à fundamentação. [~30s]


---

## Abordagens de Modelagem em MD

A revisão mostra três grandes abordagens para modelagem em MD. Física: interpretável mas cara. Data-driven: flexível mas dependente dos dados. Híbridos: combinam o melhor dos dois mundos. [~1,5 min]


---

## Panorama V-AGMD/AGMD

Tabela consolidada da revisão bibliográfica, organizada por tipo de abordagem. Destaque para o reduzido número de trabalhos híbridos em MD — este trabalho é o único híbrido para V-AGMD. [~1,5 min]


---

## Lacunas e Contribuições

A literatura tem limitações em validação e seleção. Este trabalho contribui com validação por grupos, busca sistemática, e critério de complexidade. [~1 min]


---

## Princípios da Destilação por Membranas

A destilação por membranas é um processo térmico de separação. A água salgada é aquecida e circula por um lado de uma membrana hidrofóbica — ela não permite a passagem de líquido, mas o vapor consegue atravessar os poros. A força motriz é a diferença de temperatura: do lado quente a água evapora, o vapor migra pelos poros e condensa do lado frio, gerando água pura. Existem quatro configurações principais: DCMD, AGMD, VMD e SGMD. A V-AGMD, usada neste trabalho, combina o espaço de ar da AGMD com vácuo parcial, reduzindo a resistência ao transporte de vapor sem perder o isolamento térmico. [~2 min]


---

## Modelo Físico Reduzido 0D

É importante distinguir três níveis de modelos físicos na literatura de MD. O primeiro são os modelos distribuídos — como os de Alsaadi (2013), com discretização 1D, e Ansari (2022), com CFD 2D. Eles resolvem explicitamente os perfis espaciais de temperatura, concentração e velocidade ao longo do módulo. Perfis espaciais significam o seguinte: num sistema V-AGMD real, a temperatura da água quente não é uniforme — ela entra a cerca de 65°C na entrada e vai esfriando ao longo do canal conforme perde calor para o lado frio. O fluxo de permeado também varia ao longo do comprimento, sendo maior onde o gradiente térmico é maior. A concentração de sal aumenta conforme a água evapora. Modelos distribuídos capturam essas variações — discretizam o módulo em dezenas de segmentos e resolvem equações em cada ponto. Têm alta fidelidade física, mas exigem muitos parâmetros e alto custo computacional. O segundo nível são modelos físicos simplificados baseados em balanços globais, como o de Andrés-Mañas (2023), que aplica balanços de massa e energia em estado estacionário sem discretizar o domínio. O terceiro nível — e o que usamos neste trabalho — são os modelos reduzidos 0D, como o de Lisboa (2024). Diferentemente dos distribuídos, eles tratam o módulo como um volume único com grandezas médias e resistências equivalentes. Em vez de calcular T(x) ao longo do canal, assumem uma temperatura média representativa para o módulo inteiro. Não resolvem equações diferenciais, apenas balanços globais e relações algébricas. Isso reduz drasticamente o custo computacional, permitindo gerar estimativas físicas rápidas. Em compensação, perdem detalhe — não capturam gradientes axiais, polarização térmica nem fouling. E é justamente essa limitação que motiva as abordagens híbridas, que combinam a física do modelo 0D com aprendizado a partir dos dados. [~3 min]


---

## Fundamentos de Aprendizado de Máquinas

Um ponto importante é o pré-processamento por padronização Z-score. As variáveis de entrada do sistema V-AGMD têm unidades físicas e ordens de grandeza muito distintas — temperatura em °C, vazão em L/h, pressão de vácuo em mbar, concentração salina em g/L. O Z-score centraliza cada variável subtraindo sua média e dividindo pelo desvio padrão. Assim, todas passam a ter média zero e desvio padrão unitário, ficando em escala comparável. Isso evita que variáveis com magnitudes maiores — como temperatura — dominem desproporcionalmente o ajuste do modelo. É especialmente importante em modelos regularizados como Ridge e Lasso, onde a penalização dos coeficientes é sensível à escala. [~1,5 min]


---

## Famílias de Modelos

Quatro famílias de modelos foram comparadas. Os modelos lineares servem como referência. As árvores capturam relações não lineares. As redes neurais têm alta flexibilidade. Os híbridos combinam física com dados. [~1,5 min]


---

## Pipeline e Dados

O pipeline começa com os dados experimentais. Temos 5 variáveis de entrada: Alim\_T\_in — temperatura de entrada da alimentação, que define a força motriz térmica; Ref\_T\_in — temperatura de entrada do resfriamento, que junto com a anterior estabelece o gradiente térmico; Ref\_V\_in — vazão da corrente de resfriamento, que afeta o regime de escoamento e o tempo de residência; P\_vacuum — pressão de vácuo na câmara de ar, que modifica a resistência difusiva; e C\_NaCl — concentração de sal, que reduz a pressão de vapor da solução. As 3 saídas são: Fluxo de permeado, temperatura de saída da alimentação e temperatura de saída do resfriamento. O modelo físico 0D é executado para cada observação, gerando previsões que alimentam as arquiteturas híbridas. O pré-processamento é ajustado apenas no treino de cada fold. A modelagem segue 3 etapas de complexidade crescente. [~2,5 min]


---

## Validação Cruzada e Seleção de Modelos

A validação usa GroupKFold com 3 partições. A cada iteração, um regime fica de fora — então temos 3 valores de RMSE, um para cada fold. O desvio padrão desses 3 RMSEs mede o quanto o desempenho do modelo varia quando testado em regimes diferentes. Se um modelo tem RMSE médio de 0,070 com desvio de 0,010, isso significa que o RMSE pode variar cerca de 0,010 para mais ou para menos dependendo do regime. O critério 1-SE diz o seguinte: calculamos o RMSE médio de cada modelo entre os 3 folds. Pegamos o melhor modelo. Depois, consideramos todos os modelos cujo RMSE médio está dentro de 1 desvio padrão acima do melhor. Entre esses, escolhemos o mais simples. A lógica é: se a diferença entre dois modelos é menor que a própria variabilidade da avaliação, não dá para dizer que um é realmente melhor — então fica com o mais simples. [~2 min]


---

## Busca de Hiperparâmetros

A busca foi organizada por família. Nos lineares, o foco é a intensidade da regularização. Nas árvores, controlamos profundidade e número de estimadores. Nas redes neurais, a busca envolve arquitetura, taxa de aprendizado e regularização L2. Já nos híbridos, a busca foi restrita: mantivemos toda a estrutura da baseline fixa e variamos apenas o L2, para avaliar o efeito da incorporação da física sem alterar a arquitetura. [~1,5 min]


---

## Arquiteturas Híbridas

Vamos às arquiteturas híbridas. A primeira é o HPD, Hybrid Physics Data. A ideia é simples: pegamos as predições do modelo físico 0D e concatenamos como variáveis de entrada extras, formando um vetor expandido [X, Y_phy]. A rede então aprende a relação entre esse conjunto expandido e as saídas experimentais, podendo explorar complementaridades entre os dados medidos e a física. A terceira é o ZohanResidual, que usa modelagem residual. O modelo físico dá uma estimativa inicial, e a rede neural aprende uma correção para somar a ela: Y_hat = Y_phy + Y_res. A rede não precisa aprender o comportamento inteiro do zero — só o desvio em relação ao modelo físico. A quarta é o HRNN, Hybrid Residual Neural Network, que combina as duas anteriores: a rede recebe tanto as variáveis experimentais quanto a predição física como entrada, E produz uma correção residual somada à física. É a arquitetura mais flexível, mas também a mais complexa. Por fim, o Luc não altera a arquitetura da rede — em vez disso, adiciona um termo na função de perda que penaliza a diferença entre a predição da rede e a predição física. A função objetivo passa a ter dois termos: o erro em relação aos dados experimentais e uma penalização pelo desvio em relação ao modelo físico. [~3 min]


---

## Análise Exploratória

A análise exploratória mostra que as temperaturas de saída têm forte correlação linear com variáveis térmicas, enquanto o fluxo de permeado apresenta comportamento mais complexo, dependendo de múltiplas variáveis. Isso motiva a modelagem multivariada. [~1 min]


---

## Correlações

O coeficiente de Pearson mede a correlação linear entre duas variáveis — valores próximos de 1 ou -1 indicam relação linear forte. O de Spearman, calculado sobre os postos, mede associações monotônicas, capturando relações que não precisam ser lineares, mas em que uma variável tende a crescer ou decrescer consistentemente com a outra. Comparando os dois mapas, vemos que as temperaturas de saída têm correlações lineares fortes com as entradas térmicas (|r| > 0,9), enquanto o fluxo apresenta correlações moderadas e mais distribuídas — isso justifica a abordagem multivariada. [~1,5 min]


---

## Modelo Físico 0D vs Experimental

O modelo 0D captura tendências mas com dispersão. O ZohanResidual reduz o RMSE do fluxo em 72\% (0,215 $\rightarrow$ 0,060) e o da temperatura de alimentação em 91\% (1,613 $\rightarrow$ 0,141). [~1 min]


---

## Desempenho Consolidado

O ZohanResidual (base Alim) é o melhor para fluxo (0,060) e temperatura de alimentação (0,141). O ZohanHRNN (base Alim) vence para temperatura de saída (0,211). A seleção foi feita pelo critério 1-SE entre famílias, priorizando o modelo mais simples dentro de 1 desvio padrão do melhor. [~1,5 min]


---

## Gráficos de Desempenho

O gráfico da esquerda mostra o RMSE por target para os principais modelos. O da direita mostra o melhor modelo de cada família, permitindo comparar o ganho das arquiteturas híbridas em relação às lineares e neurais. [~40s]


---

## Seleção dos Modelos Vencedores

Foram treinadas 3 baselines independentes, cada uma priorizando um alvo diferente: Alim, Ref e Flux. A baseline Alim — 1 camada [256] — teve a arquitetura mais simples e apresentou o melhor equilíbrio de desempenho entre os 3 alvos. As baselines Ref e Flux geraram redes mais complexas, com 2 e 3 camadas respectivamente, mas o ganho em seus respectivos alvos prioritários ficou dentro de 1 desvio padrão da validação cruzada. Como a validação tem 3 folds (um por regime de salinidade), o desvio padrão mede a variabilidade do RMSE entre regimes. Se a diferença entre a rede complexa e a baseline é menor que essa variabilidade, não podemos afirmar que a rede complexa é realmente melhor — a diferença pode ser ruído amostral. Pelo critério 1-SE, selecionamos o modelo mais simples: a baseline Alim com 1 camada [256]. [~2 min]


---

## Análise do Treinamento dos Modelos Vencedores

A curva de aprendizado mostra convergência estável com Early Stopping, com o erro de validação acompanhando o de treino sem sinais de overfitting. [~40s]


---

## Híbridos vs MLP Pura

A incorporação de informação física via arquiteturas híbridas trouxe ganhos significativos em relação à MLP pura. O ZohanResidual reduziu o RMSE do Alim em 31,2\% e do Flux em 7,7\%. O ZohanHRNN reduziu o RMSE do Ref em 51,0\%. [~1 min]


---

## O que a Hibridização está Corrigindo?

O ganho dos híbridos não é capturar relações não lineares — a região é aproximadamente linear (OLS com R² > 0,95). O ganho é corrigir o viés dos modelos data-driven usando a física como referência. A linha y=x representa predito = experimental. [~1 min]


---

## Comparação Final — Modelos Vencedores vs Modelo 0D

Comparação final: ZohanResidual para fluxo e temperatura de alimentação, ZohanHRNN para temperatura de saída do circuito de resfriamento. A seleção por target com critério 1-SE permite que cada alvo tenha o modelo mais adequado. [~1 min]


---

## Resumo dos Resultados

Resumo: o ZohanResidual (base Alim) vence para fluxo e temperatura de alimentação; o ZohanHRNN (base Alim) vence para temperatura de saída. A seleção foi feita pelo critério 1-SE entre famílias. [~30s]


---

## Conclusões

Conclusões principais: ZohanResidual (base Alim) vence para fluxo e temperatura de alimentação; ZohanHRNN (base Alim) vence para Ref. O critério 1-SE entre famílias com número de parâmetros como medida de complexidade guiou a seleção. [~1,5 min]


---

## Contribuições e Trabalhos Futuros

As principais contribuições são o pipeline com GroupKFold, a comparação de 4 arquiteturas híbridas, e o critério 1-SE entre famílias com número de parâmetros. Como trabalhos futuros: duas abordagens com PINNs (puramente física + residual, e híbrida com dados) e otimização multi-objetivo. [~1,5 min]
