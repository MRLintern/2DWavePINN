# 2DWavePINN
---
## Introduction
---
* This project investigates how we can apply ___Physics-Informed Neural Networks___ to solving the __2D Wave Equation__.
* Note: this is a work-in-progress.

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
* A ___Physics-Informed Neural Network (PINN)___ is a __machine learning__ approach that solves __differential equations__ by __embedding physical laws__ directly into the __training process__ of a __neural network__.

* Instead of just learning from data, the __PINN learns a function u(x, y, t)__ that __approximately__ satisfies the governing __partial differential equation (PDE)__ and __boundary/initial conditions__.
* This is achieved by __minimizing__ a __composite loss function__ that combines __data fitting__ (if available) and the __residuals__ of the __PDE__.

#### How the PINN Works
##### 1. Neural Network as Function Approximator
* Define a neural network:

    `u_theta(x, y, t) ~ u(x, y, t)`
  
* Inputs: `(x, y, t)`.
* Output: Predicted wave value `u`.
* Architecture: Fully connected network with `tanh` activations; Note: `tanh` is the __hyperbolic tangent function.

##### 2. Automatic Differentiation
* Using a custom __dual number implementation__, compute:
    * First and second order partial derivatives: `du/dt`, `d^u/dx^2` and `d^2u/dy^2`.
    * No need for symbolic or finite difference methods.
    * Enables precise calculation of PDE residuals during training.
 
##### 3. Loss Function Components
* `Total loss` = `PDE residual loss` + `initial condition loss` + `boundary condition loss`.

    * __Physics Loss__: `Total Loss` = `|| d_tt u_theta - C^2*(d_xx u_theta + d_yy u_theta ||^2`.
    * __Initial condition loss__: `u(x, y, t) = 0`, `d_t u(x, y, t) = 0`.
    * __Homogeneous Neumann or Dirichlet boundary conditions__: `du/dn = 0` (__Neumann__), `u = 0` (__Dirichlet__).

##### 4. Training Process
* Sample __collocation points__ `(x, y, t)` from the domain.
* Evaluate loss using __AD__ and __compute gradients__ manually (__backpropagation__).
* Update __weights__ using __gradient descent__ (e.g., __Adam__).
      
      
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
