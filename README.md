## AstraSched
Game-Theoretic GPU Cluster Scheduling Simulator
AstraSched is a research-oriented simulation framework for studying how strategic user behavior affects GPU cluster scheduling.
The system compares baseline scheduling policies with a simplified incentive-aware mechanism inspired by auction-based allocation.
The simulator measures how different policies affect:
fairness
- waiting time
- GPU utilization
- social welfare

## Table of Contents 
- [Overview](#overview)
- [Research Motivation](#research_motivation)
- [Project Goals](#project_goals)
- [Simulator Architecture](#simulator_architecture)
- [Scheduling Policies](#scheduling_policies)
- [Matrics](#matrics)
- [Experiment Design](#experiment_design)
- [How to Run](#how_to_run)
- [Sample Results](#sample_results)
- [Future Work](#future_work)
---

## Overview 
AstraSched models a shared GPU cluster where multiple users submit jobs competing for limited resources.
The simulator evaluates how scheduling policies perform when users:
 - report job priorities truthfully
 - exaggerate job urgency strategically
The system runs controlled experiments to analyze fairness and efficiency in resource allocation.

## Research Motivation
Modern ML workloads rely heavily on shared GPU clusters.
In many systems:
 - GPUs are scarce
 - users compete for resources
 - priority is self-reported
This creates a strategic environment where users may inflate job importance to obtain faster scheduling.
AstraSched explores how mechanism design and game theory can improve scheduling decisions in such environments.

## Project Goals
AstraSched aims to:
 - simulate a shared GPU cluster environment
 - model truthful and strategic user behavior
 - implement baseline and incentive-aware schedulers
 - evaluate fairness and efficiency of allocation policies
 - demonstrate how mechanism design impacts system performance

## Simulator Architecture 
The simulator uses a modular architecture designed for controlled experimentation.
Core components:
 Component	           Responsibility
 - Job Generator	     : Creates workloads from multiple users
 - Cluster Model	     : Tracks GPU availability and running jobs
 - Scheduler	         : Selects jobs for execution
 - Mechanism Module	  : Implements incentive-aware allocation
 - Metrics Engine	    : Computes system performance metrics
 - Visualization	     : Generates experiment plots

## Scheduling Policies
AstraSched evaluates three allocation strategies.
- FIFO
Schedules jobs in arrival order.
Baseline policy used in many queueing systems.
- Priority
Schedules jobs based on reported priority.
Strategic users can manipulate this policy.
- Incentive-Aware
Allocates GPUs using a normalized value score:
    score = reported_value / gpu_demand
This mechanism discourages extreme priority inflation and improves fairness

## Metrics
Experiments evaluate system performance using the following metrics.
 Metric	                Description
 - Average Waiting      : Time	Time between job submission and execution
 - GPU Utilization	     : Percentage of time GPUs are active
 - Fairness Index	      : Distribution of resource allocation among users
 - Social Welfare	      : Total value of completed jobs
These metrics capture both efficiency and fairness.

## Experiment Design
The simulator runs three primary experiment sets.
Scheduler Comparison
Compare:
  - FIFO
  - Priority
  - Incentive-Aware
Measure fairness, waiting time, utilization, and welfare.

Strategic Behavior
Simulate different user types:
  - truthful users
  - strategic users
  - mixed populations
Evaluate how manipulation affects scheduling outcomes.

Cluster Scaling
Test scheduler performance under different resource availability.
Example configurations:
      GPUs = 4
      GPUs = 8
      GPUs = 32
This shows how policies behave as system scale increases.

## How to Run
- Install dependencies:
    pip install -r requirements.txt
- Run experiments:
    python run_experiments.py
- Generated outputs appear in:
    results/plots

## Sample Results
Example experiment outputs include:
- waiting time comparison across schedulers
- GPU utilization across cluster sizes
- fairness comparison under strategic behavior
- social welfare across policies
These results demonstrate how incentive-aware scheduling improves fairness and efficiency.

## Future Work
Possible extensions include:
- implementing auction-based payment mechanisms
- modeling heterogeneous GPU clusters
- incorporating real workload traces
- exploring reinforcement learning schedulers
