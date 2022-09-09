# geogram.psm.OpenNL
geogram OpenNL pluggable software module

This is OpenNL Pluggable Software Module, extracted
from GEOGRAM source tree. It contains a standalone .cpp/.h
pair that can be used in any program and that does not have
any dependency. 

# Example program
It also contain an example program that can be compiled by using:
```
$ gcc -O3 -fopenmp -frounding-math -ffp-contract=off --std=c++11 OpenNL_example.c OpenNL_psm.c -o OpenNL_example -ldl -lm
```

# Documentation
- [OpenNL tutorial](https://github.com/BrunoLevy/geogram/wiki/OpenNL)
- [OpenNL reference](https://brunolevy.github.io/geogram/nl_8h.html)





