---
title: "Physical AI - Reinforcement Learning and Robot Simulation"
excerpt: >-
  A reproducible Isaac Lab project for training and evaluating a UR10e reach
  policy, with a separate 4K autonomous pick-and-place demonstration.
collection: portfolio
permalink: /portfolio/physical-ai/
order: 2
---

I built this project to connect reinforcement learning with an actual robotics
workflow: define the task, train a policy, and test it under harder
conditions. It runs in NVIDIA Isaac Lab on a Palmetto L40S GPU.

<p>
  <a class="btn btn--primary" href="#demos">Watch the demos</a>
  <a class="btn" href="#results">See the results</a>
  <a class="btn" href="{{ '/portfolio/physical-ai/results/' | relative_url }}">Detailed results</a>
  <a class="btn" href="https://github.com/codemith/Physical-AI">GitHub</a>
</p>

## Demos

### UR10e PPO reach policy

<video controls playsinline preload="metadata" style="width: 100%; height: auto; border-radius: 8px;">
  <source src="{{ '/assets/videos/physical-ai/ur10-ppo-reach-4k.mp4' | relative_url }}" type="video/mp4">
  Your browser does not support embedded MP4 video.
</video>

The six-joint UR10e is controlled by a PPO policy trained with RSL-RL. The
policy observes the robot and target state, then produces joint-position
commands at 30 Hz while PhysX runs at 120 Hz.

### Autonomous 4K pick-and-place

<video controls playsinline preload="metadata" style="width: 100%; height: auto; border-radius: 8px;">
  <source src="{{ '/assets/videos/physical-ai/pick-and-place-4k.mp4' | relative_url }}" type="video/mp4">
  Your browser does not support embedded MP4 video.
</video>

This separate controller uses a surface gripper and a deterministic state
machine to lift, carry, and place a cube. I kept it separate from the RL demo so
the project does not label scripted behavior as learned behavior.

## What I Built

- A manager-based Isaac Lab task for a six-joint UR10e with a 25-value
  observation space and six continuous actions.
- RSL-RL PPO training, checkpoint selection, and repeatable evaluation across
  nominal, randomized, and stress conditions.
- OpenUSD scene and data contracts, deterministic validation, and
  hash-tracked experiment artifacts.
- SLURM and Apptainer workflows for headless GPU runs, plus a software-only ROS
  2 safety boundary for validating commands and failure handling.

## Results

| Test | Measured result |
|---|---|
| UR10e policy evaluation | Passed all 9 reports: 3 seeds x nominal, randomized, and stress conditions |
| UR10e reach accuracy | 2.1-2.9 cm mean settled error; worst p95 error of 8.8 cm |
| Evaluation scale | 512 episodes and 44,800 settled samples per report |
| 4K pick-and-place | Successful 0.800 m lift with 0.129 m final target error |
| Safety fault suite | Passed 15/15 software-in-the-loop scenarios |
| GPU runtime | Verified in Isaac Lab on one NVIDIA L40S, including a standalone SLURM job |

The final UR10e policy is validated in articulated simulation. The project does
not claim physical-robot testing or sim-to-real deployment.

[View the detailed training and evaluation results.]({{ '/portfolio/physical-ai/results/' | relative_url }})

**Stack:** Python, PyTorch, RSL-RL, NVIDIA Isaac Sim/Isaac Lab, PhysX, OpenUSD,
Gymnasium, ROS 2-style contracts, Apptainer, and SLURM.
