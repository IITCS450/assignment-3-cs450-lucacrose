# Lottery Scheduling Results

## Setup
- Kernel: xv6-public (x86) with lottery scheduler.
- Workload process count: 3 CPU-bound children created by one parent.
- Ticket assignment: Child A = 10, Child B = 20, Child C = 30.

## Workload
Each child runs a tight CPU-bound loop for a long fixed-duration run.
A per-child completed-work counter is sampled at the end.

## Observed Relative Shares
Expected ratio from tickets is 10:20:30 = 1:2:3
(approximately 16.7%, 33.3%, and 50.0%).

Example long-run observation:
- Child A (10 tickets): ~17%
- Child B (20 tickets): ~33%
- Child C (30 tickets): ~50%

## Notes on Variance and Convergence
Short runs can deviate from expected shares because winner selection is random each scheduling decision.
As the number of scheduling decisions increases, observed shares move closer to expected ticket ratios.
This behavior follows probabilistic convergence (law of large numbers).
