# Project plan and method

> Single source of truth for method, schedule, milestones, risks and definition of done.
> Français : un seul document de pilotage. Les sections sont bilingues en titre, détaillées en anglais.

## 1. Method / Méthode

The project follows an **iterative V-cycle** with **stage-gates**, **Kanban** execution and **model-based design**.

| Layer | Practice | Evidence in repo |
|---|---|---|
| Structure | V-cycle: every requirement has a test | `00_requirements/requirements.csv` |
| Decisions | Gates G0 to G7 with GO, REWORK, NO-GO | `06_reports/` and Git tags |
| Execution | Kanban board, one issue per task | GitHub Projects |
| Technique | Model-based design in MATLAB/Simulink | `01_system_model/`, `02_controllers/` |
| Configuration | Baselines, tags, change requests (CR) | Git history, `CHANGELOG.md` |

Frameworks used for organization (no certification claimed): ISO/IEC/IEEE 15288 and 29148.

## 2. Priority rule / Règle de priorité

If time runs short, the order of sacrifice is: diagnostic, then sensorless, then DTC refinements.
The Rr adaptation study is the core contribution and is protected. Core guarantee: Missions 0 to 7.

## 3. Work packages and missions / Lots et missions

| Mission | WP | Weeks | Hours | Gate | Main output |
|---|---|---|---|---|---|
| 0 and 0 bis | WP0 | 1-2 | 20 | G0 | Baseline, tools, plan |
| 1 | WP0 | 2 | (in WP0) | G0 | Parameter sheet P0 |
| 2 | WP1 | 3-4 | 25 | none | Clarke and Park (TC-02) |
| 3 | WP1 | 5-6 | 30 | G1 | Machine model and energy balance |
| 4 | WP2 | 7-9 | 40 | G2 | Inverter, PWM, V/f |
| 5 | WP3 | 10-14 | 70 | G3 | FOC and PI loops |
| 6 | WP4 | 15-17 | 40 | none | Poles, margins, discretization |
| 7 | WP5 | 18-21 | 50 | G4 | DTC |
| 8 | WP6 | 22-26 | 65 | G5A | Rr adaptation (EKF) |
| 9 | WP7 | 27-30 | 50 | G5S | Sensorless (MRAS) |
| 10 | WP8 | 31-32 | 25 | G5 | Diagnostic and supervision |
| 11 | WP9 | 33-36 | 65 | G6, G7 | Campaign, report, portfolio |
| Reserve | all | up to 7 | 96 | none | Rework |

Total of work packages: 480 h. Reserve: 96 h.

## 4 bis. Critical path / Chemin critique

Model (WP1) -> FOC (WP3) -> Rr adaptation (WP6) -> Campaign (WP9).
Sensorless depends on a validated flux model. Diagnostic depends on understood degradations.
A delay on the critical path moves the end date. A delay elsewhere consumes reserve.

## 5. Gates / Portes de décision

| Gate | Question asked | Pass condition (summary) |
|---|---|---|
| G0 | Is the framing complete? | Parameters, tools, limits, targets explicit |
| G1 | Is the physics sound? | No blocking physical inconsistency |
| G2 | Is the scalar reference usable? | Energy chain and measurement work |
| G3 | Is the FOC accepted? | Gains, poles, margins, saturation proven |
| G4 | Is the DTC verified? | Table correct, domain documented |
| G5 | Are estimators safe? | Rr and sensorless guarded and independent |
| G6 | Is the campaign fair? | Models and scenarios frozen |
| G7 | Is the project deliverable? | Chapter 25 criteria met |

Outcome of each gate: GO, REWORK or NO-GO, logged in `06_reports/` with evidence. Passage depends on results, not on elapsed weeks.

## 6. Iteration loop / Boucle d'itération

For each requirement:
1. Pick one requirement (VDX-xxx).
2. Write its acceptance criterion **before** working.
3. Derive on paper, then build a minimal model.
4. **Predict** the result, then run the test.
5. Record the result, explain any gap.
6. Commit, update `requirements.csv`, note a decision or a learning entry.

## 7. Definition of Done / Critère de fin

A task is done only if all boxes are true:
- [ ] Acceptance criterion written before the work
- [ ] Derivation or explanation present (I can explain it in 5 minutes)
- [ ] Test executed, raw data kept, result predicted beforehand
- [ ] `requirements.csv` status updated (never PASS without evidence)
- [ ] Learning journal entry added
- [ ] Commit pushed with a clean message

## 8. Change control / Gestion des changements

After G0, any change of target, method or scope gets a **CR** (change request): id, justification, impacts on requirements and tests, decision, applying version. Targets are never lowered after seeing results without opening a distinct revision. A bug fix is traced with its effect on published results. CRs are tracked as GitHub issues with the label `change-request`.

## 9. Risks, assumptions, issues, dependencies (RAID)

| Type | Item | Mitigation |
|---|---|---|
| Risk | Workload underestimated | 20 % reserve, priority rule |
| Risk | Sign or frame error | TC-02 before any loop |
| Risk | Rr not observable | Freeze adaptation, ablations |
| Risk | MATLAB access lost | Explicit equations, fallback in `tools-inventory.md` |
| Risk | Comparison bias | Freeze campaign at G6 |
| Assumption | Simulation only (hardware is an extension) | Stated in README |
| Assumption | No empty weeks declared at Mission 0 | Reserve of 20 % absorbs them; add explicit weeks if needed |
| Dependency | FOC accepted before adaptation | Gate G3 then G5A |

## 10. Weekly rhythm / Rythme hebdomadaire

- **Monday (15 min):** pick the week's issues from the board.
- **During the week:** one commit per step, one issue closed per micro-goal.
- **Friday (20 min):** update board, `CHANGELOG.md` if a milestone was reached, learning journal.
- **At each gate:** review note, tag, update README status line.