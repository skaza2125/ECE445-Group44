# Self-Heating Bed

## Lab Notebook:

### Week of 9/18
**Initial Project Proposal**
- Collaboratively brainstormed potential designs for the self-heating system. Focused on integrating a robust heating subsystem with proper ventilation.
- Prepared the project proposal outlining the main components: a nichrome heating element, steel pipe enclosure, thermistor-based temperature sensing, and a fan-driven ventilation system.
- Highlighted potential challenges in power management, safety mechanisms, and integration of off-the-shelf components.
- Finalized initial high-level requirements:
  - Temperature modulation within 3°F of the setpoint.
  - Noise levels below 60 dB for quiet operation.
  - Energy efficiency within 1000-1500W power consumption.

---

### Week of 9/25
**Initial Heating Subsystem Design**
- Selected nichrome wire as the heating element for its corrosion resistance, high melting point, and superior resistivity.
- Calculated power requirements using:

```math
P = \frac{V^2}{R}
```
Where:
- \(V = 24\) volts.
- \(R\) (resistance) determined experimentally to optimize heat output.

Resulting in:
```math
P = \frac{24^2}{3.5} \approx 165 \text{ W}
```

- Tested initial nichrome lengths and gauges, refining configurations through iterative testing.
- Decided on nichrome-80 as the material for its high-temperature resistance and mechanical flexibility.

---

### Week of 10/2
**Heating System Prototyping**
- Wrapped nichrome wire around steel pipes to serve as heating elements.
- Performed tests to balance heating efficiency and safety:
  - Recorded instances of overheating and electrical shorts due to direct contact between nichrome and steel.
  - Applied Rust-Oleum insulating spray to mitigate shorts and maintain uniform heating distribution.

| Gauge | Length (cm) | Res. (Ω) | Heat | Melted? | Amps  | Power (W) |
|-------|-------------|-----------|------|---------|-------|-----------|
| 18    | 106         | 2.3       | Yes  | No      | 10.43 | 250.43    |
| 18    | 54          | 0.94      | Yes  | Yes     | 20    | 376       |
| 18    | 24          | 0.33      | Yes  | Yes     | 20    | 132       |
| 24    | 45          | 1.6       | Yes  | No      | 10.62 | 254.88    |
| 24    | 54          | 3.1       | Yes  | Yes*    | 7.74  | 185.81    |
| 24    | 106         | 5.83      | Yes* | No      | 4.12  | 98.80     |

(*Notes: "Yes*" indicates partial melting occurred or required additional insulation adjustments.)

**Diagram of Heating Setup:**
```plaintext
+---------+        +---------+        +---------+
| Nichrome|  --->  | Steel   |  --->  | Heated  |
| Wire    |        | Pipe    |        | Airflow |
+---------+        +---------+        +---------+
```

---

### Week of 10/15
**Ventilation System Implementation**
- Integrated PWM-controlled fans to manage airflow through the steel pipes.
- Developed a 6-stage PWM curve for dynamic fan speed adjustment:
  - Optimized exhaust temperatures while minimizing noise levels.
  - Verified airflow with thermistors, achieving a 28°F temperature delta.
- Used oscilloscope to calibrate PWM signal parameters for the fans.

---

### Week of 10/28
**PCB Design Challenges**
- Designed PCB to integrate power delivery and sensor interfaces:
  - Added safety features for high-current traces and voltage regulators.
  - Verified operation of DS18B20 sensors for precise temperature measurements.
- Encountered issues with MOSFETs:
  - MOSFETs overheated due to insufficient Vgs and high Rds.
  - Replaced MOSFETs with 24V relays for reliable switching of the nichrome wire.

**Fried ESP32 Chip:**
- Damage occurred while adjusting IO/power pins during operation.
- Implemented safety measures:
  - Powered down all systems before modifications.
  - Added current-limiting resistors and flyback diodes.

---

### Week of 11/15
**System Testing and Optimization**
- Conducted end-to-end testing of all subsystems:
  - Measured exhaust and ambient temperatures, ensuring safe operating limits.
  - Validated PWM fan control under varying load conditions.
- Power consumption stabilized at:

```math
P \approx 150 \text{ W}
```

- Demonstrated compliance with noise and energy efficiency requirements.

---

### Week of 12/4
**Final Integration and Demonstration**
- Assembled the final system:
  - Unified heating, ventilation, and control subsystems.
  - Verified operation under simulated user scenarios.
- Presented final prototype, achieving:
  - Temperature modulation within ±3°F.
  - Energy consumption under 400W.
  - Noise levels measured at 55 dB during operation.
- Suggested future improvements:
  - Use of infrared heating panels to improve efficiency.
  - Replace metal enclosures with ABS plastic to reduce thermal losses.

---

**Key Contributions:**
1. Developed and optimized the nichrome heating subsystem.
2. Designed a robust ventilation system with PWM-controlled fans.
3. Overcame PCB design challenges, ensuring safety and reliability.
4. Integrated DS18B20 sensors for precise temperature tracking.
5. Established safety protocols to prevent hardware failures.
6. Demonstrated a fully functional prototype meeting all requirements.

**Images:**
- Annotated circuit diagrams.
- PWM fan calibration curves.
- Final system assembly.

---

**Reflections:**
- Successfully implemented a cost-effective, energy-efficient self-heating system.
- Learned valuable lessons in hardware troubleshooting, safety design, and subsystem integration.
- Addressed challenges through iterative prototyping and testing, meeting all project goals.
