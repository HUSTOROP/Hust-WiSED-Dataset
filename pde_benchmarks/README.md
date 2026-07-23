# Controlled PDE benchmark fields

This directory contains the cached numerical fields used for the controlled
WiSED PDE-discovery benchmarks. The files are generated from the solvers in
the companion [`Hust-WiSED`](https://github.com/HUSTOROP/Hust-WiSED) repository
and are released under CC BY 4.0. Cite the WiSED manuscript/software release
when reusing the fields or derived results.

## Files and noise protocol

Each benchmark has one archive for each relative additive Gaussian-noise level:
`0`, `0.01`, `0.02`, `0.03`, `0.04`, `0.05`, and `0.1`. The filename records the
benchmark and noise level, for example `burgers_2d_noise0.03.npz`. Noise is
added to the clean simulated field with a standard deviation scaled to the
standard deviation of the corresponding clean trajectory or field channel.

| Benchmark | Archived shape | Domain and boundary condition | Governing equation |
| --- | --- | --- | --- |
| 1D Burgers | `(32, 101, 256)` | `t in [0, 1]`, `x in [-1, 1)`, periodic `x` | `u_t = -u u_x + 0.01 u_xx` |
| 1D KdV | `(32, 101, 256)` | `t in [0, 1]`, `x in [-pi, pi)`, periodic `x` | `u_t = -6 u u_x - u_xxx` |
| 2D Burgers | `(32, 51, 48, 48, 2)` | `t in [0, 0.5]`, `x, y in [-1, 1)`, periodic `x, y` | Coupled two-field advection-diffusion system with viscosity `0.01` |
| 2D FitzHugh-Nagumo | `(32, 41, 64, 64, 2)` | `t in [0, 20]`, `x, y in [-10, 10)`, periodic `x, y` | Coupled reaction-diffusion system with `D_u = 1.0` and `D_v = 0.01` |

For the two-field benchmarks, the final dimension stores the fields in the
order `u, v`. The leading dimension indexes independently generated initial
conditions.

## Archive schema

Every `.npz` file contains the following entries:

| Key | Description |
| --- | --- |
| `data` | Noisy field observations used as discovery input. |
| `data_clean` | Noise-free numerical reference field. |
| `grid_info` | Coordinate arrays, periodic-axis metadata, field names and benchmark identifier. This object requires `allow_pickle=True` when opened with NumPy. |
| `true_eq` | Known governing equation or equations used exclusively for benchmark evaluation. |

The archives are tracked with Git LFS. After cloning the dataset repository,
install Git LFS and retrieve the binary objects before running the companion
installer:

```bash
git lfs install
git lfs pull
```

The companion command
`python scripts/install_release_data.py --dataset-root ../Hust-WiSED-Dataset`
copies all 28 benchmark archives into `Hust-WiSED/data/dataset/`, where the
benchmark runner expects the original filenames.
