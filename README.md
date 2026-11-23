# Solar PV Performance Monitoring and Diagnostics

A case study using real monitoring data from PVDAQ System 2107. The project investigates how to tell whether low solar generation reflects a measurement issue, expected operating conditions, or genuine underperformance.

## First notebook

[`01_monitoring_data_audit.ipynb`](notebooks/01_monitoring_data_audit.ipynb) focuses on **1–7 January 2024**. It checks the sampling cadence, duplicate timestamps, gaps and missing readings in the AC power and plane-of-array irradiance streams. It then plots both signals on their original timestamps and examines one low-output interval to see what the available measurements can explain.

## Data setup

Create `data/raw/pvdaq_2107/` from the repository root and save these three files there using their original filenames.

- [2024 AC meter readings](https://oedi-data-lake.s3.amazonaws.com/pvdaq/2023-solar-data-prize/2107_OEDI/data/2107_meter_15m_data_2024.csv)
- [2024 irradiance readings](https://oedi-data-lake.s3.amazonaws.com/pvdaq/2023-solar-data-prize/2107_OEDI/data/2107_irradiance_data_2024.csv)
- [System 2107 metadata](https://oedi-data-lake.s3.amazonaws.com/pvdaq/2023-solar-data-prize/2107_OEDI/metadata/2107_system_metadata.json)

```text
data/raw/pvdaq_2107/
├── 2107_meter_15m_data_2024.csv
├── 2107_irradiance_data_2024.csv
└── 2107_system_metadata.json
```

Keep the source files local by adding `/data/raw/` to `.gitignore`.

## Planned analysis

- Estimate weather-adjusted generation and compare it with measured output over the same valid intervals.
- Investigate a sustained shortfall and quantify the energy difference against the baseline.
- Build a PostgreSQL and Grafana workflow to report daily generation, data coverage and flagged events.
