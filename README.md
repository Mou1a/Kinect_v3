# Kinec_v3_5.dat

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

## Preview — Kinec_BET (beta)

A compact, table-driven restructuring of this database is available in the [beta/](beta/) folder: same thermodynamic data and rate parameters, with the rate laws written once in CALCULATE_VALUES and a one-line parameter stub per mineral (see beta/README.md and table_Oelkers_BET.csv). Verified against Kinec_v3_5 for all 135 minerals — machine-precision agreement. Feedback welcome via Issues.

## Current Release
- **Kinec_v3_5.dat** (Jul 2026)

  BASIC / structural fixes:
  - Glass_Basalt: corrected jump target, line 4 `GOTO 10` → `GOTO 100`.
  - Halite: parameter block relabelled 1001 → 1000 so `goto 1000` resolves.
  - Andalusite, Kyanite: removed duplicate line 1001 (Sig moved to 1010).
  - K-Feldspar, Maximum_Microcline, Sanidine_high: `ACTI^(nC)` → `ACTI^(nb)`.
  - Ferroactinolite: removed duplicate line 5.
  - Almandine, Andradite, Grossular: Sig renumbered 10010 → 1010 (was used
    before defined, causing a 1/Sig divide-by-zero).
  - Clinoptilolite-Ca: repaired a rate expression split across two lines;
    restored the missing `^(1/Sig)` exponent.
  - Glass_Basalt kinetics: fixed fatal Basic syntax error `go to` -> `goto`
    (line 1000; triggered only when m0 <= 0).

  Rate-parameter corrections (cross-checked against Heřmanská et al. 2022, 2023
  and Oelkers & Addassi 2025, tables and text):
  - Almandine, Grossular: neutral-mechanism parameters (An, En) were defined but missing from the rate sum; added rplusn to rplus 
  - Wollastonite: basic A 20 → 200 mol m⁻² s⁻¹ (dropped zero).
  - Dolomite: aqueous-carbonate K_c 160 → 5000.
  - Strontianite: carbonate A_c 8.89 → 2.44×10⁻² (had Smithsonite's value).
  - Witherite: aqueous-carbonate K_c 160 → 60.
  - Illite: neutral A 3.348×10⁻³ → 3.84×10⁻³.
  - Paragonite: neutral A 3.48×10⁻³ → 3.84×10⁻³ (paper sets its parameters
    equal to illite).
  - Laumontite, Leonhardite: acid/neutral/basic A → 0.221 / 1.56×10⁻⁴ /
    4.94×10⁻⁵, matching chabazite (paper sets these zeolites equal to the
    average of heulandite and scolecite).
  - Andalusite, Kyanite: activation energies corrected to the Table 1
    (epidote-based) values — Andalusite 60/43.2/42.3, Kyanite 60/43.2/50
    kJ mol⁻¹; the database had inherited anorthite's Ea from a Table 11 note
    (confirmed with E. Oelkers).


## Previous Releases
- **Kinec_v3_4.dat** (Sep 01, 2025)
  - Corrected solid-solution SR definitions by replacing '*' with '^' (exponents for end-member coefficients)
  - Fixed control flow in solid-solution kinetics (line 4 now goes to 10 instead of 1000 or 100).
  - Added guard in SA calculation (line 3) to avoid zero-divide; uses fixed SA if m0 ≤ 0.
  - Carbonate rate expressions: corrected missing surface-area factor; r_plus_c now multiplied by S.
