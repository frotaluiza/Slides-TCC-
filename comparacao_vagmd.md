# Comparação: Trabalhos de Modelagem Preditiva em V-AGMD/AGMD

| # | Paper | Abordagem | Tecnologia | Modelo | Variáveis preditas |
|---|-------|----------|-----------|-------|-------------------|
| 1 | Kim et al. (2022) | Data-driven | V-AGMD | MLR, GNN, MLFNN | Fluxo |
| 2 | Requena et al. (2023) | Data-driven | V-AGMD | ANN (MLP 4:2:2) | SRF, MLR |
| 3 | **Lisboa et al. (2024)** | Física | V-AGMD | Modelo 0D reduzido | Fluxo, T$_{out\_alim}$, T$_{out\_ref}$ |
| 4 | Andrés-Mañas (2023) | Física | V-AGMD | 1os princípios | Fluxo, T$_{out}$, GOR, SEC |
| 5 | Abdulrahim (2026) | Híbrido | AGMD | CFD→ANN surrogate | Fluxo, STEC |
| 6 | Khayet (2012a) | Data-driven | AGMD | Feed-forward ANN | Fluxo, rejeição |
| 7 | Shirazian (2017) | Data-driven | AGMD | ANN + PSO | Fluxo, GOR, T$_{out}$ |
| 8 | Yang (2023) | Data-driven | AGMD | MLR, BP-ANN, RBF-ANN | Fluxo, GOR |
| 9 | Jawed (2025) | Data-driven | AGMD (foto) | ANN + GA | Fluxo |
| 10 | Khalifa (2017) | Otimização | AGMD | Físico + ACO/PSO | Fluxo |
| — | **🔥 Este trabalho** | **Híbrido** | **V-AGMD** | **4 famílias + 4 híbridas** | **Fluxo, T$_{out\_alim}$, T$_{out\_ref}$** |

## Principais conclusões

1. **Apenas 5 papers** modelam V-AGMD — e nenhum com validação cruzada por grupos
2. **Só 2 papers** (Kim 2022, Yang 2023) comparam múltiplos modelos — mas sem CV adequada
3. **Nenhum paper** usa arquiteturas híbridas residuais (ZohanResidual, HRNN) para V-AGMD
4. **Seu trabalho é o único** que prediz **simultaneamente** fluxo + T_out_alim + T_out_ref
5. Seu trabalho é o único com **GroupKFold por regimes experimentais**

## Legenda de abreviações

**Modelos:**
| Abrev. | Significado |
|--------|-------------|
| MLR | Multiple Linear Regression (regressão linear múltipla) |
| GNN | Generalized Neural Network |
| MLFNN | Multi-Layer Feed-Forward Neural Network |
| ANN | Artificial Neural Network (rede neural artificial) |
| MLP | Multi-Layer Perceptron (perceptron multicamadas) |
| BP-ANN | Back-Propagation ANN (retropropagação) |
| RBF-ANN | Radial Basis Function ANN (função de base radial) |
| RSM | Response Surface Methodology (metodologia de superfície de resposta) |
| PSO | Particle Swarm Optimization (otimização por enxame de partículas) |
| GA | Genetic Algorithm (algoritmo genético) |
| ACO | Ant Colony Optimization (otimização por colônia de formigas) |
| DT | Decision Tree (árvore de decisão) |
| RF | Random Forest (floresta aleatória) |
| SVM | Support Vector Machine |
| CFD | Computational Fluid Dynamics (dinâmica dos fluidos computacional) |

**Tecnologias MD:**
| Abrev. | Significado |
|--------|-------------|
| V-AGMD | Vacuum-Enhanced Air Gap Membrane Distillation |
| AGMD | Air Gap Membrane Distillation |
| VMD | Vacuum Membrane Distillation |
| DCMD | Direct Contact Membrane Distillation |
| SGMD | Sweeping Gas Membrane Distillation |

**Variáveis preditas:**
| Abrev. | Significado |
|--------|-------------|
| SRF | Salt Rejection Factor (fator de rejeição de sais) |
| MLR | Membrane Leak Ratio (taxa de vazamento da membrana) |
| GOR | Gained Output Ratio (razão de ganho de saída) |
| SEC | Specific Energy Consumption (consumo específico de energia) |
| STEC | Specific Thermal Energy Consumption |
| T_out | Temperatura de saída |
| T_out_alim | Temperatura de saída da alimentação |
| T_out_ref | Temperatura de saída do resfriamento |

## Referências completas
- Kim et al. (2022) — Membr. Water Treat. — V-AGMD
- Requena et al. (2023) — Membranes 13(11), 857 — V-AGMD
- Andrés-Mañas et al. (2022) — Desalination — V-AGMD (caracterização)
- Andrés-Mañas et al. (2023) — Desalination — V-AGMD (modelo físico)
- Lisboa et al. (2024) — Sep. Purif. Technol. 350, 127891 — V-AGMD
- Abdulrahim et al. (2026) — Desalination — AGMD (CFD surrogate)
