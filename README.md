# PINN_book — code for the monograph

Runnable code accompanying the monograph

> **Physics-Informed Neural Networks: An Honest, Hands-On Introduction, with Emphasis on Fluid Dynamics**
> Rajesh Ranjan, Department of Aerospace Engineering, Indian Institute of Technology Kanpur

Every numerical result in the monograph was produced by running the notebook named beside it in the
text; this repository is that code. Each notebook is **self-contained** — it imports only PyTorch,
NumPy, Matplotlib and (in a few cases) SciPy, selects a GPU automatically if one is present, and
needs no external data file.

## Requirements

```bash
pip install torch numpy matplotlib scipy
```

The examples run on CPU or GPU; the code is device-agnostic (`cuda` if available, otherwise `cpu`)
and runs unchanged on NVIDIA (CUDA) and AMD (ROCm) hardware. The timings quoted in the monograph
were measured on one GPU of an NVIDIA RTX PRO 6000 Blackwell card. Because collocation points are
resampled at random every step, reproduced numbers vary in the last significant figure but not in
the conclusions.

## How to run

Open any notebook in Jupyter and run all cells, or execute it headless:

```bash
jupyter nbconvert --to notebook --execute ch03/lotka_volterra.ipynb
```

## Contents

### Chapter 1 — Physics and neural networks
- `ch01/motivation_oscillator.ipynb` — harmonic oscillator: data-only fit vs. a PINN

### Chapter 2 — Tools of the trade
- `ch02/decay_pinn_15lines.ipynb` — a complete PINN in fifteen lines (linear decay `u' = -k u`)

### Chapter 3 — First solutions: ODEs and PDEs
- `ch03/riccati_ode.ipynb` — nonlinear first-order ODE (Riccati)
- `ch03/lotka_volterra.ipynb` — a nonlinear system (Lotka–Volterra predator–prey)
- `ch03/fin_and_slab.ipynb` — the fin equation and the transient slab
- `ch03/convection_ftbs_vs_pinn.ipynb` — linear convection: finite differences vs. PINN
- `ch03/diffusion_ftcs_vs_pinn.ipynb` — linear diffusion: finite differences vs. PINN
- `ch03/convection_diffusion_vs_pinn.ipynb` — convection–diffusion and grid refinement

### Chapter 4 — Where PINNs excel: the use cases
- `ch04/inverse_wave_speed.ipynb` — inverse problem: recover one coefficient
- `ch04/inverse_two_parameters.ipynb` — inverse problem: recover two coefficients
- `ch04/highdim_poisson.ipynb` — a high-dimensional Poisson equation
- `ch04/euler_bernoulli_beam.ipynb` — a fourth-order PDE (Euler–Bernoulli beam)
- `ch04/parametric_surrogate.ipynb` — a parametric surrogate (one network, many problems)
- `ch04/data_assimilation.ipynb` — a field from scattered sensors, no boundary conditions
- `ch04/unknown_function_kx.ipynb` — recovering an unknown spatially varying coefficient
- `ch04/equation_discovery.ipynb` — discovering which terms govern the data

### Chapter 5 — When PINNs fail: pitfalls and cures
- `ch05/vanilla_failures.ipynb` — four Chapter-6 problems run vanilla: all fail
- `ch05/spectral_bias.ipynb` — spectral bias and Fourier features
- `ch05/fbpinn_domain_decomposition.ipynb` — finite-basis domain decomposition
- `ch05/burgers_shock.ipynb` — a steep internal front (Burgers)
- `ch05/rba_loss_imbalance.ipynb` — loss imbalance and residual-based attention
- `ch05/rard_adaptive_sampling.ipynb` — adaptive collocation (RAR-D)
- `ch05/causality_violation.ipynb` — causality violation, causal weighting, time-marching
- `ch05/sir_epidemic.ipynb` — the SIR epidemic: a causality trap and its cure
- `ch05/ill_conditioning.ipynb` — ill-conditioning from bad units (non-dimensionalisation)
- `ch05/blasius_first_order_system.ipynb` — the cost of high-order derivatives
- `ch05/conservation_pendulum.ipynb` — conservation, long-time integration, extrapolation
- `ch05/error_estimates_ensemble.ipynb` — error indicators from a seed ensemble

### Chapter 6 — The capstone: fluid mechanics and heat transfer
- `ch06/channel_flow.ipynb` — fully developed channel flow
- `ch06/orr_sommerfeld.ipynb` — Orr–Sommerfeld linear stability (eigenvalue problem)
- `ch06/stokes_first_problem.ipynb` — impulsively started plate
- `ch06/stokes_second_problem.ipynb` — oscillating plate
- `ch06/womersley_flow.ipynb` — pulsatile channel flow
- `ch06/potential_flow_cylinder.ipynb` — potential flow past a cylinder (annular domain)
- `ch06/falkner_skan_surrogate.ipynb` — the Falkner–Skan wedge family (boundary-layer surrogate)
- `ch06/plate_conduction_2d.ipynb` — two-dimensional steady conduction
- `ch06/inverse_conduction.ipynb` — inverse conduction: measuring thermal diffusivity
- `ch06/radiative_cooling.ipynb` — radiative cooling (strongly nonlinear ODE)
- `ch06/composite_wall.ipynb` — the composite wall: interfaces and mini domain decomposition
- `ch06/taylor_green_vortex.ipynb` — Taylor–Green vortex (unsteady Navier–Stokes)
- `ch06/lid_driven_cavity.ipynb` — lid-driven cavity at Re = 100
- `ch06/cavity_reynolds.ipynb` — lid-driven cavity at higher Reynolds number

## License

Released for educational use alongside the monograph. Please cite the monograph if you use this code.
