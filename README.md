 Project Summary

## Abstract

This project presents the design, simulation and optimization of a low-power charge pump inverter capable of generating a negative DC voltage from a single +5V supply. The objective was to create an energy efficient and compact dual-rail power source suitable for analog circuits and operational amplifier applications without requiring a dedicated negative voltage supply.

A switched-capacitor charge pump topology was implemented and simulated using LTspice. The circuit employs a flying capacitor, Schottky diodes and output filtering capacitors to invert the input supply voltage. To improve efficiency, low-ESR capacitors and parallel capacitor configurations were incorporated, reducing charge-transfer losses and output ripple. The subsequent load was also decreased to improve generation efficiency.

The generated negative voltage was used to power an operational amplifier stage.This demonstrates the practical applicability of the charge pump in dual-supply analog systems. Simulation results showed a negative output voltage approaching -4.81V from a +5V input, corresponding to approximately 96% voltage conversion efficiency.

---

## Objectives

* Generate a negative DC voltage from a single +5V source.
* Study the operation of switched-capacitor charge pumps.
* Investigate the impact of diode selection on efficiency.
* Analyze the effect of capacitor ESR on output performance.
* Reduce output ripple through capacitor optimization.
* Demonstrate practical use of the generated negative rail using an operational amplifier.
* Decrease Load.

---

## Methodology

The charge pump inverter was designed using:

* Pulse-based clock source (100 kHz)
* Flying capacitor network (Ceramic Capacitors, most ideal)
* Schottky rectifier diodes (1N5817)
* Low-ESR capacitors (0.02 Ohm)
* Parallel capacitor configuration
* Resistive load
* Operational amplifier stage ( Construction of a Voltage Follower)
* 1V, 10KHz AC input source.

The circuit was modeled and verified entirely in LTspice through transient analysis.

---
# Working Principle

The circuit operates as a switched-capacitor charge pump inverter, converting a single +5V DC supply into a negative voltage without requiring an additional negative power source. A 100 kHz clock signal periodically charges and discharges a flying capacitor, transferring charge in such a way that the output node is driven below ground potential.

Phase 1: Capacitor Charging

When the clock output is high (+5V), the flying capacitor charges through diode D1. One terminal of the capacitor is connected to the clock source while the other terminal is clamped near ground, resulting in approximately 5V being stored across the capacitor.

Phase 2: Charge Transfer and Voltage Inversion

When the clock transitions low (0V), the charged capacitor retains its stored voltage. Since the left terminal of the capacitor is now pulled to ground, the right terminal is forced to approximately -5V relative to ground. Diode D2 becomes forward biased and transfers this negative potential to the output capacitor.

Output Filtering

The output capacitor stores charge delivered during successive clock cycles and smooths the generated negative voltage. As the clock continues switching, the output capacitor is repeatedly refreshed, maintaining a stable negative DC voltage with minimal ripple.

Op-Amp Validation

The generated negative rail (VNEG) was connected to the negative supply terminal of an operational amplifier while the positive supply terminal was connected to +5V. A voltage follower configuration was implemented to verify that the generated negative supply could successfully power practical analog circuitry. The simulation confirmed stable op-amp operation using the charge-pump-generated dual-rail supply.

----
## Key Design Improvements

### Schottky Diodes

Conventional silicon diodes were replaced with Schottky diodes to reduce forward voltage drop and improve charge-transfer efficiency.
Traditional diodes have a forward voltage drop of about 0.6/0.7V however with Schottkey diodes this reduces to 0.2V.

### Low-ESR Capacitors

Capacitor ESR was reduced to approximately 0.02 Ω to minimize power loss and output voltage degradation. This value was assumed from the most ideal value for lab available ceramic capacitors.

### Parallel Capacitor Configuration

Parallel capacitors were used to:

* Double effective capacitance
* Reduce equivalent ESR:
                    ESR(equired) = 1/ESR(1) + 1/ESR(2)
                                 =  0.02*0.02/0.02+0.02 = 0.01 Ohm;
* Improve transient response:
                    C(eq) = C1 + C2 = 20uF; thereby decreasing ripple
  In the above case as capacitance is doubled and ESR is halved, efficiency increases by reducing Voltage loss since,
                    V(loss) = I * ESR;
* Lower output ripple
* Reduced Load since high resistance load is applied to decrease Load current.

---

## Results

| Parameter          | Value   |
| ------------------ | ------- |
| Input Voltage      | +5V     |
| Output Voltage     | ≈ -4.8V |
| Clock Frequency    | 100 kHz |
| Flying Capacitance | 20 µF   |
| Output Capacitance | 20 µF   |
| Load Resistance    | 100 kΩ  |
| Diodes             | 1N5817  |
| Capacitor ESR      | 0.02 Ω  |

---

## Tools Used

* LTspice Version 26.0.2
* Analog Circuit Design Principles
* Switched-Capacitor Power Conversion Techniques

---

## Applications

* Dual-rail operational amplifier systems
* Sensor signal conditioning
* Portable instrumentation
* Embedded analog interfaces
* Battery-powered electronics
* Negative bias generation circuits

---

## Skills Demonstrated

* Analog Circuit Design
* Power Electronics Fundamentals
* LTspice Simulation
* Switched-Capacitor Power Conversion
* Signal Conditioning
* Component Optimization
* Engineering Trade-Off Analysis
* Performance Evaluation and Validation

---
