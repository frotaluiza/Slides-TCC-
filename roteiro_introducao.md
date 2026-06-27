# Roteiro de Apresentação — Introdução (~6 min)

## Slide 1: A Crise Global da Água (~1 min)

"Bom dia/tarde a todos. Vou começar com um dado que chama atenção: atualmente, **4 bilhões de pessoas** enfrentam escassez severa de água pelo menos um mês por ano — isso é mais da metade da população mundial. Desses, **2,2 bilhões** não têm acesso a água potável segura, e **1,7 bilhão** consome água de fonte contaminada, segundo a OMS. A Organização Mundial da Saúde estima que cerca de **1 milhão de mortes por ano** estão associadas a doenças transmitidas por água contaminada. A projeção é que a demanda global por água **supere a oferta em 40% até 2030**, segundo a IDRA. É natural imaginar que, diante desse cenário, a demanda por tecnologias de dessalinização cada vez mais eficientes deve crescer significativamente."

**Fontes:**
- Mekonnen & Hoekstra (2016) — artigo científico sobre escassez hídrica global
- WHO (2023) — relatório da Organização Mundial da Saúde
- IDRA (2026) — International Desalination and Reuse Association

---

## Slide 2: O Problema no Brasil (~1,5 min)

"Contextualizando para o Brasil, 2026 foi um ano particularmente desafiador: chuvas abaixo da média histórica, com o sistema Cantareira operando com cerca de **30% da capacidade**, segundo dados da **ANA** — Agência Nacional de Águas e Saneamento Básico — reportados pela **CNN Brasil**.

No **Nordeste**, a realidade é estrutural: aproximadamente **4 meses de chuva concentrada** contra **8 meses de seca extrema** por ano, também segundo a ANA. Essa é a região que mais sofre com a escassez no país.

**Em contrapartida**, a **CNI** — Confederação Nacional da Indústria — divulgou um estudo mostrando que a **dessalinização pode reduzir o custo da água em até 10 vezes**, para valores entre R$ 2,63 e R$ 4,21 por metro cúbico. **[Pesquisa pendente:** preciso revisitar esse estudo para entender exatamente como a CNI calcula essa redução — se é por ganho de escala, avanço tecnológico, ou comparação com fontes alternativas como carro-pipa.] A maior planta do Brasil, no Espírito Santo, já atende uma demanda equivalente a **80 mil pessoas**. E com **8.500 km de costa**, o potencial de expansão no país é enorme."

**Fontes:**
- **ANA:** Agência Nacional de Águas e Saneamento Básico
- **CNN Brasil:** canal de notícias que reportou os dados da ANA
- **CNI:** Confederação Nacional da Indústria — estudo de 2026
- **IBGE:** dados litorâneos

---

## Slide 3: Dessalinização — Realidade Global (~45 s)

"A dessalinização não é uma promessa futura — **já é realidade consolidada** no mundo todo. A Arábia Saudita produz **86% do seu abastecimento** por dessalinização (12,5 milhões de m³/dia). Em Israel, **80% da água produzida** vem de dessalinização. Mais de **150 países** utilizam a tecnologia, atendendo cerca de **300 milhões de pessoas**, segundo o Banco Mundial.

No Brasil, um case de sucesso é **Fernando de Noronha**, onde a dessalinização aumentou a oferta de água em **122%** e eliminou o racionamento. Um dado importante da CNI: a dessalinização permite que a indústria **desvincule seu crescimento da oferta limitada de água doce**, ganhando autonomia hídrica."

**Fontes:** CNI (2026), Banco Mundial

---

## Slide 4: Ilha de Policogeração Sustentável (~1,5 min)

"Este trabalho está inserido em um projeto maior: a **Ilha de Policogeração Sustentável**, desenvolvida pelo LabMEMS da COPPE/UFRJ e inaugurada em 2022. **[Pesquisa pendente:** ler artigo do Lisboa 2024 sobre o projeto para enriquecer a explicação com detalhes operacionais.]

A ilha é um protótipo pioneiro que integra **geração de energia solar térmica de alta concentração** com um **dessalinizador V-AGMD**. Ela produz:
- **5 kW elétricos** — o suficiente para abastecer cerca de **25 residências**
- **8 kW térmicos** recuperáveis em micro-trocadores de calor
- **1.000 litros de água destilada por dia** — capacidade para atender mais de **100 pessoas**

O foco do projeto são **comunidades remotas e off-grid**: semiárido nordestino, ilhas, áreas de operação de óleo e gás, e regiões de desastre. O projeto está alinhado com os **ODS 6** (água potável), **ODS 7** (energia limpa) e **ODS 13** (ação climática)."

**Fontes:** COPPE/UFRJ (2022); Lisboa et al. (2024)

---

## Slide 5: Foto da Instalação (~20 s — opcional)

"Essa é uma imagem da instalação piloto, mostrando os painéis solares de concentração e o módulo de dessalinização."

**Fonte:** SEIXO (2024)

---

## Slide 6: V-AGMD — Inovação Tecnológica (~1 min)

"A tecnologia central é a **destilação por membrana (MD)**, que combina um processo térmico com uma membrana hidrofóbica: o vapor de água atravessa a membrana impulsionado por uma diferença de temperatura — não por alta pressão como na osmose reversa.

A configuração usada aqui é a **V-AGMD** (Vacuum-Enhanced Air Gap Membrane Distillation), que adiciona **vácuo parcial na lacuna de ar** entre a membrana e a superfície de condensação, aumentando significativamente o fluxo de permeado.

A grande inovação é que o sistema pode operar com **calor solar ou residual**, sem demandar altas pressões. O **desafio** que motiva este trabalho: modelar esse sistema com dados experimentais limitados (174 amostras) para permitir otimização e operação autônoma."

**Fontes:** CATH (2010); WARSINGER (2017); YADAV et al. (2021)

---

## Slide 7: Motivação e Objetivos (~1 min)

"A motivação é clara: um modelo preditivo confiável permite otimizar a operação do dessalinizador, reduzir experimentos caros e viabilizar a operação autônoma em comunidades remotas.

**Objetivo geral:** avaliar estratégias de modelagem — desde regressões lineares até arquiteturas híbridas — para predizer o desempenho do V-AGMD.

**Objetivos específicos:**
1. Estruturar os dados com separação por regimes experimentais
2. Comparar 4 famílias de modelos: lineares, árvores, redes neurais e híbridas
3. Aplicar validação cruzada por grupos (GroupKFold)
4. **Selecionar modelo por desempenho, validação e complexidade, buscando minimizar sobreajuste nos dados**"

---

## Slide 8: Organização da Apresentação (~20 s)

"A apresentação está dividida em 5 blocos:
1. Introdução (que estamos vendo agora)
2. Fundamentação teórica
3. Metodologia proposta
4. Resultados
5. Conclusões e contribuições"
