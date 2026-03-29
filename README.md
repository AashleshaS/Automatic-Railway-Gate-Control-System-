## 🛤️ Automatic Railway Gate Control System using S-R Latch

This project demonstrates a smart, automated safety system for railway level crossings designed to eliminate human error and the flaws of timer-based automation. Built using fundamental sequential logic, the system uses "memory" to ensure the gate remains closed as long as a train is present, regardless of its speed or length.

---

## 🚀 Key Features
* **Sensor-Driven Logic:** Uses two distinct sensors—**Train Arrives (S1)** and **Train Leaves (S2)**—to provide a 100% responsive system based on physical train position.
* **Sequential Memory:** Unlike timer-based systems that "guess" when a train has passed, this system uses an **S-R Latch** to reliably "remember" that a train is in the crossing even after it passes the first sensor.
* **Fail-Safe Design:** By placing sensors before and after the gate, the system is physically incapable of entering an "invalid" state.
* **Hardware-Efficient:** Built entirely from fundamental logic gates (**NOR gates**) without the need for complex microcontrollers or programming.

---

## 🧠 The "Memory" Case
The most critical feature of this circuit is its ability to **hold a state** when both sensors are inactive ($S=0, R=0$). 

* **The Problem:** In a simple system without memory, once a train passes the first sensor, the signal drops to $0$. This would cause the gate to immediately open while the train is still on the tracks.
* **The Solution:** The S-R Latch creates a **Memory (Hold)** state. When the train is between sensors, both inputs are $0$, but the latch "remembers" the previous **Set** command and keeps the gate closed.
* **The Result:** The gate only opens when it receives a deliberate **Reset** signal from the second sensor, ensuring total safety for long or slow-moving trains.

---

## ⚙️ How It Works
The system operates based on the **S-R Latch Truth Table**:

| System State | S1 (Arrives) | S2 (Leaves) | Gate Status | Logic Operation |
| :--- | :---: | :---: | :--- | :--- |
| **No Train** | 0 | 0 | **Open** | Memory (Initial Hold) |
| **Train Arrives** | 1 | 0 | **Closed** | SET (Gate Closes) |
| **Train Between** | 0 | 0 | **Closed** | **Memory (Maintains Closure)** |
| **Train Leaving** | 0 | 1 | **Open** | RESET (Gate Opens) |

---

## 🛠️ Components
* **Logic Core:** S-R (Set-Reset) Latch using cross-coupled **NOR gates (IC 7402)**.
* **Inputs:** 2 Push-button sensors acting as S and R signals.
* **Outputs:** 2 LEDs indicating **Gate Closed** (Set) and **Gate Open** (Reset).

---
