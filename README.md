# PID Control Practice Notebook

A hands-on exploration of PID control through progressively complex simulations. Each system models real plant dynamics — including sensor noise, mid-run disturbances, and setpoint changes — using [`simple_pid`](https://simple-pid.readthedocs.io/en/latest/) and [`matplotlib`](https://matplotlib.org/).

Built to develop practical intuition with PID tuning ahead of an internship in automation and robotics.

---

## Systems

### Position Correction
A mass is driven from rest at 0m toward a target position of 100m. Models velocity-dependent drag and a gravity-like bias force. Sensor noise is injected on every reading. At t=2.5s a positional disturbance is applied; at t=6s the setpoint changes to 20m, demonstrating setpoint tracking.

### Velocity Correction
The controlled variable shifts from position to velocity. The system starts at 5m/s and targets 80m/s using the same drag model. At t=2.5s a sudden velocity drop simulates hitting an obstacle. At t=6s the setpoint drops to 30m/s.

### Temperature Control — Heating
Simulates a heating system starting at ambient (23.73°C) targeting 73°C. The plant models heater output against natural cooling toward ambient. Sensor noise is present throughout. At t=5s a thermal disturbance drops the temperature by 10°C, testing disturbance rejection.

### Temperature Control — Cooling
Simulates a refrigeration system starting at ambient (23.73°C) targeting 5°C — below room temperature. The plant models cooler output against natural warming toward ambient. At t=5s a disturbance adds 10°C (seal leak), forcing the controller to recover.

---

## Dependencies

```
simple-pid
matplotlib
numpy
```

Install with:

```bash
pip install simple-pid matplotlib numpy
```

---

## Key Concepts Demonstrated

- **P, I, D tuning** — each system required separate gain tuning based on plant dynamics
- **Plant modeling** — position, velocity, and thermal systems each have distinct physics
- **Disturbance rejection** — every system includes a mid-run event the controller must recover from
- **Setpoint tracking** — position and velocity systems change target mid-run
- **Sensor noise** — Gaussian noise injected on measurements to simulate real sensor behavior
- **Derivative on measurement** — used in cooling system to prevent derivative kick on disturbance spikes
