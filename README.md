🌱 Carbon Emissions of GPUs in LLM Training
📌 Project Overview

This project estimates the carbon footprint of GPUs used in AI / Large Language Model (LLM) training.
It combines GPU specifications, real-world power measurements, and global electricity carbon intensities to calculate the environmental impact of training AI models.

We answer:

How much CO₂ is emitted when training an LLM on different GPUs?

How do GPU power ratings (TDP) affect emissions?

How do country-specific electricity mixes change results?

📊 Datasets Used

GPU Specs Dataset (gpu_specs_v7.csv) → memory, shaders, clocks, TDP

BUTTER-E Dataset (butter_e_energy.csv) → real GPU power measurements

EU Carbon Intensity (2017_CO2_IntensEL_EEA.csv)

Global Energy Mix (OWID) (owid-energy.csv)

⚙️ Methodology

GPU Power Estimation

Use TDP from dataset if available.

If missing, apply a heuristic based on shaders, clock speed, and memory size.

Energy Calculation

Energy (kWh)
=
Watts
×
Hours
1000
Energy (kWh)=
1000
Watts×Hours
	​


Carbon Emission Calculation

CO₂ (kg)
=
Energy (kWh)
×
Carbon Intensity (kgCO₂/kWh)
CO₂ (kg)=Energy (kWh)×Carbon Intensity (kgCO₂/kWh)

Validation

Use BUTTER-E dataset to compute measured kWh and emissions.

Compare against estimated values.

LLM Training Simulation

Function simulate_llm_training() lets you input GPU watts, training hours, country, and year to estimate CO₂ emissions.

📈 Key Results

High-end GPUs like NVIDIA A100 or RTX 3090 emit the most CO₂ when used continuously.

Emissions vary significantly by country depending on energy grid carbon intensity.

Example:

400W GPU running 24h in the US (2017): ~4.56 kg CO₂

Same GPU in France (2017, low-carbon grid): ~0.74 kg CO₂

Validated against real-world measurements from BUTTER-E dataset.

🛠️ Files Generated

gpu_emission_estimates_24h.csv → estimated 24h emissions for all GPUs

butter_e_summary.csv → measured emissions from BUTTER-E dataset

🚀 How to Run

Open the Kaggle notebook.

Upload datasets (gpu_specs_v7.csv, butter_e_energy.csv, 2017_CO2_IntensEL_EEA.csv, owid-energy.csv).

Run all cells to:

Clean and estimate GPU power usage

Calculate CO₂ emissions

Simulate LLM training emissions

Export results

🌍 Why this matters

Training large AI models consumes massive energy. By quantifying emissions, this project helps raise awareness about the environmental cost of deep learning and encourages more carbon-aware AI research.
