# 📻 FM Radio Receiver – Technical Overview
![FM Radio Schematic](https://github.com/bejaouihamza/FM_Radio/blob/main/Capture%20d'%C3%A9cran%202025-08-10%20013145.png)

## 📑 Introduction
This project is a simple **FM radio receiver** built using analog components and an RF tuner stage.  
It demonstrates the **principles of frequency modulation** (FM) reception, the **electromagnetic theory**,  
and the **electronics** needed to detect and play broadcast FM audio.

---

## 📷 Schematic

---

## ⚡ How FM Radio Works
**FM (Frequency Modulation)** encodes audio into a radio wave by varying its **frequency**  
while keeping the **amplitude constant**.

### Electromagnetic Principle
- FM signals are **electromagnetic waves** traveling at the speed of light (*c = 3×10⁸ m/s*).
- A broadcast station transmits a **carrier frequency** in the **VHF band** (88–108 MHz).
- The antenna captures a small portion of this wave and converts it into a **weak AC signal**.
- The circuit processes this to recover the original **audio waveform**.

---

## 📐 The Math Behind FM
If the **carrier wave** is:

<p align="center">
c(t) = A<sub>c</sub> · cos( 2π f<sub>c</sub> t )
</p>

In FM, the **instantaneous frequency** varies with the audio signal *m(t)*:

<p align="center">
s(t) = A<sub>c</sub> · cos[ 2π f<sub>c</sub> t + β · sin( 2π f<sub>m</sub> t ) ]
</p>

Where:  
- *f<sub>m</sub>* = maximum frequency of the audio signal  
- β = modulation index = Δf / f<sub>m</sub>  
- Δf = frequency deviation (max shift from f<sub>c</sub>)

Typical broadcast values:  
- Δf ≈ 75 kHz  
- f<sub>m</sub> ≤ 15 kHz  

---

## 🔧 Circuit Overview
**1. Antenna & LC Tuner**  
Captures the FM signal and selects the desired frequency using:

<p align="center">
f<sub>res</sub> = 1 / ( 2π √(LC) )
</p>

**2. RF Amplifier**  
Boosts the weak signal without adding too much noise.

**3. Mixer & Local Oscillator**  
Shifts the RF signal to an **Intermediate Frequency (IF)** (10.7 MHz).

**4. IF Amplifier & Limiter**  
Amplifies and removes amplitude variations (FM carries info in frequency only).

**5. FM Demodulator**  
Converts frequency changes into voltage variations (audio signal).

**6. Audio Amplifier**  
Boosts the audio to drive a speaker.

---

## 📊 Signal Flow
```mermaid
graph LR
    A[Antenna] --> B[LC Tuned Circuit]
    B --> C[RF Amplifier]
    C --> D[Mixer]
    E[Local Oscillator] --> D
    D --> F[IF Filter]
    F --> G[IF Amplifier]
    G --> H[Limiter]
    H --> I[FM Discriminator]
    I --> J[Audio Amplifier]
    J --> K[Speaker]
