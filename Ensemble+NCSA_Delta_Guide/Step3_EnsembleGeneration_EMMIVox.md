# Ensemble Generation on EMMIVox
After completing single refinement you can now proceed to ensemble generation. This step is unique in that it requires parallelization. Current guidelines recommends at least 8 CPU cores and 16 GB of RAM for each replicate. An ideal set-up is the following:
16 replicates at 10ns each for a total of 160ns sampling.

A40x4 GPU nodes have the following specifications:
4x A40 (48gb GDDR6 with ECC) GPUs per node
AMD Milan CPU with 64 CPU cores (Simultaneous Multing Threading, SMT is off)
256GB RAM

EMMIVox benchmarks share 2 GPUs per replicate, so to replicate we will request 2 compute nodes. This leaves the following resources available for each run:
* 1 shared A40 GPU (with another replicate)
* 8 CPU cores
* 32 GB of RAM

For smaller systems, it may be okay to run all 16 replicates on 1 node which will leave the following allocation:
* 1 shared A40 GPU (with three other replicates)
* 4 CPU cores
* 16 GB of RAM

I have only tried ensemble generation with the first set-up (16 replicates across two nodes) so I am not sure of the feasability of a compact replicate. A target of 160ns of total simulation time provides sufficient data, you may also lower the number of replicates but increase the run time of each replicate.

In other words, the number of replicates and simulation runtime is inversely related. If the number of replicates decreases, the simulation runtime must increase to compensate for the missed sampling.

`.slurm` scripts are available in the sample project directory.