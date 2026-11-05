# 3D PFM switching loops (vector SS-PFM)

Acquisition and analysis code for vector switching-spectroscopy PFM (3D PFM loops)
on an Asylum Research Cypher AFM. At each DC bias step the laser spot is moved
between positions on the cantilever, so the vertical and both in-plane
components of the piezoresponse are recorded along the switching loop.

This is the code used to acquire and analyse the data in the accompanying
manuscript (citation to be added on publication). The data are archived
separately on Zenodo (DOI to be added).

## Contents

| Folder | File | What it does |
|---|---|---|
| `acquisition/` | `Script Automated 3D PFM loops.ipynb` | Main acquisition notebook: single 3D loops and grids (maps) of 3D loops. Writes `OFF_Loops_Map_(i,j)_{Before,Left,Past,Right}.txt` per grid point plus `Log_3DPFM` / `LogCalib` log files. |
| `acquisition/` | `Acquisition_v0_2.py` | `Acquisition` class: Igor Pro and FPGA (BEPyAE) control, waveform output and data capture. |
| `acquisition/` | `ralph_tools.py` | Laser-positioning and calibration tools (R. Bulanadi, CNMS): lab-to-Asylum coordinate transform, laser moves, blind-spot location. |
| `acquisition/` | `igor_code.ipf` | Igor Pro procedures called from Python (e.g. `SpotGrid`). Load into Igor before running. |
| `analysis/` | `Data_Analysis_Single_3dLoop_pmV.ipynb` | Loads a map of 3D loops, reconstructs the x/y/z response vs. bias in pm/V and plots loops and switching maps. |
| `analysis/` | `Data_Analysis_Single_3dLoop_v2_pmV.ipynb` | Same analysis, later version with additional plots. |

## Requirements

- Windows PC controlling an Asylum Research Cypher with Igor Pro (COM automation enabled).
- `BEPyAE.exe`, the CNMS LabVIEW FPGA program the notebook launches. It is not
  distributed here; contact the authors.
- Python 3 with the packages in `requirements.txt`.

## Usage notes

- Keep `Acquisition_v0_2.py`, `ralph_tools.py` and the acquisition notebook in the
  same folder. The notebook contains `os.chdir(...)` and file paths for the
  original instrument PC; change them to your local folders before running.
- In the analysis notebooks, set the data folder to the downloaded map folder
  (e.g. from the Zenodo record).
- Responses are converted from lock-in output to pm/V in the analysis notebooks.

## Authors

Marti Checa (Oak Ridge National Laboratory, CNMS). `ralph_tools.py` by Ralph Bulanadi (CNMS).
