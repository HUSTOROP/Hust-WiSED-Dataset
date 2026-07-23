# SIB diffusion equation assessment

- Official WiSED equation: `u_t = 2.189*u_{x} / x + 0.8065*(u_{xx})`
- True PDE form: `u_t = u_xx + 2*u_x/x`
- Discovered RHS vs u_t: RMSE=0.0183767, R2=0.998947, MAE=0.0067968
- In-window field reconstruction, 0 to T: RMSE=0.00330014, R2=0.999923, MAE=0.00267807
- Out-of-window rollout, T to 6T: RMSE=3.62855e-05, R2=1, MAE=5.02587e-06
- Note: this assessment does not replace the official selected equation or rerank candidates.
