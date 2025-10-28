# Kinec_v3.dat

Thermodynamic and kinetic database for use in PHREEQC, combining data from Carbfix.dat, llnl.dat, and curated kinetic parameters from:

1- Heřmanská, M., Voigt, M.J., Marieni, C., Declercq, J., Oelkers, E.H. (2022).
A comprehensive and internally consistent mineral dissolution rate database: Part I: Primary silicate minerals and glasses. Chemical Geology, 597, 120807.
https://doi.org/10.1016/j.chemgeo.2022.120807 

2- Heřmanská, M., Voigt, M.J., Marieni, C., Declercq, J., Oelkers, E.H. (2023).
A comprehensive and internally consistent mineral dissolution rate database: Part II: Secondary silicate minerals. Chemical Geology, 636, 121632.
https://doi.org/10.1016/j.chemgeo.2023.121632

3- Oelkers, E.H., Addassi, M. (2025a).
A comprehensive and consistent mineral dissolution rate database: Part III: Non-silicate minerals including carbonate, sulfate, phosphate, halide, and oxy-hydroxide minerals. Chemical Geology, 673, 122528.
https://doi.org/10.1016/j.chemgeo.2024.122528

4- Oelkers, E.H., Addassi, M. (2025b).
Kinec_v3: A computer database for the calculation of the dissolution rates of the major rock forming minerals. Chemical Geology, 695, 123041.
https://doi.org/10.1016/j.chemgeo.2025.123041

📌 Use with PHREEQC via KINETICS blocks.  
📎 See file header for references, usage instructions, and parameter definitions.

## Current Release

- **Kinec_v3_4.dat** (Sep 01, 2025)
  - Corrected solid-solution SR definitions by replacing '*' with '^' (exponents for end-member coefficients)
  - Fixed control flow in solid-solution kinetics (line 4 now goes to 10 instead of 1000 or 100).
  - Added guard in SA calculation (line 3) to avoid zero-divide; uses fixed SA if m0 ≤ 0.
  - Carbonate rate expressions: corrected missing surface-area factor; r_plus_c now multiplied by S.
