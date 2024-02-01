# Sample: API reference

API documentation can be challenging because it leaves little room to communicate potentially complex concepts and interactions. Additionally, the first sentence of the following examples is the only content for these items displayed as contextual, rollover help in development environments, so it is especially critical to convey the purpose of the item succinctly.

- Example 1: [Compliance Limit Symmetry](#compliance-limit-symmetry)
- Example 2: [LCR Impedance Autorange](#lcr-impedance-autorange)
- Example 3: [Runt Polarity](#runt-polarity)
- Example 4: [Runt Time Condition](#runt-time-condition)

---

## <a name="compliance-limit-symmetry"></a>Compliance Limit Symmetry

Specifies whether compliance limits for current generation and voltage generation for the device are applied symmetrically about 0 V and 0 A or asymmetrically with respect to 0 V and 0 A.

When set to **Symmetric**, voltage limits and current limits are set using a single property with a positive value. The resulting range is bounded by this positive value and its opposite.

When set to **Asymmetric**, you must separately set a limit high and a limit low using distinct properties.

For asymmetric limits, the range bounded by the limit high and limit low must include zero.

**Note:** This property is not supported by all instruments. Refer to *Supported Properties by Instrument* for information about supported instruments.

**Default Value:** **Symmetric**

---

## <a name="lcr-impedance-autorange"></a>LCR Impedance Autorange

Defines whether an instrument in LCR mode automatically selects the best impedance range for each given LCR measurement.

Impedance autoranging may be enabled only when both:

- The **Source Mode** property is set to **Single Point**
- The **Measure When** property is set to a value other than **On Measure Trigger**

You can read **LCR Impedance Range** back after a measurement to determine the actual range used.

When enabled, impedance autoranging overrides impedance range settings you configure manually with any other properties.

**Tip:** When using a load with unknown impedance, you can set this property to **On** to determine the correct impedance range for the load. When you know the load impedance, you can achieve faster performance by setting this property to **Off** and setting **LCR Impedance Range Source** to **LCR Load Configuration**.

**Note:** This property is not supported by all instruments. Refer to *Supported Properties by Instrument* for information about supported instruments.

**Default Value:** **Off**

| Value | Description |
| - | - |
| **Off** | Disables automatic selection of the impedance range. Channel(s) use the impedance range you specify with the **LCR Impedance Range** property. |
| **On**  | Channel(s) automatically select the optimal **LCR Impedance Range** for the measured signal. |

---

## <a name="runt-polarity"></a>Runt Polarity

Specifies the polarity of pulses that trigger the oscilloscope for runt triggering.

This property determines how the oscilloscope triggers relative to the runt thresholds you set.

When set to **Positive**, the oscilloscope triggers when the following conditions are met:

- The leading edge of a pulse crosses the **Runt Low Threshold** in a positive direction;
- The trailing edge of the pulse crosses the **Runt Low Threshold** in a negative direction; and
- No portion of the pulse crosses the **Runt High Threshold**.

When set to **Negative**, the oscilloscope triggers when the following conditions are met:

- The leading edge of a pulse crosses the **Runt High Threshold** in a negative direction;
- The trailing edge of the pulse crosses the **Runt High Threshold** in a positive direction; and
- No portion of the pulse crosses the **Runt Low Threshold**.

When set to **Either**, the oscilloscope triggers in either case.

**Default Value:** **Positive**

| Value | Description |
| - | - |
| **Positive** | The oscilloscope triggers on pulses of positive polarity relative to **Runt Low Threshold** that do not cross **Runt High Threshold**. |
| **Negative** | The oscilloscope triggers on pulses of negative polarity relative to the **Runt High Threshold** that do not cross **Runt Low Threshold**. |
| **Either** | The oscilloscope triggers on runt pulses of either positive or negative polarity. |

---

## <a name="runt-time-condition"></a>Runt Time Condition

Specifies whether runt triggers are time qualified and, if so, how the oscilloscope triggers in relation to the duration range bounded by the **Runt Time Low Limit** and **Runt Time High Limit** properties.

**Default Value:** **None**

| Value | Description |
| - | - |
| **None** | Time qualification is disabled. The oscilloscope triggers on runt pulses based solely on the voltage level of the pulses. |
| **Within** | The oscilloscope triggers on pulses that, in addition to meeting runt voltage criteria, have a duration within the range bounded by **Runt Time Low Limit** and **Runt Time High Limit**. |
| **Outside** | The oscilloscope triggers on pulses that, in addition to meeting runt voltage criteria, have a duration not within the range bounded by **Runt Time Low Limit** and **Runt Time High Limit**. |
