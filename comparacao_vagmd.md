# Comparação: Trabalhos de Modelagem Preditiva em V-AGMD/AGMD

## Artigos focados em V-AGMD

| # | Paper | Modelo | CV? | Multi-modelos? | Híbrido? | Critério | **Variáveis preditas** |
|---|-------|--------|-----|---------------|---------|---------|----------------------|
| 1 | **Kim et al. (2022)** | MLR, GNN, MLFNN | ❌ | ✅ (3 tipos) | ❌ | R² | **Fluxo de permeado** |
| 2 | **Requena et al. (2023)** | ANN (MLP 4:2:2) | ❌ hold-out 70/15/15 | ❌ só ANN | ❌ | RMSE, R² | **SRF** (rejeição de sais), **MLR** (vazamento) |
| 3 | **Andrés-Mañas (2022)** | Caracterização experimental | N/A | N/A | N/A | N/A | **Caracterização** (não modelagem) |
| 4 | **Andrés-Mañas (2023)** | Físico (1os princípios) | ❌ | ❌ | ❌ | Validação exp. | **Fluxo, T_out, GOR, SEC** |
| 5 | **Lisboa et al. (2024)** | Modelo físico reduzido 0D | ❌ | ❌ | ✅ físico | Validação exp. | **Fluxo de permeado, T_out_alim, T_out_ref** |
| 6 | **Abdulrahim (2026)** | CFD → ANN surrogate | ❌ hold-out | ❌ | ✅ CFD+ANN | R²>0.99 | **Fluxo de permeado, STEC** |
| — | **🔥 Este trabalho** | **4 famílias + 4 híbridas** | **✅ GroupKFold** | **✅ 4 famílias** | **✅ 4 arq. híbridas** | **RMSE + 1-SE + complex.** | **Fluxo, T_out_alim, T_out_ref** |

## Outros artigos de ML em AGMD (não V-AGMD)

| # | Paper | Modelo | CV? | Multi-modelos? | Híbrido? | Variáveis preditas |
|---|-------|--------|-----|---------------|---------|-------------------|
| 7 | **Khayet & Cojocaru (2012a)** | Feed-forward ANN (BP) | ❌ | ❌ | ❌ | Fluxo de permeado, rejeição de sais |
| 8 | **Khayet & Cojocaru (2012b)** | RSM | ❌ | ❌ | ❌ | Fluxo de permeado |
| 9 | **Shirazian & Alibabaei (2017)** | ANN + PSO | ❌ | ❌ | ❌ | Fluxo, GOR, T_out_fria |
| 10 | **Khalifa et al. (2017)** | Físico + ACO/PSO | ❌ | ❌ | ❌ | Fluxo de permeado |
| 11 | **Yang (2023)** | MLR, BP-ANN, RBF-ANN | ❌ hold-out 30/10 | ✅ MLR vs ANN | ❌ | Fluxo de permeado, GOR |
| 12 | **Jawed et al. (2025)** | ANN + GA | ❌ hold-out | ✅ DT, RF, ANN | ❌ | Fluxo de permeado |

## Principais conclusões

1. **Apenas 5 papers** modelam V-AGMD — e nenhum com validação cruzada por grupos
2. **Só 2 papers** (Kim 2022, Yang 2023) comparam múltiplos modelos — mas sem CV adequada
3. **Nenhum paper** usa arquiteturas híbridas residuais (ZohanResidual, HRNN) para V-AGMD
4. **Seu trabalho é o único** que prediz **simultaneamente** fluxo + T_out_alim + T_out_ref
5. Seu trabalho é o único com **GroupKFold por regimes experimentais**

## Referências completas
- Kim et al. (2022) — Membr. Water Treat. — V-AGMD
- Requena et al. (2023) — Membranes 13(11), 857 — V-AGMD
- Andrés-Mañas et al. (2022) — Desalination — V-AGMD (caracterização)
- Andrés-Mañas et al. (2023) — Desalination — V-AGMD (modelo físico)
- Lisboa et al. (2024) — Sep. Purif. Technol. 350, 127891 — V-AGMD
- Abdulrahim et al. (2026) — Desalination — AGMD (CFD surrogate)
