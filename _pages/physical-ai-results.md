---
layout: single
title: "Physical AI - Detailed Results"
permalink: /portfolio/physical-ai/results/
excerpt: >-
  Training, evaluation, checkpoint, test, and runtime evidence for the Physical
  AI project.
author_profile: true
---

This page contains the measurements behind the shorter portfolio summary. The
articulated-robot results come from Isaac Lab simulation on one NVIDIA L40S.
Analytical point-mass results are reported separately and are not presented as
robot performance.

<p>
  <a class="btn btn--primary" href="{{ '/portfolio/physical-ai/' | relative_url }}">Back to project</a>
  <a class="btn" href="https://github.com/codemith/Physical-AI/tree/main/physical-ai-data/evidence">Evidence on GitHub</a>
</p>

## Results at a Glance

| Area | Result |
|---|---|
| PPO training | 98.3 million simulation steps, 4,096 parallel environments, 1,000 iterations |
| UR10e evaluation | Passed 9/9 reports across 3 seeds and 3 conditions |
| Settled reach error | 2.1-2.9 cm mean error; worst p95 error was 8.8 cm |
| Pick-and-place | Successful 0.800 m lift and 0.129 m final target error |
| Automated tests | 217 executed: 202 passed and 15 optional-dependency skips |
| Safety boundary | Passed 15/15 deterministic software-in-the-loop fault scenarios |
| Batch execution | Standalone SLURM job completed with exit code 0 |

## UR10e PPO Training

The selected policy was trained with RSL-RL PPO using a 25-value observation,
six continuous joint-position actions, and a 64 x 64 ELU actor-critic network.

| Training property | Recorded value |
|---|---:|
| Parallel environments | 4,096 |
| PPO iterations | 1,000 |
| Total simulation steps | 98,304,000 |
| Training time | 628.9 seconds |
| Final throughput | 170,802 steps/second |
| Physics and policy rates | 120 Hz and 30 Hz |
| Training seed | 42 |
| PPO clip / gamma / GAE lambda | 0.2 / 0.99 / 0.95 |

The run retained the complete
[training log](https://github.com/codemith/Physical-AI/blob/main/physical-ai-data/evidence/ur10-rsl-l40s-2026-08-29/final_bundle/artifacts/training/training.log)
and frozen
[environment and agent parameters](https://github.com/codemith/Physical-AI/tree/main/physical-ai-data/evidence/ur10-rsl-l40s-2026-08-29/final_bundle/artifacts/training/params).

## Checkpoint Selection

Three predefined checkpoints were compared on selection seed 9002. Passing
candidates were ranked by settled mean position error and then p95 error.

| Checkpoint | Mean error | p95 error | Gate |
|---|---:|---:|---|
| Iteration 500 | 5.46 cm | 22.19 cm | Failed |
| Iteration 750 | 2.85 cm | 7.97 cm | Passed |
| Iteration 999 | 2.13 cm | 7.35 cm | Passed and selected |

Selected checkpoint SHA-256:

190a5323acf3ebc9f658bf67a1c8d447debabb73b303705a6a196a82acb5e635

The full
[selection summary](https://github.com/codemith/Physical-AI/blob/main/physical-ai-data/evidence/ur10-rsl-l40s-2026-08-29/final_bundle/artifacts/checkpoint_selection/selection_summary.json)
records candidate hashes, reports, thresholds, and selection order.

## Articulated Policy Evaluation

The selected checkpoint was independently evaluated on seeds 1001, 2001, and
3001 under nominal, randomized, and stress conditions. Each report contains 512
episodes and 44,800 samples from the final settled second of each target
interval.

| Seed | Condition | Mean error | p95 error | Within threshold |
|---:|---|---:|---:|---:|
| 1001 | Nominal | 2.10 cm | 7.06 cm | 91.1% within 5 cm |
| 1001 | Randomized | 2.22 cm | 8.14 cm | 96.7% within 10 cm |
| 1001 | Stress | 2.95 cm | 8.84 cm | 96.2% within 10 cm |
| 2001 | Nominal | 2.20 cm | 7.85 cm | 90.9% within 5 cm |
| 2001 | Randomized | 2.17 cm | 8.09 cm | 96.8% within 10 cm |
| 2001 | Stress | 2.82 cm | 8.60 cm | 96.2% within 10 cm |
| 3001 | Nominal | 2.31 cm | 8.63 cm | 89.5% within 5 cm |
| 3001 | Randomized | 2.22 cm | 7.62 cm | 97.1% within 10 cm |
| 3001 | Stress | 2.87 cm | 8.29 cm | 96.7% within 10 cm |

All nine reports passed their frozen mean-error, p95-error, and
within-threshold gates. The
[validation summary](https://github.com/codemith/Physical-AI/blob/main/physical-ai-data/evidence/ur10-rsl-l40s-2026-08-29/final_bundle/artifacts/evaluations/policy_validation_summary.json)
links each report to the selected checkpoint hash.

## Autonomous Pick-and-Place

The separate deterministic controller was recorded at 3840 x 2160 and 30 FPS
for 450 frames.

| Measurement | Result |
|---|---:|
| Cube lift | 0.800 m |
| Final planar target error | 0.129 m |
| Final vertical target error | Less than 0.001 mm |
| Task result | Success |

This demonstration uses a state machine and surface gripper. It is intentionally
not described as reinforcement learning.

## Analytical Point-Reach Baselines

Before moving into articulated simulation, PPO was compared with PD and random
controllers in a lightweight 2D environment. PPO results pool three training
seeds over 20 held-out evaluation seeds.

| Controller | Nominal | Randomized | Stress |
|---|---:|---:|---:|
| PPO | 100% | 90% | 13.3% |
| PD | 100% | 95% | 95% |
| Random | 0% | 5% | 5% |

The stress result is useful rather than embarrassing: it shows that the learned
policy did not generalize as well as the classical controller in this analytical
task. The project keeps that failure visible instead of treating nominal success
as sufficient evidence. See the
[analytical evidence release](https://github.com/codemith/Physical-AI/blob/main/physical-ai-data/evidence/analytical-point-reach-v1/release_summary.md).

## Tests, Runtime, and Safety Evidence

The current portable and offline Isaac suites executed 217 tests: 202 passed and
15 optional Gymnasium or Stable-Baselines3 tests were skipped because those
dependencies were not installed in the test shell.

Runtime evidence also records:

- A finite articulated UR10e smoke run on one NVIDIA L40S.
- Standalone SLURM job 15366221 with COMPLETED state and 0:0 exit code.
- Fifteen software-in-the-loop scenarios covering ordering, timestamp,
  non-finite value, range, frame, quaternion, rate, and watchdog faults.
- A checksum ledger covering the immutable evidence bundle.

The
[final evidence bundle](https://github.com/codemith/Physical-AI/tree/main/physical-ai-data/evidence/ur10-rsl-l40s-2026-08-29/final_bundle)
contains the logs, JSON reports, frozen configurations, source snapshots, and
checksums.
