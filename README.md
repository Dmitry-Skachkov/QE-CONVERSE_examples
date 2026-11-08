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
>
```

Install QE-CONVERSE
```
> ./configure --with-qe-source=~/qe-7.5
> make
```
