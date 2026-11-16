# Installation on STOKES

Load modules
```
> module load scalapack/scalapack-2.2.3-openmpi-4.1.5-gcc-12.2.0

> module list

1) gcc/gcc-12.2.0
2) hpcx/hpcx-2.25.1
3) openmpi/openmpi-4.1.5-gcc-12.2.0
4) openblas/openblas-0.3.25-gcc-12.2.0
5) scalapack/scalapack-2.2.3-openmpi-4.1.5-gcc-12.2.0
```

Install Quantum Espresso
```
> cd qe-7.5
> ./configure --with-scalapack=yes
> make all
```

Install QE-CONVERSE
```
> ./configure --with-qe-source=~/qe-7.5
> make
```


# Installation on ANVIL

Load modules
```
> module load aocc/3.1.0
> module load openmpi/4.0.6
> module load amdscalapack/3.0

> module list

1) xalt/2.10.45 (S)
2) modtree/cpu
3) aocc/3.1.0
4) zlib/1.2.11
5) numactl/2.0.14
6) libfabric/1.12.0
7) openmpi/4.0.6
8) amdscalapack/3.0
```

Install Quantum Espresso
```
> cd qe-7.5_ScaLapack
> ./configure --with-scalapack=yes
> make all
```

Install QE-CONVERSE
```
> ./configure --with-qe-source=~/qe-7.5_ScaLapack
> make
```


# The code is modified

src/newscf.f90 (SCF inside QE-CONVERSE):
```
starting_pot='file': the SCF starts from the converged pw.x density instead of the atomic one.
imix=2: local-TF mixing instead of plain.
nmix=12, niter=300 (were 8 and 100).
```

[src/calc_orbital_magnetization.f90](https://github.com/Dmitry-Skachkov/QE-CONVERSE/blob/main/src/calc_orbital_magnetization.f90) (calc_g_tensor):
```
The number of unpaired electrons (unp_ele) is now taken from the occupations (sum of wg, spin up minus spin down), not from nint(tot_magnetization). Without tot_magnetization (smearing runs), the old code divided Δg by −10000.
If tot_magnetization is set, the old integer value is kept.
unp_ele is now a real number, printed as a decimal, and the code stops with an error if it is zero.
```
