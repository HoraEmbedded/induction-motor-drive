# Conventions

## Language policy
- Code, comments, commits, file names: English.
- Documentation: English first, French summary when useful.
- No em dashes in any file.

## Physics and units
- All model equations run in SI units.
- Normalized ratios are used only to present scenarios and KPIs.
- Stator currents and voltages: receiver convention.
- Rotor referred to the stator.
- Clarke and Park: amplitude invariant, three-wire (ia + ib + ic = 0).
- Electrical angle theta_e grows in the direct rotation direction.
- Mechanical speed wm in rad/s. Electrical rotor speed = p * wm.
- Currents: peak values unless stated RMS.

## Naming
- Variants: VF, FOC, DTC, FOC-A, FOC-S.
- Requirement IDs: VDX-001 to VDX-080. Tests: TC-01 to TC-40. Scenarios: SC-01 to SC-14.
- Truth signals (omega_truth, psi_r_truth, rr_true) are for evaluation only, never used by a controller.

## Git
- Branch: main (one short-lived branch per risky change if needed).
- One commit at the end of each step.
- Message format: type: short description (feat, fix, docs, test, chore, refactor).
- Tags mark reviews, for example v0.1.0-G0.