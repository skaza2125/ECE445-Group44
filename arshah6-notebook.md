# Self-Heating System Project

## Lab Notebook: 

### Week of 9/18
**Initial Project Proposal**
- Collaboratively brainstormed potential designs for the self-heating system. Focused on integrating a robust heating subsystem with proper ventilation.
- Prepared the project proposal outlining the main components: a nichrome heating element, steel pipe enclosure, thermistor-based temperature sensing, and a fan-driven ventilation system.
- Highlighted potential challenges in power management and safety mechanisms, particularly with high-current circuits.

### Week of 9/25
**Initial Heating Subsystem Design**
- Finalized selection of nichrome wire as the primary heating element due to its resistance properties and heat dissipation efficiency.
- Calculated the required power (Φ) to heat the nichrome effectively using:

```math
P = \frac{V^2}{R}
```
Where:
- \(V\) is the voltage supplied by a 24V, 20A power supply.
- \(R\) (measured resistance of the nichrome wire) = ~3.5 Ω.

Resulting in:
```math
P = \frac{24^2}{3.5} \approx 165 \text{ W}
```

- Determined optimal nichrome length to balance between overheating and insufficient heating.

---

### Week of 10/2
**Prototyping the Heating System**
- Began testing nichrome wire configurations by wrapping it around a steel pipe to enhance heat transfer to airflow.
- Experimented with various nichrome gauges and lengths to identify optimal heating performance without overheating or insufficient heating. Below are key test results:

| Gauge | Length (cm) | Res. (Ω) | Heat | Melted? | Amps  | Power (W) |
|-------|-------------|-----------|------|---------|-------|-----------|
| 18    | 106         | 2.3       | Yes  | No      | 10.43 | 250.43    |
| 18    | 54          | 0.94      | Yes  | Yes     | 20    | 376       |
| 18    | 24          | 0.33      | Yes  | Yes     | 20    | 132       |
| 24    | 45          | 1.6       | Yes  | No      | 10.62 | 254.88    |
| 24    | 54          | 3.1       | Yes  | Yes*    | 7.74  | 185.81    |
| 24    | 106         | 5.83      | Yes* | No      | 4.12  | 98.80     |

(*Notes: "Yes*" indicates partial melting occurred or required additional insulation adjustments.)

- Proposed the use of **Rust-Oleum insulating spray** to thermally insulate the steel pipe and prevent electrical conduction through the pipe, which was causing shorts during initial tests.

**Diagram of Initial Heating Setup:**
```plaintext
+---------+        +---------+        +---------+
| Nichrome|  --->  | Steel   |  --->  | Heated  |
| Wire    |        | Pipe    |        | Airflow |
+---------+        +---------+        +---------+
```

---

### Week of 10/15
**Challenges with Buck Converters**
- Decided to relocate the buck converters off-board due to safety and troubleshooting concerns. During testing, 2 out of 3 buck converters failed.
  - Likely reasons included:
    - Improper soldering connections leading to voltage spikes.
    - Insufficient heat sinking, causing thermal runaway.
    - Inadequate current handling for prolonged operation.
- Shifted focus to external, pre-tested buck converter modules for stability and reduced risk during subsequent development phases.

---

### Week of 10/28
**Fried ESP Chip During Testing**
- Encountered an issue where one ESP chip was damaged during a prototyping session.
  - Likely cause: Adjustments to the IO/Power pins while the system was powered on led to an influx of current, resulting in a short circuit and hardware failure.
- Implemented strict safety protocols:
  - Ensure all systems are powered off before making any physical adjustments.
  - Use current-limiting resistors and diodes to safeguard sensitive components in future designs.

---

### Week of 11/15
**System Testing and Optimization**
- Conducted full system testing, recording temperature differences and ensuring even heating distribution.
- Adjusted nichrome configuration to achieve an optimal balance between power consumption and heating performance.

Final power draw:
```math
P \approx 150 \text{ W}
```

- Integrated additional safety mechanisms, including temperature cutoffs to prevent overheating.

---

### Week of 12/4
**Final Integration and Demonstration**
- Completed assembly of all subsystems into a unified prototype.
- Verified operation of the nichrome heating subsystem, airflow ventilation, and safety controls during demonstration tests.
- Collected performance data showing consistent heating within design specifications and minimal energy waste.
- Presented the fully functional system for evaluation, highlighting design decisions, troubleshooting processes, and final outcomes.

---

**Key Contributions:**
1. Nichrome wire selection, length optimization, and testing across multiple configurations.
2. Insulation design to prevent electrical shorts and improve safety.
3. Power and thermal calculations for subsystem efficiency.
4. PCB design, troubleshooting, and integration with ventilation system.
5. Comprehensive testing and refinement of heating subsystem and airflow dynamics.
6. Final system integration and demonstration.

**Images:**
- Annotated circuit diagrams.
- Thermal test setups.
- Final assembled system.
