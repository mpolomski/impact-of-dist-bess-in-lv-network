# Dataset for: Impact of distributed BESS controlled by optimization-based HEMS on the voltage profiles in high PV-saturated LV networks

This repository contains the dataset used for the simulations and analyses presented in the research article:

**"Impact of distributed battery energy storage controlled by optimization-based home energy management systems implementing various objective functions on the voltage profiles in the low-voltage network with a high saturation of prosumer photovoltaic micro-installations"**


## Authors of the Article and Dataset

*   Roman Korab (Department of Power Systems and Control, Faculty of Electrical Engineering, Silesian University of Technology, Gliwice, Poland) - Corresponding Author
*   Marcin Połomski (Department of Algorithmics and Software, Faculty of Automatic Control, Electronics and Computer Science, Silesian University of Technology, Gliwice, Poland)
*   Marcin Smołka (Joint Doctoral School, Silesian University of Technology, Gliwice, Poland)
*   Tomasz Naczyński (Joint Doctoral School, Silesian University of Technology, Gliwice, Poland)

## Abstract of the Article

Prosumer photovoltaic (PV) micro-installations change the operating conditions of low-voltage (LV) networks. When these networks are highly saturated with PV sources, some disruptions in their operation may occur periodically. In particular, long-term overvoltages are a frequent phenomenon, the most noticeable effect of which is the shutdown of PV sources. The simulation results showed that long-term overvoltages could affect more than a third of the customers supplied from a real LV rural network and last up to 383 hours per year. As a result, the yearly generation of the PV source can be reduced by up to 25.6%. The method of overvoltage mitigation analyzed in this article consists of changing the unfavorable power balance using distributed battery energy storage systems (BESSs). However, the effectiveness of this voltage control method depends on the adopted control strategy for the BESSs. In this article, distributed BESSs are assumed to be controlled by individual, optimization-based home energy management systems (HEMSs). Using a model of a real LV rural network, the impact of BESSs operating according to the schedules resulting from two objective functions of HEMSs (i.e., energy cost minimization and maximization of prosumer financial neutrality) are compared. Better results are achieved when BESSs are operated according to profiles that maximize the financial neutrality of prosumers. In this case, the maximum duration of long-term overvoltages is reduced from 383 to 231 hours per year, compared with 251 hours when the BESSs are controlled in a way that minimizes energy costs, while the yearly reduction in PV generation is 16.1% and 17.9%, respectively.

## Dataset Description

This dataset comprises simulation results derived from a model of an actual low-voltage (LV) rural distribution network. It encompasses various scenarios of Battery Energy Storage System (BESS) operation, with data organized into daily and yearly simulation outputs.

**Note on Network Model:** The detailed model of the LV distribution network used for these simulations is proprietary and not publicly available due to confidentiality agreements with the network operator. However, the input data profiles provided in the subfolders allow for the replication of load, PV generation, and BESS dispatch conditions.

### Data Structure

The dataset is organized as follows:

```
├── 1. Daily simulations
│ ├── 1. without BESS # Scenario: No BESS operation
│ │ ├── 1. Customers # Customer-specific line monitoring data
│ │ │ ├── !Sieć_nN_Mon_line.[...]_p_q_1.csv # Active (P) and reactive (Q) power
│ │ │ └── !Sieć_nN_Mon_line.[...]u_i_1.csv # Voltage (U) and current (I)
│ │ ├── 2. LV grid # Aggregated LV grid monitoring data (OpenDSS reports)
│ │ │ ├── DI_Overloads_1.CSV
│ │ │ ├── DI_SystemMeter_1.CSV
│ │ │ ├── DI_Totals_1.CSV
│ │ │ ├── DI_VoltExceptions_1.CSV
│ │ │ ├── em_1.CSV
│ │ │ ├── em_PhaseVoltageReport_1.CSV
│ │ │ ├── EnergyMeterTotals_1.CSV
│ │ │ ├── SystemMeter_1.CSV
│ │ │ └── Totals_1.CSV
│ │ ├── 3. Transformer # Transformer monitoring data
│ │ │ ├── !Sieć_nN_Mon_transformer.mv-lv_p_q_1.csv
│ │ │ ├── !Sieć_nN_Mon_transformer.mv-lv_u_i_1.csv
│ │ │ └── !Sieć_nN_Mon_transformer.mv-lv_u_i_sym_1.csv
│ │ ├── 4. PV sources # PV source-specific monitoring data (power per phase)
│ │ │ └── !Sieć_nN_Mon_pvsystem.pv[...]_p_q_1.csv
│ │ ├── 5. Load # Load-specific monitoring data (power per phase)
│ │ │ └── !Sieć_nN_Mon_load.[...]_p_q_1.csv
│ │ └── 6. OpenDSS data # Key input profiles for OpenDSS simulations
│ │ ├── Bus_Load.csv
│ │ ├── Bus_MV_Voltage.csv
│ │ ├── PV_Irradiance.csv
│ │ └── PV_Temperature.csv
│ ├── 2. max FN - day 1 # Scenario: BESS maximizing Financial Neutrality - Day 1
│ │ ├── ... (structure as above, includes BESS monitoring files in '2. BESS' subfolder)
│ │ └── 7. OpenDSS data
│ │ └── Bus_Storage - max FN - day 1.csv # BESS dispatch profile
│ ├── 3. max FN - day 2 # Scenario: BESS maximizing Financial Neutrality - Day 2
│ │ ├── ...
│ │ └── 7. OpenDSS data
│ │ └── Bus_Storage - max FN - day 2.csv
│ ├── 4. min CE - day 1 # Scenario: BESS minimizing Cost of Energy - Day 1
│ │ ├── ...
│ │ └── 7. OpenDSS data
│ │ └── Bus_Storage - min CE - day 1.csv
│ └── 5. min CE - day 2 # Scenario: BESS minimizing Cost of Energy - Day 2
│ ├── ...
│ └── 7. OpenDSS data
│ └── Bus_Storage - min CE - day 2.csv
├── 2. Yearly simulations
│ ├── 1. Without BESS # Yearly scenario: No BESS operation
│ │ ├── ... (structure as daily simulations)
│ ├── 2. Max FN # Yearly scenario: BESS maximizing Financial Neutrality
│ │ ├── ... (includes BESS monitoring)
│ │ └── 7. OpenDSS data
│ │ └── Bus_Storage - max FN.csv
│ └── 3. Min CE # Yearly scenario: BESS minimizing Cost of Energy
│ ├── ... (includes BESS monitoring)
│ └── 7. OpenDSS data
│ └── Bus_Storage.csv

```


### File Naming Convention and Content Details

*   Files prefixed with `!Sieć_nN_Mon_line...` contain monitoring data for individual customer connection points (lines/feeders).
    *   `..._p_q_1.csv`: Time-series of active power (P) and reactive power (Q). Columns: [PLACEHOLDER: e.g., Timestamp, P_L1_kW, Q_L1_kvar, P_L2_kW, Q_L2_kvar, P_L3_kW, Q_L3_kvar]. Time resolution: [PLACEHOLDER: e.g., 1-minute].
    *   `..._u_i_1.csv`: Time-series of voltage (U) and current (I). Columns: [PLACEHOLDER: e.g., Timestamp, U_L1_V, I_L1_A, ...]. Time resolution: [PLACEHOLDER].
*   Files prefixed with `!Sieć_nN_Mon_transformer...` contain MV/LV transformer monitoring data.
*   Files prefixed with `!Sieć_nN_Mon_pvsystem...` contain PV system generation data (per phase).
*   Files prefixed with `!Sieć_nN_Mon_load...` contain customer load data (per phase).
*   Files prefixed with `!Sieć_nN_Mon_storage...` (within BESS scenarios) detail BESS charging/discharging power and State of Charge (SoC). Columns: [PLACEHOLDER: e.g., Timestamp, P_BESS_kW, SoC_percent].
*   Files within `LV grid` subfolders (`DI_...`, `em_...`) are standard OpenDSS output reports, containing aggregated grid parameters, overload reports, and voltage exception summaries.
*   Files within `OpenDSS data` subfolders provide key input time-series profiles for the OpenDSS simulations (e.g., `Bus_Load.csv` for aggregated load profiles, `PV_Irradiance.csv`, `PV_Temperature.csv`, and BESS dispatch schedules in `Bus_Storage - [scenario].csv`).
*   All data files are in CSV (Comma Separated Values) format, using [PLACEHOLDER: e.g., a comma as a delimiter and a period as a decimal separator]. Column headers are provided in the first row of each CSV file.


## How to Use This Data

This dataset is provided to enable:
*   Replication of the simulation results presented in the associated research article.
*   Further investigation into the impacts of BESS and PV systems on LV distribution networks.
*   Development and validation of novel BESS control algorithms or HEMS objective functions.


## Citation

Researchers using this dataset are kindly requested to cite both the original research article and this dataset.

**1. The Article:**

Article details.

**2. This Dataset:**

Name of the Repository.

If a DOI for the dataset is not yet available or if citing the GitHub repository directly, please use:

Korab, R.; Połomski, M.; Smołka, M.; Naczyński, T. (2025). Dataset for: Impact of distributed battery energy storage [...]. Retrieved from [place here thr URL of this GitHub repository].

*Please also cite the associated article.*

## License

This dataset is made available under the **Creative Commons Attribution 4.0 International (CC BY 4.0) license**.

[![CC BY 4.0](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0/)

This license allows others to:
*   **Share** — copy and redistribute the material in any medium or format.
*   **Adapt** — remix, transform, and build upon the material for any purpose, even commercially.

Under the following terms:
*   **Attribution** — You must give appropriate credit, provide a link to the license, and indicate if changes were made. You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use. **This includes citing the original research article (see "Citation" section above) and this dataset (if a DOI is available).**

For the full license text, please visit: [https://creativecommons.org/licenses/by/4.0/legalcode](https://creativecommons.org/licenses/by/4.0/legalcode)

## Note on Automated Data Collection and AI Training

Please note that while this data is publicly available under the [![CC BY 4.0](https://i.creativecommons.org/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0/) license, any automated collection or use of this data for the training of artificial intelligence models should respect the terms of the license, particularly regarding attribution to the original authors and this work.

## Contact

For inquiries regarding this dataset or the associated research, please contact the corresponding author.