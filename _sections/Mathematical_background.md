---
layout: default
title: "Mathematical background"
---

### Mathematical background

Simulations based on the Boltzmann or Navier-Stokes Cahn-Hilliard equations are complex and multifaceted. The part that will be accelerated using GPGPU techniques is the solving of systems of non-linear equations.

#### Bilinear form

The weak and discretized formulations of the Boltzmann and Navier-Stokes Cahn-Hilliard equations can be abstracted to the following:

$$
\begin{array}{lr}
a( \sum_{j=1}^{m} u_{k}^{j} \psi_{j} ; \psi_{i} ) = f(\psi_{i}) & \forall i \in \left [ 1,m \right ]
\end{array}
$$

  * $a(\cdot \, ; \cdot)$ is the bilinear form.
  * $u_{k}^{j}$ is the solution at time $k$, on location $j$.
  * $\psi_{i}$ is the i *th* test function.
  * $m$ is the total amount of test functions.

Which can be expressed by the following system of non-linear equations:

$$
N(\underline{u_{k}}) = \underline{f}
$$

With $\underline{u_{k}} = \left [ u_{n}^{1} \,,u_{n}^{2} \,,...\,,u_{n}^{m} \right ]$.

This system of non-linear equations needs to be solved for every time step, using the Newton-Raphson method.

#### Newton's method

Applying Newton's method for timestep $k$ results in a sequence of iterations containing (at iteration $n + 1$) the following system:

$$
J_{N}(\underline{u_{k,n}}) (\underline{u_{k,n+1}} - \underline{u_{k,n}}) = - N(\underline{u_{k,n}}) + \underline{f}
$$

  * $n$ is the iteration counter.
  * $J_{N}$ is the Jacobian matrix of $N$.

Which is of the canonical form:

$$
A\,x=b
$$

#### Solving

The acceleration of the Boltzmann or Navier-Stokes Cahn-Hilliard equations will focus on improving the performance of the step where the system $A\,x=b$ is solved.

#### Defect correction

The objective is to solve a linear system of equations:

$$
A\,x=b
$$

The problem is that the system is very difficult to solve. One approach would be to use a defect correction method. Instead of solving the original system, an easier system will be solved:

$$
\widetilde{A}\,x=b
$$

The solution to this, $x_{k}$, is an approximation to the solution of the original system, with an accompanying residual:

$$
r_{k} = A\,x_{k} - b
$$

The update required to get the solution of the original system would be the solution of the following system:

$$
A\,\Delta x = r_{k}
$$

But again, this is to difficult, so the update is calculated by solving the following system:

$$
\widetilde{A}\,\Delta x = r_{k}
$$

Resulting in an iterative process:

$$
x_{k+1} = (\widetilde{A}^{-1} A - I)x_{k} - \widetilde{A}^{-1}b
$$

For this to work, two conditions must be satisfied:

  * $\widetilde{A}$ must be easy to invert.
  * $\widetilde{A}$ must sufficiently resemble $A$ to get convergence.

