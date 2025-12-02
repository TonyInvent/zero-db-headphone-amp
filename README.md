# zero-db-headphone-amp

A zero output resistance zero dB headphone amplifier

## Overview

This project provides simulation files for a zero output resistance headphone amplifier design based on the Texas Instruments paper:

**"Zero output resistance of headphone amplifier optimizes audio performance"**
- Document: SLYT630
- URL: https://www.ti.com/lit/pdf/slyt630

## Why Zero Output Impedance?

Traditional headphone amplifiers have some output impedance (typically 0.5-50 ohms) which:
- Causes voltage drop when driving low-impedance headphones (16-300 ohms)
- Creates frequency-dependent response variations due to headphone impedance changes with frequency
- Reduces damping factor, affecting bass response and transient performance

The zero output impedance design eliminates these issues by using feedback sensing at the load to compensate for any voltage drop in the output stage.

## Simulation Files

### LTspice Schematics (.asc)

| File | Description |
|------|-------------|
| `simulation/zero_db_headphone_amp.asc` | Basic single op-amp zero output impedance circuit |
| `simulation/zero_db_headphone_amp_dual_opamp.asc` | Dual op-amp version with separate sensing amplifier |
| `simulation/comparison_standard_vs_zero_zout.asc` | Side-by-side comparison of standard vs zero-Zout designs |

### SPICE Netlists (.cir)

| File | Description |
|------|-------------|
| `simulation/zero_db_headphone_amp.cir` | Basic SPICE netlist compatible with most simulators |
| `simulation/zero_db_headphone_amp_complete.cir` | Complete simulation with op-amp models and measurements |

## How to Use

### LTspice
1. Download and install [LTspice](https://www.analog.com/en/design-center/design-tools-and-calculators/ltspice-simulator.html)
2. Open any `.asc` file in LTspice
3. Run simulation (press F9 or click Run)
4. View waveforms by clicking on circuit nodes

### Other SPICE Simulators
1. Use the `.cir` netlist files
2. Import into your preferred SPICE simulator (ngspice, PSpice, etc.)
3. Run transient (`.TRAN`) or AC (`.AC`) analysis

## Circuit Parameters

- **Input Impedance**: ~10k ohms
- **Gain**: Unity (0 dB)
- **Output Impedance**: ~0 ohms (compensated)
- **Load**: 32 ohm headphones (typical)
- **Bandwidth**: >100 kHz

## Key Components

- **R1, Rg**: Input gain setting resistors
- **Ro**: Output resistor (its impedance is actively cancelled)
- **Rs**: Current sense resistor
- **Rf1, Rf2**: Feedback network for impedance cancellation

## Simulations to Run

1. **Transient Analysis**: Observe time-domain waveforms with 1kHz sine input
2. **AC Analysis**: Check frequency response from 10Hz to 100kHz
3. **Output Impedance**: Compare voltage at load with varying load impedance

## License

MIT License - See [LICENSE](LICENSE) file for details
