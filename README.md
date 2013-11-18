Slater-Condon
=============

Files for the Slater-Condon paper 2013. The Intel Fortran compiler and the
GNU C compiler are needed.

To run the benchmarks, run

  make tests

This command will build the four benchmarks:

* test_cu_avx
* test_cu_sse2
* test_h2o_avx
* test_h2o_sse2

The output should look like this:

    ==============
    Cu, SSE2
    ==============
    taskset -c 0 ./test_cu_sse2
     ndet =        10000
     Cycles n_excitations:   34.7540077400000       +/-   3.479021910893892E-005
     CPU    n_excitations:   1.12000000000000     
               0
     Cycles get_excitation:   40.2044544800000       +/-   4.030457234270350E-005
     CPU    get_excitation:   1.29000000000000     
     Cycles zero   :   30.4083702667599       +/-   1.008247307982627E-004
     Cycles single :   87.7390566250000       +/-   1.829049539625737E-003
     Cycles double :   144.569855767367       +/-   1.169988940582419E-004
     Cycles other  :   30.2330823827413       +/-   1.726071165104671E-005
     Cycles density matrix :    38.7053945194519     
     CPU    density matrix :   0.620000000000001     
    ==============
    Cu, AVX
    ==============
    taskset -c 0 ./test_cu_avx
     ndet =        10000
     Cycles n_excitations:   5.10230640000000       +/-   5.165095393066429E-006
     CPU    n_excitations:  0.170000000000000     
               0
     Cycles get_excitation:   8.66424608000000       +/-   8.905112566651616E-006
     CPU    get_excitation:  0.280000000000000     
     Cycles zero   :   4.93462403836547       +/-   1.572017678605744E-005
     Cycles single :   46.2361855000000       +/-   9.642070951752019E-004
     Cycles double :   78.7195363408724       +/-   6.373098925677101E-005
     Cycles other  :   5.54228558173953       +/-   3.202738133568022E-006
     Cycles density matrix :    6.53137199719972     
     CPU    density matrix :   0.110000000000000     
    ==============
    H2O, SSE2
    ==============
    taskset -c 0 ./test_h2o_sse2
     ndet =        10000
     Cycles n_excitations:   72.4396000700000       +/-   7.250726495869192E-005
     CPU    n_excitations:   2.34000000000000     
               0
     Cycles get_excitation:   81.2813032900000       +/-   8.146127076930712E-005
     CPU    get_excitation:   2.62000000000000     
     Cycles zero   :   58.5725555999600       +/-   1.862427473250057E-004
     Cycles single :   126.333416652778       +/-   1.758400588223553E-003
     Cycles double :   194.749878845180       +/-   1.650472976311530E-004
     Cycles other  :   63.7100840413763       +/-   3.530620172058838E-005
     Cycles density matrix :    76.8598384438444     
     CPU    density matrix :    1.24000000000000     
    ==============
    H2O, AVX
    ==============
    taskset -c 0 ./test_h2o_avx
     ndet =        10000
     Cycles n_excitations:   10.1925470600000       +/-   1.034849403182130E-005
     CPU    n_excitations:  0.330000000000000     
               0
     Cycles get_excitation:   18.1355976500000       +/-   1.843817205266690E-005
     CPU    get_excitation:  0.590000000000000     
     Cycles zero   :   6.19700369667299       +/-   1.990164909991091E-005
     Cycles single :   51.8508057777778       +/-   7.221451379202684E-004
     Cycles double :   88.6343955596826       +/-   7.506068582786541E-005
     Cycles other  :   6.70027751963713       +/-   3.742039226306923E-006
     Cycles density matrix :    11.6624591059106     
     CPU    density matrix :   0.190000000000000   


Source files:
-------------

* nsubst1.x.f90 : Find the number of substitutions between two determinants
* exc0.x.f90 : Dispatch function for getting the excitation operator from determinants
* exc1.x.f90 : Finds the single excitation operator
* exc2.x.f90 : Finds the double excitation operator
* density_matrix.x.f90 : Computation of the one-electron density matrix
* rdtsc.c : Get number of CPU cycles from hardware counter

Data Files
-----------

* cu.dat   : 10 000 determinants obtained from CIPSI in cc-PVDZ basis set for the Cu atom
* cu.coef  : CI Coefficients
* h2o_determinants.dat : 10 000 determinants obtained from CIPSI in cc-PVTZ basis set for the water molecule



