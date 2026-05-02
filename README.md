# Temperature Profile of Hawking Radiation

Numerical simulations of the thermal evolution and temperature profiles of plasma surrounding an evaporating Schwarzschild black hole.

## Overview

This repository contains Python implementations designed to numerically verify the theoretical estimates presented in:
**"Black Hole Production of Monopoles in the Early Universe"** ([arXiv:2109.00039](https://arxiv.org/abs/2109.00039)).

The code simulates a non-linear diffusion equation in the regime of high conductivity and thermal equilibrium, a characteristic environment for Hawking radiation interacting with standard model particles.

## Key Features

- **Steady-State Comparison:** Solves the non-linear heat equation to recover the $T \propto r^{-7/11}$ power-law scaling predicted for a BH type source.
- **Dynamic Boundary Conditions:** Simulates the "heating" phase where the inner boundary temperature spikes as the black hole approaches its final evaporation stage.
- **Thermal Front Tracking:** Algorithmically determines the radius of the "isothermal core" where the plasma has reached a local equilibrium before transitioning to the power-law tail.
- **Method of Lines:** Utilizes `scipy.integrate.solve_ivp` with stiff solvers (`Radau`/`BDF`) to handle the numerical instabilities inherent in non-linear diffusion.

## Project Structure

* `cooling.py`: Simulates the redistribution of energy in a "dead" system where the central source has ceased, showing the flattening of the temperature core.
* `Hawking_radiation_1D_heating.py`: Incorporates the time-dependent Hawking temperature $T_H(t) \propto (1 - \Delta t)^{-1/3}$ at the event horizon to simulate active heating of the surroundings.

## Physics Context

The simulations solve the non-linear PDE:
$$\frac{\partial (T^4)}{\partial t} = \frac{c}{r^2} \frac{\partial}{\partial r} \left[ \frac{r^2}{T} \frac{\partial (T^4)}{\partial r} \right]$$

The equation arises from heat diffusion equation in 3 dimentions and radial symmetry which is expected for Schwarzschild Black Hole. This equation the unique behavior of the "thermal front"—a distinct boundary between the isothermal core and the exterior—which is a hallmark of radiative heat transfer in these astrophysical contexts.

## Requirements

- Python 3.x
- NumPy
- SciPy
- Matplotlib
