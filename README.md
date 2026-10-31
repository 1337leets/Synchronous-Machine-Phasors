# Synchronous Machine Phasors

Interactive web pages for studying the synchronous generator in ELM3092 Electrical Machines 2 at Yildiz Technical
University (YTU). They show how the load changes the phasor diagram, how the armature current splits into d and q
components, and what the V curves mean. They are study aids, not a design tool.

## Pages

- `phasor-and-v-curves.html` draws the phasor diagram of a salient-pole generator using two-reaction theory. You can
  set the load type, power factor angle, armature current, `X_d`, `X_q` and `R_a`, and read `δ`, `E_f`, `ψ`, `I_d` and
  `I_q`. Its second tab draws V curves for a cylindrical-rotor machine with `R_a` neglected.
- `dq-decomposition.html` puts inductive, resistive and capacitive loads next to each other for fixed machine values.
  It draws the voltage construction from `V_t` to `E_f`, and one button adds `R_a`. Its main point is that `I_d` is not
  zero for a resistive load, because the axes follow `E_f` and not `V_t`.

## Usage

Open `index.html` in a browser. There is nothing to install or build, and the pages work offline.

## How it works

All values are per unit with `V = 1`. With the current phasor `I_a` at angle `-φ` for a lagging load, the q-axis
direction comes from

```
E_q' = V + I_a (R_a + jX_q)
δ = arg(E_q')
ψ = φ + δ
I_d = I_a sin ψ
I_q = I_a cos ψ
E_f = |E_q'| + (X_d - X_q) I_d
```

The V curves use `E_f sin δ = P X_s / V` to find `δ` for each excitation, then `I_a = (E_f∠δ - V) / (jX_s)`. The
lowest point of a curve is at unity power factor, where `E_f = sqrt(V² + (I_a X_s)²)`.

## Limitations

- Saturation is ignored, and the reactances are constants.
- The phasor tab and the V curve tab use different rotor models, so their numbers are not meant to be compared.
- The pages do not check stability limits. With extreme slider values `E_f` can come out negative, and the page says
  so instead of treating it as an operating point.

## License

MIT, see [LICENSE](LICENSE).
