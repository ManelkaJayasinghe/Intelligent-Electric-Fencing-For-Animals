# Intelligent-Electric-Fencing-For-Animals

An automated, species-specific animal deterrence system powered by computer vision and embedded hardware. This project utilizes a lightweight **YOLOv5n** model running on a **Raspberry Pi** to classify detected animals in real time and dynamically adjust the deterrence mechanism (providing an adjustable high-voltage pulse for large mammals like elephants or cows, and a non-lethal acoustic buzzer for smaller animals like squirrels).

---

## 🛠️ System Architecture & Workflow

1. **Vision Processing:** A camera connected to the Raspberry Pi captures live video frames.
2. **Inference:** A quantized **YOLOv5n** model processes the frame to identify the species of the animal.
3. **Decision & Control:** 
   * **Large Animals (e.g., Elephants, Cows):** Triggers a high-voltage relay module to activate the electric fence line.
   * **Small Animals (e.g., Squirrels):** Triggers an acoustic buzzer module to deter the animal without physical harm.
4. **Hardware Interfacing:** The Raspberry Pi communicates control signals via GPIO/serial to an **Arduino Uno**, which safely manages the relay modules and power switching.

---

## ⚙️ Hardware Components List

* **Processing Unit:** Raspberry Pi (Model 4B / 5 recommended)
* **Microcontroller:** Arduino Uno
* **Vision Sensor:** Raspberry Pi Camera Module (or USB Webcam)
* **Power Conversion:** Step-down Buck Converters (e.g., LM2596) for stable voltage regulation
* **Actuators & Output:** 
  * Relay modules (for switching the electric fence circuit)
  * Acoustic buzzers (for small animal deterrence)
* **Power Supply:** 12V Battery / DC Power Source with proper isolation

---

## 📂 Repository Directory Structure

```text
Intelligent-Electric-Fencing-For-Animals/
│
├── hardware/
│   ├── arduino_control/          # Arduino firmware (.ino files for relay/buzzer control)
│   └── schematics/               # Circuit diagrams and wiring layouts
│
├── software/
│   ├── inference/                # Python scripts for YOLOv5n video stream processing
│   └── comms/                    # Serial/GPIO communication scripts between Pi and Arduino
│
├── weights/                      # Trained YOLOv5n model weights (.pt / .engine files)
│
├── docs/                         # System block diagrams, data sheets, and project reports
│
├── requirements.txt              # Python dependencies
└── README.md                     # Project documentation
