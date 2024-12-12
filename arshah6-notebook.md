# Self-Heating System Project

## Lab Notebook: Heating Subsystem Contributions

### Week of 9/25
**Initial Heating Subsystem Design**
- Finalized selection of nichrome wire as the primary heating element due to its resistance properties and heat dissipation efficiency.
- Calculated the required power (Φ) to heat the nichrome effectively using:

  \[
  P = V^2 / R
  \]
  Where:
  - \(V\) is the voltage supplied by a 24V, 20A power supply.
  - \(R\) (measured resistance of the nichrome wire) = ~3.5 Ω.

  Resulting in:
  \[
  P = \frac{24^2}{3.5} \approx 165 \text{ W}
  \]

- Determined optimal nichrome length to balance between overheating and insufficient heating.

---

### Week of 10/2
**Prototyping the Heating System**
- Began testing nichrome wire configurations by wrapping it around a steel pipe to enhance heat transfer to airflow.
- Encountered significant issues with electrical shorts caused by direct contact between the nichrome and conductive steel pipe. This led to uneven current distribution, reducing heating efficiency.
- Proposed the use of **Rust-Oleum insulating spray** to thermally insulate the steel pipe and prevent electrical conduction through the pipe.

**Diagram of Initial Heating Setup:**
```plaintext
+---------+        +---------+        +---------+
| Nichrome|  --->  | Steel   |  --->  | Heated  |
| Wire    |        | Pipe    |        | Airflow |
+---------+        +---------+        +---------+
```

---

### Week of 10/10
**Integration with Ventilation System**
- Conducted airflow tests to measure temperature differentials across the heating subsystem using thermistors.
- Calculated heat transfer efficiency using the formula:

  \[
  Q = m \cdot c \cdot \Delta T
  \]
  Where:
  - \(Q\) = heat energy (Joules)
  - \(m\) = mass flow rate of air (kg/s)
  - \(c\) = specific heat capacity of air (1005 J/(kg·K))
  - \(\Delta T\) = temperature difference (measured with thermistors).

---

### Week of 10/20
**PCB Design and Testing**
- Contributed to the design of the PCB controlling the heating system. Focused on:
  - Power routing to the nichrome wire via a MOSFET.
  - Ensuring sufficient spacing to accommodate thermal dissipation.

- Discovered overheating issues with the MOSFET due to insufficient heat sinking. Calculations revealed:

  \[
  T_{MOSFET} = R_{\text{ds}} \cdot I^2 + T_{\text{ambient}}
  \]
  Where:
  - \(R_{\text{ds}}\) = thermal resistance (62.5°C/W).
  - \(I\) = current (6-8 A).

  Resulting temperature exceeded 700°C, necessitating the addition of external relays.

---

### Week of 11/1
**Final Heating Subsystem Integration**
- Replaced MOSFET with a mechanical relay to improve heat dissipation and reliability.
- Soldered and tested the final PCB layout, verifying nichrome heating functionality and consistent temperature control using a basic on/off thermal regulation algorithm.

**Final Heating Circuit Diagram:**
```plaintext
+---------+        +---------+        +---------+
| Relay   |  --->  | Nichrome|  --->  | Fan     |
| Control |        | Wire    |        | Output  |
+---------+        +---------+        +---------+
```

---

### Week of 11/15
**System Testing and Optimization**
- Conducted full system testing, recording temperature differences and ensuring even heating distribution.
- Adjusted nichrome configuration to achieve an optimal balance between power consumption and heating performance.

  Final power draw: \(P \approx 150 \text{ W}\).

- Prepared subsystem for final demonstration, showcasing stable temperature control and efficient airflow.

---

**Key Contributions:**
1. Nichrome wire selection and length optimization.
2. Insulation design to prevent electrical shorts.
3. Power and thermal calculations for subsystem efficiency.
4. PCB design and integration with ventilation system.
5. Testing and refinement of thermal performance.

**Images:**
- Annotated circuit diagrams.
- Thermal test setups.
- Final assembled system.

