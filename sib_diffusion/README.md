# SIB radial-diffusion field

`sib_diffusion_raw_field_noise0.03.npz` is the cached simulated field used by
the retained spherical-electrode-particle validation. It stores raw radial
concentration observations with a 3% additive noise level and the associated
normalized time and radial coordinates.

The corresponding generator and discovery entry point are in the companion
code repository:

```text
engineering_validation/sib_diffusion_raw_field/
```

The retained configuration uses one boundary-flux condition (`delta = 0.25`),
seven initial concentration profiles, and clipping of simulated concentration
to the physical interval `[0, 1]` after numerical updates. This field is
generated project data and is released under CC BY 4.0; cite WiSED when reused.

