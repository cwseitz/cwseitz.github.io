---
layout: post
title: Notes on Brownian Motion
date: 2024-10-19
description: Fokker-Planck Equation and Brownian Dynamics
tags: statistical mechanics, Brownian motion
categories: physics, mathematics
---

The Fokker-Planck equation is a central tool in non-equilibrium statistical mechanics, analogous to the master equation for discrete systems. It allows us to determine the time evolution of probability densities over continuous state spaces, with important examples found in biophysics like the phase space of a particle or the membrane potential of a nerve cell.

```math
\frac{d}{dt}\int_{V_{0}} P(\bm{x},t)dV = \int_{S}P(\bm{x},t)(\vec{J}\cdot\hat{n})dS = -\int_{V_{0}}P(\bm{x},t)(\nabla\cdot \vec{J})dV
```

This implies that:

```math
\frac{dP(\bm{x},t)}{dt} = -\left(\nabla\cdot \vec{J}\right)P(\bm{x},t)
```

The probability current $\vec{J}(\bm{x},t)$ is defined by:

```math
J(x_{i},t)  = \left(M_{i}^{(1)}(t) - \sum_{j}\frac{\partial}{\partial x_{j}}M_{ij}^{(2)}(t) \right)P(\bm{x},t)
```

The full multi-dimensional Fokker-Planck equation is:

```math
\frac{\partial P(\vec{x},t)}{\partial t}  = \sum_{i=1}^{N}\left(-\frac{\partial}{\partial x_{i}}\left[M_{i}^{(1)}(t)P(\vec{x},t)\right] + \frac{\partial^{2}}{\partial x_{i}^{2}}\left[M_{i}^{(2)}(t)P(\vec{x},t)\right] \right)
```

### Derivation in One Dimension

In one dimension, we have the simplified case where $\vec{J}$ reduces to scalar components. Let's start with the continuity equation, which ensures conservation of probability:

```math
\frac{\partial P(x,t)}{\partial t} = -\frac{\partial}{\partial x}J(x,t)
```

The current $J(x,t)$ depends on both the drift term $M^{(1)}(x,t)$ and the diffusion term $M^{(2)}(x,t)$:

```math
J(x,t) = M^{(1)}(x,t)P(x,t) - \frac{\partial}{\partial x} \left(M^{(2)}(x,t) P(x,t)\right)
```

Substituting into the continuity equation gives the one-dimensional Fokker-Planck equation:

```math
\frac{\partial P(x,t)}{\partial t} = -\frac{\partial}{\partial x}\left(M^{(1)}(x,t)P(x,t)\right) + \frac{\partial^{2}}{\partial x^{2}}\left(M^{(2)}(x,t)P(x,t)\right)
```

### Brownian Motion and the Langevin Equation

Brownian motion describes the random motion of particles suspended in a fluid resulting from collisions with the molecules of the fluid. The Langevin equation is a stochastic differential equation that describes the trajectory of such a particle under the influence of friction and random forces:

```math
m\frac{d^2x}{dt^2} = -\gamma \frac{dx}{dt} + \eta(t)
```

Here, $\gamma$ is the damping coefficient, and $\eta(t)$ is a random force that satisfies:

```math
\langle \eta(t) \rangle = 0, \quad \langle \eta(t)\eta(t') \rangle = 2\gamma k_B T \delta(t - t')
```

This corresponds to the overdamped regime where inertial effects can be neglected, reducing the Langevin equation to:

```math
\gamma \frac{dx}{dt} = \eta(t)
```

### Connection to the Fokker-Planck Equation

From the Langevin equation, we can derive the corresponding Fokker-Planck equation for the probability distribution $P(x,t)$. The drift and diffusion terms are related to the forces acting on the particle and the random fluctuations:

- The drift term $M^{(1)}(x,t)$ corresponds to systematic forces, such as friction.
- The diffusion term $M^{(2)}(x,t)$ corresponds to the random forces modeled by $\eta(t)$.

In the simple case of Brownian motion with constant coefficients, the Fokker-Planck equation becomes:

```math
\frac{\partial P(x,t)}{\partial t} = D \frac{\partial^2 P(x,t)}{\partial x^2}
```

where $D = \frac{k_B T}{\gamma}$ is the diffusion coefficient.

### Solving the Fokker-Planck Equation

For Brownian motion starting at $x_0$ at $t=0$, the solution to the Fokker-Planck equation is the Gaussian distribution:

```math
P(x,t) = \frac{1}{\sqrt{4\pi D t}} \exp\left(-\frac{(x-x_0)^2}{4Dt}\right)
```

This describes the spreading of the probability distribution over time, with a mean displacement $\langle x(t)\rangle = x_0$ and a variance $\langle x^2(t)\rangle - \langle x(t)\rangle^2 = 2Dt$.

### Brownian Dynamics Simulations

Brownian dynamics simulations are often used to model the motion of particles in a fluid, where the Langevin equation is integrated numerically. For a particle subject to both systematic and random forces, the velocity update is typically given by:

```math
v(t + \Delta t) = v(t)\left(1 - \frac{\gamma \Delta t}{m}\right) + \frac{F(t)\Delta t}{m} + \sqrt{2D\Delta t}R(t)
```

Here, $R(t)$ is a random number drawn from a Gaussian distribution with mean zero and variance one, ensuring that the random forces $\eta(t)$ are correctly modeled.

In conclusion, the Fokker-Planck equation provides a powerful framework for understanding the time evolution of probability densities in systems subject to stochastic forces, while the Langevin equation gives a more microscopic description of the trajectories of individual particles. Together, they form the foundation of our understanding of Brownian motion and related phenomena in statistical physics.

