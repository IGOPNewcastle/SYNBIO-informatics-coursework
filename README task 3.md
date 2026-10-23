# Task 3 — Virtual PCR simulator: temperature × polymerase quantity

## Aim

Evaluate how annealing temperature (63°C or 73°C) and polymerase quantity
(1 U or 2 U) influence simulated PCR yield and purity.

This is a **2 × 2 factorial design** with **three simulator replicates per
condition** (12 factorial runs). One separate confirmation run was conducted
at the selected condition. A baseline value at 68°C and 1 U was supplied
in the coursework table, but is **not in the provided CSV dataset**.

## Files

* `data/PCR\_simulation\_runs.csv` — 12 factorial results plus confirmation run 13.
* `data/PCR\_summary.csv` — mean and sample SD (`ddof=1`), excluding confirmation.
* `code/task3\_pcr\_analysis.py` — runnable analysis and figure generation.
* `figures/PCR\_Interaction\_Plot.png` — two-panel mean ± sample SD plot.
* `appendix/METHODS\_AND\_RESULTS.md` — source data, numerical results, interpretation.
* `appendix/PROVENANCE\_AND\_LIMITATIONS.md` — provenance and limitations.

## Reproduce

From the `Task\_3\_GitHub` directory, run:

```bash
python code/task3\_pcr\_analysis.py
```

Dependencies: NumPy and Matplotlib. The script reads the CSV and regenerates
the summary CSV and PNG. No random seed is necessary because the script
analyses fixed observations; it does not simulate new random runs.

## Results

|Condition|Temperature|Polymerase|Yield mean ± SD (ng/µL)|Purity mean ± SD (%)|
|-|-:|-:|-:|-:|
|A|63°C|1 U|0.1333 ± 0.0577|11.3667 ± 0.1528|
|B|63°C|2 U|0.2000 ± 0.0000|12.4667 ± 0.2082|
|C|73°C|1 U|0.1000 ± 0.0000|10.2667 ± 0.2082|
|D|73°C|2 U|0.1000 ± 0.0000|11.1000 ± 0.2646|

**Selected condition:** B (63°C, 2 U), highest mean yield and purity
among the four tested conditions. The independent confirmation run gave
0.2 ng/µL yield and 12.7% purity.

## Interpretation

The lines are non-parallel for yield: increasing polymerase from 1 to 2 U
raises mean yield at 63°C but not at 73°C. Purity is higher at 2 U at
both temperatures. These are descriptive simulator results, **not evidence
of statistically significant effects or performance in a physical PCR lab**.

## Simulator

[Virtual PCR simulator](https://virtual-pcr.ico2s.org/pcr/).
Fellermann et al. (2019) are cited in the coursework description; verify
the complete bibliographic citation against the assigned reading.

## Review status

The coursework team reports that human review, partner verification and
reruns are complete. These are not outstanding tasks.

