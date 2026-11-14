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
