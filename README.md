# 2DWavePINN
---
## Introduction
---
* This project investigates how we can apply ___Physics-Informed Neural Networks___ to solving the __2D Wave Equation__.

## Theory
---
### The Wave Equation
* The wave equation is a __linear 2nd-order hyperbolic partial differential equation__ describing waves, including __traveling__ and __standing waves__.
* The 2D wave equation takes the form:
   * `d^2u/dt^2 = c^2(d^2u/dx^2 + d^2u/dy^2)`, where:
   * `u` represents the wave-displacement field,
   * `c` represents the wave-speed,
   * `t`  repesents time and
   * `x` & `y` represent the spacial derivates.

### Physics-Informed Neural Networks
* ___Physics-Informed Neural Networks___ are a type of ___neural network___ that solve __differential equations__ by __embedding physical laws__ into the __loss function__ of the network.
* This means:
    * You don't need large datasets.
    * The model learns a *continuous solution* over the domain.
    * It generalizes well to unseen points in space and time.
* TODO.
      
## Requirements
---
* __Compiler__: `g++ 13.1.0`. A compiler that supports `C++17`.
* __OS__: Project will be developed on `Ubuntu 20.04`.
* __Eigen Template Library__: Version `3.3.7` for the Linear Algebra.
* __CMake__: version `4.0.2`.

## Getting and Using the Software
* `$ git clone git@github.com:MRLintern/2DWavePINN.git`
* `$ cd 2DWavePINN`
* `$ mkdir build -p && cd build`
---
