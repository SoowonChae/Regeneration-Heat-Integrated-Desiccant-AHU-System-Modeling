# Regeneration-Heat-Integrated Desiccant Air-Conditioning System Modeling
*A dynamic modeling framework for desiccant air-conditioning integrated with renewable/auxiliary regeneration heat sources.*

## Overview
This project provides a transient DAC model that couples adsorption–desorption physics (e.g., GAB isotherm) and energy–mass balances with regeneration heat sources (PVT, GSHP, thermal storage) to evaluate performance, comfort, and operation strategies.

## Features
- Dynamic adsorption/regeneration zone modeling
- Sorption isotherm support (e.g., GAB) and property utilities
- Regeneration heat-source coupling: PVT / GSHP / thermal storage
- Metrics: system COP, comfort indicators, renewable utilization, seasonal performance

## Repository Structure
    ├── Models/                 # Core DAC & component models
    ├── Sources/                # Regeneration heat-source modules (PVT, GSHP, HST)
    ├── Scenarios/              # Weather/load profiles, run configs
    ├── Scripts/                # Runners, plotting, analysis helpers
    ├── Results/                # Simulation outputs
    ├── Docs/                   # Notes, equations, references
    └── run_simulation.py       # Example entry point

## Getting Started
Clone:
    git clone https://github.com/USERNAME/REPO.git
    cd REPO

Install:
    pip install -r requirements.txt

Run:
    python run_simulation.py --config Scenarios/baseline.yaml

## Minimal Example (Pseudo-API)
    from Models.dac import DACModel
    from Sources.pvt import PVTSource
    from Scenarios.loader import load_config

    cfg = load_config("Scenarios/baseline.yaml")
    pvt = PVTSource(cfg["pvt"])
    dac = DACModel(cfg["dac"], regen_source=pvt)
    history = dac.run(weather=cfg["weather"], loads=cfg["loads"])
    history.to_csv("Results/baseline_timeseries.csv")

## Inputs / Outputs
- Inputs: weather (TMY/ASOS), internal loads, airflow/waterflow setpoints, heat-source parameters
- Outputs: outlet air state (T/RH/W), rotor state, energy flows, COP, comfort metrics, time series/plots

## Roadmap
- [ ] Lab/field validation
- [ ] Multi-source blending (PVT + GSHP + DH/boiler backup)
- [ ] Control co-simulation (rule-based, DNN, RL)
- [ ] Economic analysis & seasonal optimization

## License
MIT License. See LICENSE for details.
