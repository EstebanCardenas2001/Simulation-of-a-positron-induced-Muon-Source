# Muon Pair Production Monte Carlo Simulation

This repository contains a Python-based Monte Carlo simulation for the unpolarized scattering process e⁺e⁻ → μ⁺μ⁻ via a virtual photon mediator[cite: 1]. The project derives the leading-order cross-section analytically, transforms kinematics from the Center-of-Mass (CM) frame to a fixed-target Laboratory frame, and generates realistic synthetic datasets representing expected experimental yields[cite: 1].

## Features

*   **QED Cross-Section Calculation:** Computes the invariant matrix element and two-body differential cross-section analytically, without relying on the relativistic limit for the muons (preserving m_μ ≠ 0)[cite: 1].
*   **Accept-Reject Monte Carlo:** Generates discrete scattering events (θ, φ) that accurately follow the theoretical Quantum Electrodynamics probability density function[cite: 1].
*   **Relativistic Kinematics:** Performs proper Lorentz boosts from the CM frame to the fixed-target Lab frame, preserving transverse momentum while scaling longitudinal momentum and energy[cite: 1].
*   **Realistic Beam Conditions:** Models the incoming positron beam with a uniform circular transverse profile (R = 1 cm) and a Gaussian energy spread (σ = 0.5 GeV) centered around the nominal threshold energy[cite: 1].
*   **Z-Dependent Target Simulation:** Simulates positron energy loss via Bremsstrahlung as it travels through a 3 cm thick Beryllium target, recalculating the local center-of-mass energy (√s) for each interaction depth z[cite: 1].
*   **Physical Event Weighting:** Computes the necessary rescaling factors to map the simulated event count to the expected physical yield, assuming a positron rate of 10⁶ Hz over one week of continuous operation[cite: 1].

## Dependencies

The simulation relies on standard scientific Python libraries[cite: 1]:
*   `numpy`
*   `scipy`
*   `matplotlib`
*   `pandas`
*   `IPython` (for notebook image rendering)

## Generated Datasets

The pipeline produces two primary synthetic datasets, formatted as CSV files with row-wise event records[cite: 1]:

1.  **`muon_events_dataset.csv`**: Contains 100,000 simulated events assuming a constant nominal beam energy[cite: 1]. Includes the 3 spatial momentum coordinates for both the μ⁻ and μ⁺ in the laboratory frame, alongside the starting beam coordinates and initial Gaussian-smeared energy[cite: 1].
2.  **`advanced_muon_events.csv`**: Contains the results of the z-dependent simulation, incorporating energy loss[cite: 1]. This dataset adds the exact interaction depth (`z_origin`) and the local Mandelstam variable (`s_local`) for each valid event[cite: 1].

## Visualizations

The code generates several analytical and statistical plots to validate the Monte Carlo methods and physical models. 

### 1. Monte Carlo Validation
The Accept-Reject algorithm relies on a bounding box (w_max) to sample the theoretical distribution. 
![Monte Carlo Accept-Reject](<img width="1187" height="707" alt="1" src="https://github.com/user-attachments/assets/8c75f199-f8c7-4d91-9566-5b76a346a020" />)

### 2. Angular & Kinematic Distributions
Compares the uniform azimuthal angle (φ) and the highly directional polar scattering angle (θ) against theoretical QED PDFs, alongside CM vs. Lab momentum shifts[cite: 1].
![Kinematic Distributions](<img width="1389" height="490" alt="2" src="https://github.com/user-attachments/assets/6e5defd7-b2c9-4591-88fd-2a27e6dc6849" />
)

### 3. Realistic Beam Profile & Energy Spread
Visualizes the uniform density correction applied to the beam radius sampling to prevent unphysical central clustering, and the normal distribution of the beam energy[cite: 1].
![Beam Profile](<img width="1475" height="1184" alt="3" src="https://github.com/user-attachments/assets/6e385766-0c4f-4704-bce0-1974031bed60" />
) 

### 4. Target Bremsstrahlung Energy Loss
Maps the exponential decay of the positron beam energy through the Beryllium target, ensuring the nominal energy is high enough to cross the ≈ 43.69 GeV minimum threshold by the exit[cite: 1].
![Energy Loss](<img width="990" height="590" alt="4" src="https://github.com/user-attachments/assets/a0063d1c-28b8-49a8-ae94-f694ac31b839" />
) 

### 5. Z-Dependent Production Depth
Displays the weighted vs. unweighted distribution of muon origins inside the target, demonstrating how the production rate drops exponentially as the beam loses energy[cite: 1].
![Z-Dependent Production](<img width="1187" height="707" alt="6" src="https://github.com/user-attachments/assets/eaca24de-edc5-4d04-a8fd-d03a77e660ba" />
) 

## Usage

To reproduce the datasets and plots, execute the main Jupyter Notebook `Project.ipynb` sequentially[cite: 1]. The script will automatically calculate the kinematic threshold, compute the correct nominal beam energy for the Beryllium target, generate the MC events, and output the `.csv` datasets[cite: 1].
