# induction-motor-drive

![License](https://img.shields.io/github/license/HoraEmbedded/induction-motor-drive)
![Last commit](https://img.shields.io/github/last-commit/HoraEmbedded/induction-motor-drive)
![MATLAB](https://img.shields.io/badge/MATLAB-Simulink-orange)

**VECTOR-DRIVE X+** : modeling, control and validation of a three-phase induction motor drive in MATLAB/Simulink.

> Status: **Mission 0 (setup)**. Parameters and targets are proposals pending review G0 (Gate 0). No performance is claimed yet.

## Goal

Build a reproducible digital test bench to understand, implement and compare five control strategies on one common machine:

| Variant | Full name | Description |
|---|---|---|
| VF | Voltage/Frequency control | Open-loop scalar V/f control |
| FOC | Field-Oriented Control | Indirect rotor-flux-oriented vector control, measured speed |
| DTC | Direct Torque Control | Classical direct torque control |
| FOC-A | FOC with Adaptive rotor resistance | FOC with online rotor resistance (Rr) adaptation |
| FOC-S | FOC Sensorless | FOC with sensorless speed estimation (MRAS), Rr fixed |

**MRAS** = Model Reference Adaptive System. **Rr** = rotor resistance.

**Research question:** under which conditions does adapting Rr actually improve FOC speed regulation, and at what cost in computation, noise sensitivity and robustness?

## Repository layout

| Folder | Content |
|---|---|
| `00_requirements` | Specification, requirements, traceability |
| `01_system_model` | Machine, inverter, loads, physical validation |
| `02_controllers` | vf, foc, dtc, foc_adaptive, foc_sensorless |
| `03_testbench` | Scenarios, KPI (Key Performance Indicator) scripts, campaigns |
| `04_results` | Run outputs, manifests, figures |
| `05_safety` | Risk analysis, conditional hardware file |
| `06_reports` | Calculation notes, reviews G0 to G7, final report |
| `07_portfolio` | Case study and summary figures |
| `config` | Plant, control, estimator and campaign parameters |
| `docs` | Conventions, decisions, learning journal |
| `captures` | Screenshots of progress |

## Roadmap

## Roadmap

Missions 0 to 11 follow the 10 work packages (WP0 to WP9) and the 8 gate reviews (G0 to G7) of the specification VDX-CDC-002. A gate review is a decision point (GO, REWORK or NO-GO) based on evidence, not on elapsed time.

See [docs/PLAN.md](docs/PLAN.md) for method, schedule and gates.

## Requirements

MATLAB and Simulink (exact versions recorded in `docs/tools-inventory.md`).

## Honesty policy

Simulation is never presented as a real motor experiment. Analytical results, simulated results and hardware measurements are always separated.

## License

MIT. See `LICENSE`.

---

# Version française

**VECTOR-DRIVE X+** : modélisation, commande et validation d'un entraînement à moteur asynchrone triphasé sous MATLAB/Simulink.

> Statut : **Mission 0 (mise en place)**. Les paramètres et cibles sont des propositions en attente de la revue G0 (porte 0). Aucune performance n'est déclarée.

## Objectif

Construire un banc d'essai numérique reproductible pour comprendre, implanter et comparer cinq commandes sur une même machine : V/f ouverte, FOC, DTC, FOC adaptative (adaptation de Rr) et FOC sans capteur mécanique (MRAS).

| Variante | Nom complet | Description |
|---|---|---|
| VF | Commande tension/fréquence | Commande scalaire V/f en boucle ouverte |
| FOC | Commande vectorielle à flux orienté (Field-Oriented Control) | Commande vectorielle indirecte, vitesse mesurée |
| DTC | Commande directe du couple (Direct Torque Control) | Commande directe du couple classique |
| FOC-A | FOC avec adaptation de la résistance rotorique | Adaptation en ligne de Rr |
| FOC-S | FOC sans capteur mécanique | Estimation de vitesse par MRAS, Rr figée |

**MRAS** = système adaptatif à modèle de référence (Model Reference Adaptive System). **Rr** = résistance rotorique.

**Question de recherche :** dans quelles conditions l'adaptation de la résistance rotorique améliore-t-elle réellement la régulation de vitesse d'une FOC, et à quel coût en calcul, sensibilité au bruit et robustesse ?

## Politique d'honnêteté

Une simulation n'est jamais présentée comme un essai sur moteur réel. Les calculs analytiques, les résultats simulés et les mesures matérielles sont toujours séparés.

## Licence

MIT. Voir `LICENSE`.
