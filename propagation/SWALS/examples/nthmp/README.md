Benchmark problems from the National Tsunami Hazard Mitigation Program (NTHMP) test suite
-----------------------------------------------------------------------------------------

Most of the test problems here were set-up based on problem descriptions in this [NTHMP benchmarking repository](https://github.com/rjleveque/nthmp-benchmark-problems) and the [NTHMP tsunami currents benchmarking problems website](http://coastal.usc.edu/currents_workshop/index.html). Please consult these sources for detailed problem descriptions and data.

The problems are:

* BP01 -- Solitary wave runup on a simple beach. This is a 1D runup problem with an analytical solution. The `run_model.sh` script compiles and runs the model, and makes a plot comparing the analytical and numerical solutions. See problem description [here](https://github.com/rjleveque/nthmp-benchmark-problems/blob/master/BP01-DmitryN-Single_wave_on_simple_beach/description.pdf).

* BP02 and BP05 -- Solitary wave on a composite beach. This is a 1D wave propagation problem, which has an exact analytical solution for the linear shallow water equations ([see here for the linear problem](https://github.com/rjleveque/nthmp-benchmark-problems/blob/master/BP02-DmitryN-Solitary_wave_on_composite_beach_analytic/description.pdf)). There is [another variant of this problem which uses experimental data](https://github.com/rjleveque/nthmp-benchmark-problems/blob/master/BP05-ElenaT-Solitary_wave_on_composite_beach_laboratory/BP5_description.pdf), and is often called BP05. Our `run_model.sh` script compares both the analytical solution and the data with results from several SWALS solvers.

* BP04 -- This is a [laboratory counterpart of BP01](https://github.com/rjleveque/nthmp-benchmark-problems/blob/master/BP04-JosephZ-Single_wave_on_simple_beach/Benchmark4_description.pdf). The `run_model.sh` script compares the model with observations for a number of scenarios, and the code makes a plot comparing the wave-height vs runup relation (both divided by the depth) in the models and data.

* BP06 -- This is an experiment with [three cases of wave runup on a conical island](https://github.com/rjleveque/nthmp-benchmark-problems/tree/master/BP06-FrankG-Solitary_wave_on_a_conical_island). The `run_model.sh` script compares the modelled and observed wave time-series at a number of points, and the modelled and observed runup around the island. We also include results from other models using the same initial condition.

* BP07 -- This is [an experiment that was used to understand the surprisingly high runup of the 1993 Okushiri tsunami around Monai Valley](https://github.com/rjleveque/nthmp-benchmark-problems/blob/master/BP07-DmitryN-Monai_valley_beach/Matsuyama_Tanaka2001.pdf). The `run_model.sh` script compares modelled and observed wave time-series at a number of sites, and also compares the runup maxima, and several snapshots of the wave during runup.

* BP09 -- This is [a field-scale representation of the 1993 Okushiri tsunami](https://github.com/rjleveque/nthmp-benchmark-problems/blob/master/BP09-FrankG-Okushiri_island/Description.pdf). The `run_model.sh` script compares modelled and observed runup around the island using both openmp and mixed openmp/MPI verisons of the code, with default domain partitioning (which depends on the parallel approach). The `run_model_exact_reproduce.sh` script does the same using a manual domain partitioning that is identical in both cases, and enables identical results to be obtained on output grids for both two variants of the model. If the domain partitions differ then we have tiny changes in the model geometry due to the inexactness of floating point, and this affects the results by an unimportant small amount (similar changes in the results can be induced by adding a tiny random perturbation to the elevation, with range +- 0.0000000001). In both cases the models are compared with data, and with each other.

* Conical_shelf_lab -- This simulates an experiment where a solitary wave propagates up a triangular shelf with an island, following [this description](http://coastal.usc.edu/currents_workshop/problems/prob5.html). 

* Hilo_Tohoku_Tsunami -- This implements a semi-idealised model of the Tohoku tsunami in Hilo, Hawaii, following [this description](http://coastal.usc.edu/currents_workshop/problems/prob2.html). The `run_model.sh` script runs two versions of the code (openmp and mixed openmp/MPI -- here both use the same domain partitioning and so give identical results) and compares both with data (waves and currents), and with each other.

* Seaside_OSU_model -- This models a wave-tank experiment where a wave propagates up a sloping beach and inundates a city, following [this description](http://coastal.usc.edu/currents_workshop/problems/prob4.html). 

* Submerged_Island_Lab -- This models turbulent flow past a submerged bathymetric rise, following [this description](http://coastal.usc.edu/currents_workshop/problems/prob1.html)

* Tauranga_harbour_Tohoku_Tsunami -- This models the Tohoku tsunami in Tauranga Harbour, New Zealand, following [this description](http://coastal.usc.edu/currents_workshop/problems/prob3.html). The `run_model.sh` script runs two versions of the code (openmp and mixed openmp/MPI with default domain partitioning) and compares both with data (waves and currents), and with each other.

