# Angelic Lotus — ENSO, Global Temperature & Food Security in India

Analysis of how **increasing global mean temperature** and **ENSO (El Niño–Southern Oscillation)** affect **food security in India** (focus on June–September). The project combines climate reanalysis (ERA5-derived) and FAO crop yield data to explore correlations between climate anomalies and agricultural outcomes.

---

## Team

- Tejaswini Machhindra Pawase  
- Yunqing / Isaac Han  
- Vitor Luiz Victalino Galves  
- Sandesh Rai  
- N'guessan Cesaire Kouadio  
- Kevin Juan Roman Rafaele  

---

## Research Question

**How do increasing 2 m air temperature and changes in ENSO affect food security in India between June and September?**

## Objectives

- Analyse the trend of **global mean temperature** (2 m).
- Analyse the trend of **SST anomalies** in the Niño 3.4 region.
- Examine the relationship between **temperature / rainfall** and **food security** (crop yields) in India.

## Data

| Source | Description |
|--------|-------------|
| **ERA5** | Monthly 2 m temperature (global and India), total precipitation (India). Climatology 1960–1990; anomalies 1991–present. |
| **Niño 3.4** | Monthly SST anomalies (1991–2023), including JJAS (June–September) averages. |
| **FAO** | Crop production statistics for India: Rice, Cabbages, Grapes, Lentils, Mangoes, Wheat. Yield anomalies from 1991. |

## Methodology

- **Climatology:** 1960–1990 (baseline).  
- **Anomalies:** 1991–present for climate and crop yields.  
- **Analysis:** Time series, spatial maps (Cartopy), correlation matrices (Pearson and Spearman), and cross-correlation (e.g. ENSO vs crop yields).

---

## Main Results

### Climate and ENSO

- **Global 2 m temperature** and **India 2 m temperature** show a clear upward trend in anomalies from 1991 onward, consistent with warming.
- **Niño 3.4 SST** exhibits typical ENSO variability (El Niño / La Niña episodes).
- **Total precipitation over India** (JJAS) shows strong interannual variability; negative SST 3.4 anomalies (La Niña) tend to coincide with wetter conditions in the region (negative correlation between SST 3.4 and India precipitation in the correlation matrix).

### Correlations (1991–2022, Pearson)

- **Global 2 m temperature vs crop yield anomalies:**  
  - **Rice:** *r* ≈ 0.85  
  - **Wheat:** *r* ≈ 0.82  
  - **Lentils:** *r* ≈ 0.61  
  - **Cabbages:** *r* ≈ 0.54  

- **India 2 m temperature** is also positively correlated with Rice and Wheat yield anomalies (*r* ≈ 0.66 and 0.56).

- **ENSO (SST 3.4)** vs yields:  
  - Weak to moderate negative correlations with Rice and Wheat (e.g. *r* ≈ −0.21, −0.23).  
  - **SST 3.4 vs India precipitation:** *r* ≈ −0.53 (stronger La Niña → wetter India).

- **India precipitation** vs yields: moderate positive correlation with Rice (*r* ≈ 0.39) and Cabbages (*r* ≈ 0.31).

*Note: The notebook also computes Spearman correlations and cross-correlations (e.g. SST 3.4 vs Cabbages yield anomalies) for robustness and lag analysis.*

---

## Figures (from the notebook)

The notebook `angelic_lotus_project.ipynb` produces the following types of plots. Run the notebook to regenerate them; they appear inline in the executed cells. To export figures as PNG files for the repo, you can use the script `scripts/extract_notebook_figures.py` (run from the repo root: `python scripts/extract_notebook_figures.py angelic_lotus_project.ipynb --out figures`).

### 1. Climate time series

- **SST Niño 3.4** — Monthly and annual (JJAS) anomalies.  
- **Global mean 2 m temperature** — Monthly and annual anomalies.  
- **India mean 2 m temperature** — From NetCDF; time series of spatial mean.  
- **India total precipitation** — Climatology and anomalies (monthly/annual).

### 2. Combined time series

- Single plot with **ENSO 3.4**, **global T2m**, **India T2m**, and **India precipitation** (monthly and yearly) for direct comparison.

### 3. Spatial maps (Cartopy)

- **2 m temperature anomalies over India** — Mean anomaly field.  
- **Total precipitation anomalies over India** — Mean anomaly field.  
- **Niño 3.4 region** — SST anomaly map (for context).

### 4. Crop yield anomalies

- Time series of **Rice, Cabbages, Grapes, Lentils, Mangoes, Wheat** yield anomalies (India, from FAO).

### 5. Correlation matrices

- **Pearson** correlation heatmap: crop yield anomalies vs `sst3_4`, `global_t2m`, `india_t2m`, `india_tp`.  
- **Spearman** correlation heatmap (same variables).

### 6. Cross-correlation

- **Cross-correlation function (CCF):** SST 3.4 vs Cabbages yield anomalies (example of lagged relationship).

---

## Repository contents

- **`angelic_lotus_project.ipynb`** — Main analysis (data loading, climatology, anomalies, maps, correlations, CCF).  
- **`README.md`** — This file (overview, results, and figure descriptions).

Data files (CSV/NetCDF) are not included; you need to place them in the same directory as the notebook or adjust paths:

- `sst3.4 - 1991 to 2023.csv`  
- `global_t2m_mean - 1991 to 2023.csv`  
- `t2m_anomalies_india_1991-2023.nc`  
- `tp_india_1940-2023.nc`  
- `FAOSTAT_data_en_7-24-2024.csv` (or your FAO export for India/crops).

---

## How to run

1. Clone the repo (or download the notebook).  
2. Install dependencies, e.g.:

   ```bash
   pip install xarray pandas matplotlib scipy seaborn cartopy statsmodels
   ```

3. Place the required data files in the same folder as the notebook (or update paths in the notebook).  
4. Open and run **`angelic_lotus_project.ipynb`** (e.g. in Jupyter or VS Code). All figures will appear in the output cells.

---

## References

- Cooper, M., Brown, M.E., Azzarri, C. et al. (2019). Hunger, nutrition, and precipitation: evidence from Ghana and Bangladesh. *Popul Environ* **41**, 151–208.  
- Kang, Y., Khan, S., & Ma, X. (2009). Climate change impacts on crop yield, crop water productivity and food security – A review. *Progress in Natural Science*, **19**(12), 1665–1674.  
- Ringler, C., Zhu, T., Cai, X., Koo, J., & Wang, D. (2010). Climate change impacts on food security in sub-Saharan Africa. *Insights from comprehensive climate change scenarios*, **2**.  
- Villafuerte, M.Q. & Matsumoto, J. (2015). Significant Influences of Global Mean Temperature and ENSO on Extreme Rainfall in Southeast Asia. *Journal of Climate*, **28**(5), 1905–1919.
