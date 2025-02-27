# NTHMP test problems 2 and 5: Solitary wave on a composite beach (analytical solution and experiment)

This problem covers benchmarks 2 and 5 from the NTHMP test suite. The test data
and a problem description is available in 
[Randy LeVeque's repository](https://github.com/rjleveque/nthmp-benchmark-problems/tree/master/BP02-DmitryN-Solitary_wave_on_composite_beach_analytic)

Three different solitary waves (cases A, B, C) are propagated over a 1D
composite beach. The analytical solutions are known for the linear shallow water
equations (NTHMP benchmark 2). Experiments have also been conducted for this setup
(NTHMP benchmark problem 5). Herein we combine these cases, by simultaneously 
comparing models with the linear analytical solution and experiments.

![Figure 1: Beach profile and gauge locations](https://github.com/GeoscienceAustralia/ptha/blob/figures/propagation/SWALS/examples/nthmp/BP02_and_BP05/solution_geometry_caseA_linear.png)

Mathematically we expect solutions based on the nonlinear shallow water
equations to deviate from the linear solution for this problem. Physically, nonlinearity is
significant because the wave amplitudes are not negligible compared
to the depth (especially for cases B and C). Dispersion also matters physically
because the wave length is not very long short compared to the water depth
(moreso for cases B and C). Dispersion causes short waves to form in the
experiments, over regions where non-dispersive nonlinear shallow water models predict
shock formation.

The [SWALS model](BP2_testcases.f90) is setup to take the numerical method as a commandline
argument. This is used to test the linear shallow water solver (`linear`) as well as two
nonlinear shallow water solvers (`rk2` and `leapfrog_nonlinear`).

## Linear solution

Here we test the `linear` scheme, which should give excellent agreement with the analytical solution
derived from the linear shallow water equations.

![Figure 2: Comparison of analytical, experimental, and SWALS linear solutions for case A](https://github.com/GeoscienceAustralia/ptha/blob/figures/propagation/SWALS/examples/nthmp/BP02_and_BP05/solutionA_linear.png)

![Figure 3: Comparison of analytical, experimental, and SWALS linear solutions for case B](https://github.com/GeoscienceAustralia/ptha/blob/figures/propagation/SWALS/examples/nthmp/BP02_and_BP05/solutionB_linear.png)

![Figure 4: Comparison of analytical, experimental, and SWALS linear solutions for case C](https://github.com/GeoscienceAustralia/ptha/blob/figures/propagation/SWALS/examples/nthmp/BP02_and_BP05/solutionC_linear.png)

## Nonlinear solutions - `rk2`

Here we test the `rk2` finite volume scheme, which solves the nonlinear shallow water equations. 

In this problem nonlinear terms are not negligible, so we expect the numerical
solution to differ from the analytical linear solution.  The model also differs
significantly from the experiments due to dispersion, which is absent in the
model, but physically tends to suppress shock formation. Our modelled results are similar
to those [reported in the GEOCLAW nonlinear shallow water solver for benchmark 5](https://depts.washington.edu/clawpack/links/nthmp-benchmarks/geoclaw-results.pdf). 

![Figure 5: Comparison of analytical, experimental, and SWALS nonlinear solutions for case A](https://github.com/GeoscienceAustralia/ptha/blob/figures/propagation/SWALS/examples/nthmp/BP02_and_BP05/solutionA_rk2.png)

![Figure 6: Comparison of analytical, experimental, and SWALS nonlinear solutions for case B](https://github.com/GeoscienceAustralia/ptha/blob/figures/propagation/SWALS/examples/nthmp/BP02_and_BP05/solutionB_rk2.png)

![Figure 7: Comparison of analytical, experimental, and SWALS nonlinear solutions for case C](https://github.com/GeoscienceAustralia/ptha/blob/figures/propagation/SWALS/examples/nthmp/BP02_and_BP05/solutionC_rk2.png)


## Nonlinear solutions - `leapfrog_nonlinear`

Here we test the `leapfrog_nonliear` finite difference scheme, which solves the
nonlinear shallow water equations. 

The numerical solution is almost identical to the `rk2` solution above, which
is unsurprising as both are solving the nonlinear shallow water equations.

In this problem nonlinear terms are not negligible, so we expect the numerical
solution to differ from the analytical linear solution.  The model also differs
significantly from the experiments due to dispersion, which is absent in the
model, but physically tends to suppress shock formation. Our modelled results are similar
to those [reported in the GEOCLAW nonlinear shallow water solver for benchmark 5](https://depts.washington.edu/clawpack/links/nthmp-benchmarks/geoclaw-results.pdf). 

![Figure 8: Comparison of analytical, experimental, and SWALS nonlinear solutions for case A](https://github.com/GeoscienceAustralia/ptha/blob/figures/propagation/SWALS/examples/nthmp/BP02_and_BP05/solutionA_leapfrog_nonlinear.png)

![Figure 9: Comparison of analytical, experimental, and SWALS nonlinear solutions for case B](https://github.com/GeoscienceAustralia/ptha/blob/figures/propagation/SWALS/examples/nthmp/BP02_and_BP05/solutionB_leapfrog_nonlinear.png)

![Figure 10: Comparison of analytical, experimental, and SWALS nonlinear solutions for case C](https://github.com/GeoscienceAustralia/ptha/blob/figures/propagation/SWALS/examples/nthmp/BP02_and_BP05/solutionC_leapfrog_nonlinear.png)
