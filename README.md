# Carbonation–CCU System Dynamics model (IS2H4C, Basque Hub)

System Dynamics model of a CCU-enabled circular material flow in the Basque Hub: CO₂ captured at an industrial source is used to carbonate pretreated steel slag in a pilot reactor, and the carbonated product is supplied to the cement sector. The model represents slag availability, reactor capacity, CO₂ availability, product storage and delivery, and reports operational, environmental and cost indicators at weekly resolution.

The model was developed in Work Package 4 of the IS2H4C project and is documented in Deliverable D4.3 *Hub logistics and supply chain management*, Section 5.2 and Appendix 1.

## Repository contents

```
carbonation_model/
├── README.md
├── LICENSE
├── CITATION.cff
├── inputs/
│   └── parameters_and_sources.xlsx           Parameters, values, units and sources
├── model/
│   ├── carbonation_baseline.mdl              Baseline model (Vensim)
│   └── baseline_model_results.xlsx           Baseline indicators (D4.3, Tables 17–18, Figure 16)
├── verification_scenarios/
│   └── verification_scenarios_summary.xlsx   Scenarios S1–S4 (D4.3, Section 5.2.5, Tables A1.1–A1.4, Figure 17)
└── validation_scenarios/
    ├── BV1/                                  Future market uptake and resource availability
    ├── BV2/                                  Production and logistics capacity requirements
    └── BV3/                                  Carbon regulation and economic viability
```

Each Excel workbook follows the same layout:

- **Parameters**: values used in the tables and figures, with sources;
- **Vensim_\***: simulation results exported from Vensim;
- **Tables**: tables of the deliverable, calculated with formulas from the Vensim sheets;
- **Figures**: figures of the deliverable.

Colour code: blue = input or Vensim data, black = formula, green = link to another sheet.

## Requirements

The `.mdl` files open with Vensim [version to be added] (Ventana Systems). The free Vensim PLE can open and run the models. The Excel workbooks need no additional software.

Simulation output files (`.vdfx`) are not included. All results can be reproduced with the models and the settings below, and the values used in the deliverable are stored in the Excel workbooks.

## Reproducing the results

All runs use a weekly time step.

| Scenario | Model | Settings | Horizon / reading time | Workbook |
|---|---|---|---|---|
| Baseline | `model/carbonation_baseline.mdl` | Parameters as in `inputs/parameters_and_sources.xlsx` | 100 weeks | `model/baseline_model_results.xlsx` |
| S1 — Increased reactor capacity | `model/carbonation_baseline.mdl` | Reactor useful volume = 0.1, 0.25, 0.5, 1 m³ (baseline 0.0217) | Week 100 | `verification_scenarios/verification_scenarios_summary.xlsx` |
| S2 — Increased product demand | `model/carbonation_baseline.mdl` | Adoption rate = 0.1, 0.5, 0.6 (baseline 0.3) | Week 100 | idem |
| S3 — Increased demand and slag | `model/carbonation_baseline.mdl` | Cement demand = 10,000 kg/week; slag supply = 350, 700, 1,750, 3,500 kg/week | Week 100 | idem |
| S4 — Reduced CO₂ availability | `model/carbonation_baseline.mdl` | CO₂ diverted fraction = 0.25, 0.5, 0.75, 0.9, 0.92, 0.94, 0.95, 0.96, 0.98 (baseline 0) | Week 100 | idem |
| BV1 — Market uptake | `validation_scenarios/BV1/carbonation_BV1.mdl` | Grid: hub market share = 0.005%, 0.01%, 0.05% × useful granulometry fraction = 4%, 8%, 16%. Pathway: demand ×2 at week 52 and ×5 at week 104 | 156 weeks | `BV1_results_summary.xlsx` |
| BV2 — Capacity requirements | `validation_scenarios/BV2/carbonation_BV2.mdl` and `carbonation_BV2_anticipated_design.mdl` | Constant demand (C1–C3: operating hours 45, 90, 105 h/week; storage 3,600, 7,200, 9,200 kg) and step demand with capacity expanded at the step (S1) or four weeks earlier (S2) | 156 weeks | `BV2_results_summary.xlsx` |
| BV3 — Economic viability | `validation_scenarios/BV3/carbonation_BV3.mdl` | Case C2 of BV2 at steady state; operating costs and carbon prices calculated in the workbook | 156 weeks | `BV3_results_summary.xlsx` |

The exact settings of each run are listed in the Parameters sheet of each workbook.

## Data and limitations

Input data come from the Basque Hub partner (data request and technical note), the literature and public statistics. All sources are listed in `inputs/parameters_and_sources.xlsx`. The original partner documents are not included in this repository.

The model is a pilot-scale representation for exploring operating regimes and bottlenecks. Its results are illustrative and do not constitute a validated industrial design. Limitations are discussed in D4.3, Section 5.2.8.

## How to cite

Please cite this repository as indicated in `CITATION.cff` or on its Zenodo page (DOI: [to be added]).

## Funding

This work was carried out within the IS2H4C project (*Sustainable Circular Economy Transition: From Industrial Symbiosis to Hubs for Circularity*), funded by the European Union under grant agreement No 101138473. Views and opinions expressed are however those of the author(s) only and do not necessarily reflect those of the European Union or HADEA. Neither the European Union nor the granting authority can be held responsible for them.

## Licence

[Licence to be added; see `LICENSE`.]

## Contact

Beatriz Royo, Zaragoza Logistics Center (ZLC).
