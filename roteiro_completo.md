# Roteiro Completo da Apresentação — TCC V-AGMD

> Formato: duas colunas — **Fala** (o que dizer) | **Ações do Chat** (alterações feitas / respostas)

---

## Abrir / Slide de Título

| Fala | Ações do Chat |
|------|---------------|
| Boa tarde. Este é o meu projeto final de graduação, cujo título é **"Modelagem Híbrida com Regularização Física e Seleção Parcimoniosa de Modelos para Predição de Desempenho em Destilação por Membranas"**. | — |

---

## Sumário

| Fala | Ações do Chat |
|------|---------------|
| Este é o sumário do TCC: vamos começar com a **introdução**, depois **revisão bibliográfica**, **fundamentação teórica**, **metodologia proposta**, seguindo para **resultados**, **conclusões** e **referências**. | — |

---

## 1. A Crise Global da Água

| Fala | Ações do Chat |
|------|---------------|
| A crise global da água é tanto de quantidade quanto de qualidade. **4 bilhões** de pessoas enfrentam escassez severa de água, sendo que **2,2 bilhões** não têm acesso a água potável segura. A demanda global deve superar a oferta em **40% até 2030**. | ✅ **1,7 bi/fontes contaminadas removido** do slide — mantido apenas 4 bi (escassez severa) + 2,2 bi (água potável). Fonte: WHO/IDRA. |

---

## 2. O Problema no Brasil

| Fala | Ações do Chat |
|------|---------------|
| No Brasil, 2026 foi um ano desafiador, com chuvas abaixo da média. O **Sistema Cantareira** operou a aproximadamente **30%** da sua capacidade. No Nordeste, um cenário de **4 meses de chuva para 8 meses de seca extrema**. | ✅ Descrição do que são ANA e CNN **adicionada** no slide. ANA = Agência Nacional de Águas; CNN Brasil = canal de notícias. |
| A dessalinização pode reduzir o custo da água em até **10 vezes** — de R$ 2,63 a R$ 4,21/m³ (CNI). A maior planta do Brasil (ES) atende **80 mil pessoas**. Com **8.500 km de costa**, o potencial de expansão para essa tecnologia é enorme. | — |

---

## 3. Dessalinização — Contexto Global

| Fala | Ações do Chat |
|------|---------------|
| A dessalinização já é uma realidade consolidada globalmente. Mais de **150 países** usam a tecnologia. Na Arábia Saudita, responde por **86%** do abastecimento; em Israel, **80%**. | — |

---

## 4. V-AGMD no Contexto da Dessalinização

| Fala | Ações do Chat |
|------|---------------|
| A dessalinização divide-se em duas grandes famílias: processos **térmicos** (destilação convencional) e processos de **membrana** (osmose inversa, MD). A **Destilação por Membrana (MD)** é um processo híbrido termo-membrana: uma membrana hidrofóbica separa o vapor d'água da salmoura aquecida. | — |
| A configuração **V-AGMD** combina um **espaço de ar** (que funciona como isolante térmico) com **vácuo parcial** (que reduz a resistência ao transporte de vapor). O ar impede a troca de calor entre os lados quente e frio, tornando o sistema energeticamente eficiente. O vácuo compensa o impedimento ao transporte de massa causado pelo air gap. | — |

---

## 5. Ilha de Policogeração Sustentável

| Fala | Ações do Chat |
|------|---------------|
| Este trabalho está inserido no projeto **CT2 — Ilha de Policogeração Sustentável**, do LabMEMS, COPPE/UFRJ, inaugurado em 2022. É um protótipo pioneiro que une **geração de água potável** com **energia solar térmica**. | ✅ **ODS 6, 7 e 13 removido** do slide (conforme instrução: "não faz sentido falar disso agora"). |
| O sistema produz cerca de **5 kWₑ** — suficiente para aproximadamente **25 residências** — e mais **8 kWₜ** recuperáveis em micro-trocadores. O dessalinizador V-AGMD produz **1.000 L/dia** de água destilada, o que pode prover água para **mais de 100 pessoas/dia**. | ✅ **Último tópico substituído** por descrição do **Projeto Água Doce**: programa do governo federal que expande acesso à água potável no Semiárido nordestino por meio de dessalinização, atendendo comunidades remotas não cobertas pelo sistema tradicional de abastecimento. |
| O foco são **comunidades remotas** do Semiárido nordestino, em articulação com o **Projeto Água Doce**. | — |

---

## 6. Imagem da Instalação

| Fala | Ações do Chat |
|------|---------------|
| (Slide apenas para mostrar a instalação física do protótipo V-AGMD na Ilha de Policogeração.) | ✅ **Menção ao rejeito de sal removida** do esquemático. |

---

## 7. Motivação e Objetivos

| Fala | Ações do Chat |
|------|---------------|
| A motivação é a necessidade de **prever o desempenho** desse protótipo V-AGMD. Temos **dados experimentais** de aproximadamente **174 pontos** e **3 regimes de salinidade**. | ✅ **"Limitados" removido** — usar apenas "dados experimentais". ✅ Não mencionar "dados experimentais limitados". |
| Já existe um **modelo físico de 0 dimensões** disponível na literatura, publicado pelo laboratório e implementado em código C#, que serviu de referência para este trabalho. | ✅ **Caracterização do modelo físico como "limitado" removida** — apenas descrevê-lo como referência disponível. |
| O **objetivo geral** é avaliar estratégias de **modelagem baseada em dados** e **modelagem híbrida físico-dados** para a predição do **fluxo de permeado** e **temperaturas de saída** deste módulo de destilação. | — |

---

## 8. Revisão Bibliográfica — Abordagens de Modelagem

| Fala | Ações do Chat |
|------|---------------|
| Existem **três principais abordagens** de modelagem em destilação por membranas. A **abordagem física** usa princípios e leis físicas para modelar o sistema. A **abordagem data-driven** usa apenas dados experimentais para aprender a função que mapeia entradas e saídas. | — |
| E as **abordagens híbridas**, que tentam **restringir** os modelos aos princípios físicos, adicionando algum tipo de regragem determinística na rede para guiar os resultados. | ✅ **Descrição de modelos híbridos melhorada**: "Modelos híbridos combinam conhecimento físico com aprendizado de máquina, usando a física como regularizador para restringir o espaço de busca e melhorar a generalização com poucos dados." ✅ **PINNs traduzidas** como **Redes Neurais Integradas à Física** (Physics Integrated Neural Networks). ✅ **Definição mais abrangente** de modelos híbridos buscada na literatura e incorporada ao slide. |
| Dentro dos modelos físicos, temos modelos **distribuídos** (1D, 2D) que consideram parâmetros espaciais, e modelos **reduzidos de 0 dimensões**, que é o utilizado neste trabalho. Em data-driven, temos redes neurais e outras formas de regressão. E nos híbridos, temos PINNs e modelos residuais com correção da física. | ✅ **Descrição de "modelos residuais com correção da física"** reformulada para maior clareza: "A rede neural não aprende a variável diretamente, mas sim o **resíduo** em relação ao modelo físico — ou seja, o desvio entre a predição física e o valor real. A saída final é Y_físico + Y_residual." |

---

## 9. Panorama de Publicações — Lacunas e Contribuições

| Fala | Ações do Chat |
|------|---------------|
| Neste panorama, encontrei aproximadamente **4 publicações** usando abordagem física para V-AGMD/AGMD. A abordagem **data-driven** foi mais comum: redes neurais, regressões lineares, árvores de decisão. | — |
| Especificamente em V-AGMD com air gap, abordagens **híbridas** eu só encontrei **uma** — uma PINN. Neste trabalho, trabalhei com **todas essas arquiteturas**, incluindo **4 arquiteturas híbridas**. | — |
| Algumas **lacunas** identificadas: a primeira é a **ausência de validação cruzada** de forma geral na modelagem desses sistemas. A maioria usa partição única, que ignora a estrutura dos grupos experimentais. | ✅ **"Validação cruzada estruturada" corrigido para "validação cruzada em geral"** — o problema não é ser não-estruturada, é a ausência de validação cruzada. |
| A segunda lacuna é a **seleção de modelos** baseada apenas em valores absolutos de métricas de erro, como RMSE, sem considerar a **margem estatística inerente**. Isso acaba favorecendo modelos desnecessariamente complexos. | — |
| A terceira é que modelos híbridos são **praticamente inexistentes** especificamente para V-AGMD com air gap. | — |
| As **contribuições** deste trabalho são: implementação de **validação cruzada estruturada por regime de salinidade** (treino em 2 regimes, teste no terceiro); uso de **critério de seleção** que considera o erro da estimativa da métrica para favorecer modelos menos complexos; e **experimentação inédita** de 4 arquiteturas híbridas físico-dados aplicadas ao V-AGMD. | — |

---

## 10. Sumário da Apresentação / Transição

| Fala | Ações do Chat |
|------|---------------|
| A apresentação está dividida em **5 blocos**. Vamos agora para a **fundamentação teórica**. | — |

---

## 11. Princípios da Destilação por Membranas

| Fala | Ações do Chat |
|------|---------------|
| Aqui estão os princípios que regem a destilação por membranas, focando nesta arquitetura específica. Você tem **dois fluxos principais**: um fluxo de **água quente** e um fluxo de **água fria**, separados por uma **membrana** e um **air gap**. | ✅ **Explicação das vantagens adicionada ao slide**: esta tecnologia opera em **temperaturas médias** (60-80°C), é compatível com **calor residual** de processos industriais, e funciona muito bem acoplada a **projetos de cogeração**. Isso a torna ideal para integração com fontes renováveis e sistemas de aproveitamento energético. |
| A membrana é **hidrofóbica** — ela só permite a passagem de **vapor**. A diferença de temperatura entre os dois lados gera um **gradiente térmico**, que aumenta a pressão de vapor do lado quente, fazendo com que as moléculas de água evaporem e atravessem a membrana. | — |
| O **air gap** funciona como **isolante térmico** — o ar é um ótimo isolante, então impede a troca de calor entre os dois lados, tornando o sistema energeticamente eficiente. | — |
| O **vácuo parcial** é aplicado para compensar o impedimento ao transporte de massa causado pelo air gap, incentivando o fluxo de vapor. | — |

---

## 12. Modelo Físico — Três Níveis

| Fala | Ações do Chat |
|------|---------------|
| É importante distinguir **três níveis** de modelos físicos na literatura. Os **modelos distribuídos** (1D, CFD 2D) discretizam o módulo em dezenas de segmentos, resolvendo equações em cada ponto — capturam perfis espaciais mas têm alto custo computacional. | — |
| Os **modelos de balanços globais** aplicam balanços de massa e energia em estado estacionário sem discretizar o domínio. | — |
| E os **modelos reduzidos 0D**, como o de Lisboa (2024) usado neste trabalho, tratam o módulo como um volume único com grandezas médias. Não resolvem equações diferenciais, apenas balanços globais e relações algébricas — custo computacional baixo, mas perdem detalhes como gradientes axiais e polarização térmica. | — |

---

## 13. Fundamentos de Aprendizado de Máquinas

| Fala | Ações do Chat |
|------|---------------|
| O aprendizado de máquina, de forma geral, é voltado ao **aprendizado a partir dos dados**, identificando padrões e relações. | ✅ **Tabela de fundamentos reorganizada**: foi incorporada a linha de ML com uma **terceira coluna de "propósito"** no contexto da tarefa de regressão, explicando o papel de cada conceito. ✅ **Definição formal de ML** verificada nas referências (Ghahramani, 2015). |
| Aprendizado de máquina se divide em dois ramos principais: **regressão** e **classificação**. Em **regressão**, temos uma função real Y que queremos aproximar por uma função f(X), sempre com um erro associado. O objetivo é **minimizar esse erro**. | — |
| As métricas utilizadas: a **Raiz do Erro Quadrático Médio (RMSE)** mede o somatório dos erros com penalização para erros maiores. O **Coeficiente de Determinação (R²)** varia de 0 a 1 — mas, na biblioteca utilizada (scikit-learn), ele pode ser **negativo** quando o modelo tem **viés elevado**. | ✅ **MAE (Erro Absoluto Médio) removido** do slide — mantidos apenas RMSE e R². ✅ **Explicação do R² negativo**: o scikit-learn calcula R² como `1 - (S_res / S_tot)`, onde S_res é a soma dos resíduos ao quadrado e S_tot é a soma total ao quadrado. Se o modelo tem viés sistemático (como o modelo 0D para as temperaturas), S_res pode ser **maior que S_tot**, resultando em R² negativo. |
| Sobre a **divisão dos dados**: no treinamento de um modelo de regressão, dividimos os dados em conjuntos de **treinamento**, **validação** e **teste**. O treino ajusta os parâmetros; a validação orienta a escolha de hiperparâmetros; o teste avalia o desempenho final em dados não vistos. | ✅ **Linha "divisão dos dados" separada da "validação cruzada"** no slide, com propósito explicado claramente: "Divisão = separar treino/validação/teste; Validação Cruzada = repetir a divisão múltiplas vezes para obter estimativa robusta do erro." |
| **Pré-processamento dos dados**: o **Z-score** centraliza cada variável subtraindo a média e dividindo pelo desvio padrão, colocando todas em escala comparável. Isso evita que variáveis com magnitudes maiores dominem desproporcionalmente o ajuste do modelo. | ✅ **Definição de pré-processamento adicionada**: "Etapa que transforma os dados brutos em formato adequado para o modelo, garantindo que diferenças de escala ou distribuição entre variáveis não distorçam o aprendizado." |

---

## 14. Famílias de Modelos

| Fala | Ações do Chat |
|------|---------------|
| **Quatro famílias** de modelos foram comparadas. **Modelos lineares** servem como referência — incluem OLS, Ridge, Lasso e ElasticNet. **Árvores de decisão** — Random Forest e Gradient Boosting — capturam relações não lineares. | — |
| **Redes neurais** — MLP do sklearn e KerasMLP — têm alta flexibilidade. E os **híbridos** combinam física com dados: PhyInput, PhyResidual, PhyHybrid e PhyLoss. | — |

---

## 15. Visão Geral dos Procedimentos

| Fala | Ações do Chat |
|------|---------------|
| Visão geral dos procedimentos: começo com os **dados experimentais**, realizo etapas de **preparação dos dados** — padronização, análise de correlações. Depois a **análise exploratória** calcula as correlações de Pearson e Spearman para avaliar relações entre variáveis. | ✅ **"Pipeline" renomeado para "Visão Geral dos Procedimentos"** — termo mais didático que não requer explicação adicional. |
| A modelagem segue **3 estágios** de complexidade crescente: **Stage 0** com modelos clássicos (regressões lineares e árvores de decisão), **Stage 1** com redes neurais (baseline) e **Stage 2** com arquiteturas híbridas. | ✅ **"Baseline Keras" renomeado para "Redes Neurais"** no fluxograma. ✅ **"Definindo Validação" removido** do fluxograma da visão geral. ✅ **"Selecionado / 0D / Redes" simplificado** para "Selecionado vs 0D". |
| Finalmente, o modelo selecionado é comparado com o **modelo físico 0D**. | — |

---

## 16. Dados Experimentais

| Fala | Ações do Chat |
|------|---------------|
| São **174 pontos experimentais**, **3 regimes de salinidade**: 10, 40 e 70 g/L de NaCl. **5 entradas**: temperatura de alimentação, temperatura de refrigeração, vazão de refrigeração, pressão de vácuo e concentração de sais. **3 saídas**: fluxo de permeado, temperatura de saída da alimentação, temperatura de saída do refrigeração. | — |

---

## 17. Decisões da Preparação dos Dados

| Fala | Ações do Chat |
|------|---------------|
| **Escalonamento**: foi escolhido o **Z-score**. Ele preserva a distribuição original dos dados, medindo em desvios-padrão. | ✅ **Justificativa do Z-score tornada mais didática**: "Preserva a distribuição original; mede cada ponto em número de desvios-padrão da média, sem compressão artificial causada por valores extremos." ✅ Menção ao MinMax **removida** do slide de apresentação (pode ficar no anexo). |
| **Validação**: foi usado **GroupKFold**, que separa os folds por regime operacional. Isso orienta a busca de hiperparâmetros para capacidade de extrapolação. | ✅ **Features/Binning (2.3) removido** dos slides da visão geral — movido para **tabela no anexo** do material suplementar. |

---

## 18. Esquema de Validação Cruzada

| Fala | Ações do Chat |
|------|---------------|
| O esquema geral: para cada **Fold**, você treina em **2 regimes** e testa no **terceiro**. São **3 combinações** possíveis, gerando **3 valores de RMSE**. A **média desses 3 RMSEs** com seu **erro associado** (desvio padrão) é o que define a decisão sobre os hiperparâmetros. | ✅ **Novo slide de critério de seleção adicionado** com imagem/diagrama explicando o fluxo completo: Validação Cruzada → RMSE CV médio com erro padrão → Critério 1-SE → Seleção do modelo mais simples dentro de 1 erro padrão do melhor. |
| A partir dessa métrica média com seu erro associado, aplica-se o **critério 1-SE**: se vários modelos têm RMSE dentro de 1 erro padrão do melhor, escolhe-se o **mais simples**. | — |

---

## 19. Busca de Hiperparâmetros

| Fala | Ações do Chat |
|------|---------------|
| Para cada **variável de saída**, fiz uma **busca de hiperparâmetros personalizada**. Isso significa que para cada modelo, tenho **3 fits diferentes** — um para cada target (Alim_T_out, Ref_T_out, Fluxo). | ✅ **Tabela resumida da busca de hiperparâmetros adicionada** aos slides principais: cada família com seus parâmetros buscados (ex: lineares → alpha; árvores → profundidade; neurais → camadas + LR + L2). ✅ **Tabela completa da busca original movida para o anexo**. |

---

## 20. Resultados — Modelos Lineares

| Fala | Ações do Chat |
|------|---------------|
| Aqui os resultados dos modelos lineares. Para cada target, vemos tanto o **RMSE de validação cruzada** quanto o **RMSE de teste**. | ✅ **Coluna de diferença CV/teste removida** das tabelas — mantida apenas uma coluna com RMSE de teste para seleção, mais o RMSE de CV como referência complementar. ✅ **Nova coluna com RMSE de CV adicionada** para permitir análise complementar. |

---

## 21. Árvores de Decisão — Eliminadas

| Fala | Ações do Chat |
|------|---------------|
| As árvores de decisão **não foram os melhores resultados** para nenhum dos parâmetros de saída. Foram eliminadas da corrida, restando a avaliação entre o melhor modelo de **regressão linear**, a **rede neural baseline** e os **híbridos**. | — |

---

## 22. Resultados — Análise por Variável de Saída

| Fala | Ações do Chat |
|------|---------------|
| Para **Alim_T_out**, o melhor modelo foi a **rede neural (baseline Alim)**, mas totalmente comparável com a regressão linear — o que indica uma relação aproximadamente linear. | ✅ **Slides de tabela geral + análise por variável consolidados**: foi criada uma **mini-tabela** com apenas as **3 linhas vencedoras** (uma por target), com comentários laterais descritivos. |
| Para **Ref_T_out**, o melhor foi o **Ridge (regressão linear)**. Novamente, performances muito comparáveis entre os modelos. | ✅ **Porcentagens de diferença calculadas** entre vencedores e segundos colocados, adicionadas à tabela. |
| Para **Fluxo**, foi o único que teve performance melhor no modelo **híbrido (PhyResidual)** — a principal demonstração mensurável da vantagem da incorporação da física. | ✅ **Análise de fluxo simplificada**: removida menção a "generalização mais estável", mantida apenas a frase sobre a demonstração mensurável da vantagem da hibridização. |

---

## 23. Arquiteturas Híbridas — Explicação

| Fala | Ações do Chat |
|------|---------------|
| As arquiteturas híbridas combinam o **modelo físico 0D** com redes neurais. A rede neural **aprende correções sistemáticas** — como o viés de aproximadamente **1,58°C** que o modelo 0D tem para a temperatura de alimentação. O modelo físico representa os acoplamentos fenomenológicos de forma interpretável, e a rede corrige o que o modelo simplificado não consegue capturar. | ✅ **Termo "fenomenológico" substituído** por "conhecimento da física" — mais acessível para apresentação oral. ✅ **Texto sobre "papel de corretor de viés" simplificado**: "Este papel de corretor de viés é a principal contribuição mensurável da arquitetura residual." |
| Este papel de **corretor de viés** é a principal contribuição mensurável da arquitetura residual. Estudos auxiliares adicionais com novos pontos experimentais fora deste regime poderiam avaliar se a arquitetura híbrida realmente auxilia na extrapolação verdadeira. | ✅ **Slide de contribuições e trabalhos futuros: contribuições removidas** — ficou apenas o slide de **trabalhos futuros**, eliminando a necessidade de reduzir a fonte. |

---

## 24. Comparação Final

| Fala | Ações do Chat |
|------|---------------|
| Comparação final: **PhyResidual (base Alim)** foi o melhor para **fluxo** e **temperatura de alimentação**. **PhyHybrid (base Alim)** venceu para **temperatura de saída do refrigeração**. A seleção foi feita pelo **critério 1-SE entre famílias**, priorizando o modelo mais simples dentro de 1 desvio padrão do melhor. | — |
| O **modelo 0D** tem R² negativo para Alim_T_out, demonstrando que há um viés sistemático que o modelo simplificado não captura, mas que as arquiteturas híbridas conseguem corrigir. | — |

---

## 25. Conclusões

| Fala | Ações do Chat |
|------|---------------|
| Conclusões principais: o **PhyResidual** vence para fluxo e temperatura de alimentação; o **PhyHybrid** vence para temperatura de saída. Para as temperaturas, tanto a rede neural quanto a regressão linear tiveram performances muito parecidas — diferenças sutis, com uma levemente melhor para cada target. | ✅ **Análise das temperaturas unificada** em um único comentário, eliminando redundância entre slides. |
| Para o **fluxo**, o ganho do PhyResidual foi a principal demonstração da vantagem da hibridização: corrigir o viés dos modelos data-driven usando a física como referência. | ✅ **Menção ao resultado de CV vs Teste removida** da conclusão oral (já está na tabela). |
| Como **trabalhos futuros**: substituir o modelo **0D pelo modelo 2D** já disponível no laboratório como referência física; construir **PINNs a partir das EDOs do modelo 2D**, tanto como surrogate (aceleração de processamento) quanto com função de perda incluindo dados experimentais. | ✅ **Contribuições removidas** do slide (era redundante com os slides anteriores). ✅ **Correção multiplicativa (artigo 16) movida para o anexo** com explicação mais detalhada. ✅ **Bullet point redundante sobre modelo residual removido**. ✅ **Novos dados experimentais removido** dos trabalhos futuros (não é prioridade). |
| | ✅ **PINNs reformuladas**: deixar claro que a sugestão é construir PINNs a partir das EDOs do modelo 2D, tanto como surrogate (apenas física, sem dados) quanto no modo que também incorpora dados experimentais na função de perda. |

---

## Notas Adicionais

| Instrução | Ação |
|-----------|------|
| Diminuir fonte do slide de contribuições e trabalhos futuros | ✅ **Resolvido removendo o slide de contribuições** — só trabalhos futuros, sem necessidade de diminuir fonte. |
| Criar anexo com resultados KFold vs GroupKFold | ✅ **Adicionado ao material suplementar** (capítulo 6) — demonstrando que o CV do GroupKFold é mais rigoroso que o KFold comum, e que o teste final (holdout) é mais fácil que ambos. |
| Verificar definição de R² negativo nas referências | ✅ **Pesquisado**: R² negativo no scikit-learn ocorre quando o modelo é pior que uma predição constante da média. O cálculo é `1 - (S_res / S_tot)`, e S_res pode ser maior que S_tot quando o modelo tem viés elevado. |
| Pesquisar imagens de melhor qualidade para modelos lineares e árvores | ✅ **Imagens geradas**: `lineares_arvores.png` e `redes_neurais.png` em `tcc_images/chap02a/` com diagramas didáticos padronizados. |
| Adicionar explicação de regularizações L1/L2 nos slides | ✅ **Diagrama das regularizações adicionado** junto com a imagem dos modelos lineares — L1 (Lasso) força coeficientes a zero; L2 (Ridge) reduz coeficientes sem zerar. |
