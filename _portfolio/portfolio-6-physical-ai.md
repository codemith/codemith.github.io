---
title: "Physical AI – OpenUSD, Isaac Lab, and Reinforcement Learning Pipeline"
excerpt: >-
  A reproducible robotics and reinforcement-learning pipeline combining
  OpenUSD scene contracts, deterministic synthetic-data planning, shared
  analytical/Isaac Lab point-reach semantics, and headless PhysX validation on
  an NVIDIA L40S.
collection: portfolio
permalink: /portfolio/physical-ai/
order: 6
---

Physical AI is a reproducible reference implementation for connecting source
assets, OpenUSD scene composition, deterministic synthetic-data planning,
reinforcement-learning contracts, and simulator validation.

The project separates a portable Python workflow from optional NVIDIA Isaac Lab
execution so metadata planning, simulator evidence, and future robot deployment
remain clearly distinguished.

<p>
  <a class="btn btn--primary" href="#architecture">Architecture</a>
  <a class="btn" href="#reinforcement-learning">Reinforcement Learning</a>
  <a class="btn" href="#verified-results">Verified Results</a>
</p>

## Problem

Physical AI workflows cross asset formats, coordinate frames, calibration,
simulation runtimes, datasets, policies, and hardware. Small inconsistencies in
units, versions, timing, or preprocessing can invalidate downstream results.
This project makes those boundaries explicit through versioned contracts,
deterministic generation, validation, checksums, and artifact lineage.

## My Contributions

- Designed composable OpenUSD robot and workcell examples with explicit scale,
  coordinate, calibration, identity, and version metadata.
- Built a deterministic JSONL scenario planner with bounded domain
  randomization, data splits, SHA-256 checksums, and reproducible manifests.
- Implemented validation for paths, schemas, units, frames, calibration,
  distributions, provenance, execution claims, and generated artifacts.
- Created a shared point-reach reinforcement-learning contract across an
  analytical CPU environment and an Isaac Lab/PhysX rigid-body proxy.
- Added pinned container and scheduler workflows for repeatable headless Isaac
  Lab validation on GPU infrastructure.

## Architecture

![Physical AI pipeline showing the portable contract layer, verified headless proxy, and staged simulator, training, and deployment gates.](/images/projects/physical-ai-architecture.svg)

The portable workflow normalizes source inputs, composes OpenUSD assets, creates
deterministic scenario plans, and records validation evidence. The optional
Isaac Lab adapter preserves the same observation, action, timing, reset,
randomization, and reward contracts while replacing analytical dynamics with a
PhysX rigid body.

## Reinforcement Learning

The project defines `PhysicalAI-PointReach-v0`, an analytical two-dimensional
point-reach environment used to make the learning contract inspectable before
moving it into a heavier simulator.

- The policy observes planar position, velocity, and target displacement as a
  six-value vector.
- It produces two normalized force commands that are clipped before entering
  the analytical dynamics or Isaac Lab adapter.
- Named reward terms cover progress, remaining distance, action magnitude,
  velocity, settled success, and workspace violations.
- Seeded resets support domain randomization over initial state, target, mass,
  damping, actuator gain, observation noise, and action delay, with a
  three-level curriculum.
- Random and PD controllers provide classical baselines; an optional
  Stable-Baselines3 PPO workflow adds configuration snapshots, multi-condition
  evaluation, and hash-bound policy lineage.

The Isaac Lab proxy maps the same observation, action, reward, reset, and
termination semantics to a force-driven PhysX rigid body. This establishes a
testable analytical-to-simulator contract; it does not claim a trained Isaac
policy, articulated-robot control, or sim-to-real performance.

## Technical Highlights

- Python 3.10 standard-library core
- Human-readable USDA scene composition with an illustrative URDF source asset
- Deterministic synthetic-data planning
- JSONL manifests and SHA-256 artifact lineage
- Gymnasium and Stable-Baselines3 integration
- Isaac Sim 6.0.1 and Isaac Lab 3
- PhysX/CUDA headless simulation
- SLURM and Apptainer launch workflows
- Automated contract, integration, and asset-validation tests

## Verified Results

- Recorded 80 passing portable tests with 15 expected optional-dependency skips.
- Recorded 11 passing offline Isaac integration and contract tests without
  launching Kit or PhysX.
- Completed a finite headless smoke test with four parallel environments over
  120 control steps on one NVIDIA L40S.
- The smoke test exited successfully with no reported CUDA or PhysX error.
- Strict pipeline and generated-manifest validation completed with zero errors
  and zero warnings.

## Scope and Next Steps

The current Isaac Lab task is a force-driven rigid-body proxy, not an
articulated production robot. The verified run establishes simulator startup,
task registration, reset, and finite stepping. It does not claim graphical UI
validation, rendered datasets, PPO training quality, sim-to-real transfer, or
physical deployment.

Next steps include authoritative articulated assets, Replicator rendering,
held-out policy evaluation, ROS 2 interfaces, SIL/HIL testing, and staged
hardware safety validation.
