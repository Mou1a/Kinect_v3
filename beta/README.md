# Kinec_BET.dat — compact table-driven format (BETA)

Same thermodynamic data and rate parameters as Kinec_v3_5, restructured for compactness and maintainability.

**Structure.** The two rate laws (Hermanska-type silicate; carbonate with aqueous-carbonate inhibition) are defined once in CALCULATE_VALUES as `Rate_Oelkers_silicate` and `Rate_Oelkers_carbonate`. Each of the 122 table minerals is a short RATES stub holding its kinetic parameters in a single line; the full parameter set is documented in `table_Oelkers_BET.csv` (the Oelkers parameter table). Solid solutions (`_ss`) and glasses keep dedicated RATES blocks (composite saturation states / leached-layer formulations).

**Usage.** Users supply only PARM(1)-PARM(4) (surface-area options); all kinetic constants live in the database. A KINETICS example is given in the file header. Requires PHREEQC 3.0 or later.

**Normalization.** Parameters are BET-surface-area normalized; a geometric-surface-area variant (`Kinec_GEO.dat`) is in preparation.

**Verification.** Checked against Kinec_v3_5 for all 135 minerals under two conditions (pH 3.5 / 25 C and pH 9 / 60 C) — results identical to machine precision.

**This is a BETA release** — please report any issues via GitHub Issues.
