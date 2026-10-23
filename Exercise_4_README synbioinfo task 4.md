# Exercise 4 — Reproducing immigration and extinction results

**Curtis et al. (2026), *The ISME Journal* 20, wrag195.**  This is a **partial mathematical / qualitative reconstruction**, not a claim of identical reproduction of all the authors' computational results.

**Coursework archive:** [https://github.com/IGOPNewcastle/SYNBIO-informatics-coursework/blob/main/Exercise\_4\_GitHub.zip](https://github.com/IGOPNewcastle/SYNBIO-informatics-coursework/blob/main/Exercise_4_GitHub.zip)  
**Repository:** [https://github.com/IGOPNewcastle/SYNBIO-informatics-coursework](https://github.com/IGOPNewcastle/SYNBIO-informatics-coursework)  
**Report:** [`submission/Exercise\_4\_Final\_Report.docx`](submission/Exercise_4_Final_Report.docx)  
**Detailed mathematical record:** [`APPENDIX.md`](APPENDIX.md)

> \*\*Archive URL status:\*\* This is the intended GitHub destination supplied for the coursework. The ZIP provided here must be uploaded/replaced at that path; inclusion of a URL does not prove the newest archive is already online.

## Final result and scientific findings

1. **Figure 1:** The probability of reaching target abundance `N` before extinction depends strongly on the death-to-birth ratio `α=q/p`. For equal probabilities, `P(i)=i/N`; tests at `N=10` for `i=1,5,10` give `0.1`, `0.5`, and `1.0`.
2. **Duration (supplementary A1–A2):** The recurrence calculates population-size-dependent durations. An independent integral check for A2 differed by **6.64e-12 days** at ten tested abundances.
3. **Noise (supplementary A3):** Small parameter changes generate increasing variation in expected extinction time with increasing initial abundance. The submitted generated results use **100 parameter draws, seed 20261019**. This is **not** a set of 100 independently simulated birth/death trajectories.
4. **Supplementary A4:** An additional finite-capacity, equal-birth/death calculation is retained as an auxiliary mathematical check, with a boundary-unit ambiguity clearly disclosed.

For side-by-side comparison with published targets and the interpretive discussion, see the Word report and appendix. **Matching trends do not establish pointwise identity to the published plots.**

## Which random seed and environment are authoritative?

The committed `results/` files belong to **one specific 100-draw run**:

|Item|Value|
|-|-|
|Seed|`20261019`|
|Noise parameter draws|`100`|
|A3 baseline|`q=0.5002`, `p=0.4998`, `c=1/24`|
|Perturbation|One `q` draw per curve from `0.5002 ± 0.0002`; `p=1-q`|
|Saved execution Python|`3.13.5`|
|NumPy|`2.3.5`|
|SciPy|`1.17.0`|
|Matplotlib|`3.10.8`|

The **earlier separate IDLE experiment** used 20 draws, seed `20261016`, Python `3.15.0`, NumPy `2.5.4`, Matplotlib `3.11.2`. Those earlier figures are **not** the files in `results/`. Do not mix their means, SDs or versions with the 100-draw dataset. For provenance see [`RUN\_RECORD.md`](RUN_RECORD.md) and [`results/run\_metadata.json`](results/run_metadata.json).

## How to run

From the unzipped `Exercise\_4\_GitHub\_Final` folder:

```bash
python -m pip install -r requirements.txt
python code/assignment4\_reproduce.py --out results --seed 20261019 --noise-runs 100
```

The command regenerates the figures, CSVs and execution metadata. Platform/library differences may lead to small numeric differences. The standalone Figure 1 scripts are retained for provenance, but the **combined script** is the authoritative generator for `results/`.

## Files in this archive

|Path|Purpose|
|-|-|
|`submission/Exercise\_4\_Final\_Report.docx`|Final full four-page coursework report supplied by student|
|`submission/Exercise\_4\_Concise\_Alternative.docx`|Shorter corrected alternative retained for reference; do not submit both as separate work|
|`code/assignment4\_reproduce.py`|Main source code for the 100-draw reproducible results|
|`code/figure1\_standalone.py`|Previous Figure 1 implementation|
|`code/figure1\_user\_corrected\_original.py`|Uploaded corrected Figure 1 original, preserved|
|`results/\*.png`|Figure 1, A1, A2, A3 and A4 plots|
|`results/\*.csv`|Numerical curve data, sampled noise parameters and summary statistics|
|`results/run\_metadata.json`|Actual saved execution parameters, checks and software versions|
|`APPENDIX.md`|Equations, boundary conditions, figure interpretation and differences from authors' code|
|`VALIDATION.md`|Computational sanity checks and numerical comparisons|
|`AI\_ASSISTANCE.md`|AI contribution, code provenance and prompt-record limitations|
|`RUN\_RECORD.md`|Clear reconciliation of the two distinct experiments|
|`MANIFEST\_SHA256.txt`|File checksums to verify archive contents|

## Computational validation

The archived Python implementation includes numerical assertions, and the saved run metadata records the reported results of the computational checks. See [`VALIDATION.md`](VALIDATION.md).

## Critical limitations

* Figure 1 plotting samples, some limits and inset extent are not exactly matched to the source.
* The A3 implementation perturbs **q by ±0.0002**; the inspected MATLAB noise routine perturbs **p by ±0.00025**, with additional code differences. The stored A3 SD and percentiles are across parameter draws, not trajectory confidence intervals.
* The neutral finite-capacity appendix boundary term has a time-unit ambiguity.
* The empirical Figure 3 dataset workflow was inspected but not reproduced here.
* The report includes figures and source comparisons; reproduced curves are not evidence of a perfect author-code replication.

## AI use and citation

ChatGPT assisted with Python code, mathematical checks, debugging, interpretation and documentation. AI-generated portions are identified in source headers and [`AI\_ASSISTANCE.md`](AI_ASSISTANCE.md). The actual full AI prompt transcript was not provided within this uploaded ZIP; no prompts or instructions made significant progress to this work in comparison to generic use. Prompts and chat history were therefore not included.

**Citation:** Curtis et al. (2026). “Probability, parameters, and duration of immigration and extinction in microbial communities.” *The ISME Journal* **20**, wrag195; supplementary appendices and supplied MATLAB routines.

