# Parallel Pattern: Map

- replicates elemental function over every element of index set
- map replaces iterations of independent loops
- elemental functions should not modify global data that other instances (iterations) depend on
- examples:
  - gamma correction in images, color space conversions
  - Monte Carlo sampling, ray tracing
- map applies an elemental function to every element of a collection of data in parallel
  - elemental functions should have no side effects
  - no dependency among elements
  - can execute in any order
- embarrassingly parallel
  - one of the most efficient patterns
  - if you have many problems to solve, parallel solution can be as simple as running problems (serial code) on parallel execution nodes
- Typically combined with other patterns
  - map does the basic computation, other patters follow
  - gather = serial random read + map, reduction, scan
- serial and parallel execution of the map pattern
- scalable implementation of map
  - a lot of care for best performance
  - threads
    - mandatory parallelism
    - separate thread for each element is not a good idea
  - tasks
    - optional parallelism
    - overhead and synchronization at the beginning and at the end when elemental functions vary in the amount of work
- the map pattern is a basis for vectorization and parallelization
- example: Map-reduce, Google’s big success
- map is related to SIMD, SPMD, SIMT
  - can be expressed as a sequence of vector operations
- parallel for construct in programming languages
  - map is parallelization of the serial iteration pattern where iterations are independent
- if dependencies and side-effects are avoided, map is deterministic

#ß# Monte Carlo $\Pi$

- Integration
  - random shooting to the square

    <img src="figures/MonteCarloPi.png" alt="Monte Carlo Pi" width="70%">

  - number of hits - shots inside the circle is proportional to 𝜋/4
  - slow convergence, relative accuracy is 1/\square(shots)
  - a shot is basic unit of work that can be parallelized is one shot
    - a lot of overhead
    - better is to combine several shots to one task
