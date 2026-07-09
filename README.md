# Simple Quadruped Robot Dog - Mechanical Design

This repository contains the basic mechanical design parameters and initial calculations for an 8-DOF quadruped robot dog, submitted for the **Smart Methods Internship** task.

The main objective is to understand the mechanical fundamentals that allow the robot to stand and perform stable walking.

---

## 📋 Task Requirements Analysis

### 1. Body Shape & Chassis
- Designed as a simple hollow rectangular chassis to protect internal electronics (battery and controllers).
- Features a top container module representing a **Sensor Head (Radar, Cameras, Ultrasonic)**.
- Features a front slot displaying the designer's identifier (**"Ahmad"**).

### 2. Leg Design
- The robot has 4 identical symmetric legs.
- Each leg consists of 2 distinct links (Thigh and Lower Leg) joined via rotary mechanisms to enable forward walking steps.

### 3. Number of Joints & Degrees of Freedom (DOF)
- **Hip Joint:** 1 Rotary joint per leg (Moves forward/backward).
- **Knee Joint:** 1 Rotary joint per leg (Flexes/extends to clear the ground).
- **Total System DOF:** 4 legs × 2 joints = **8-DOF Total**.

### 4. Motor Selection
- **Actuator Specified:** **MG996R Servo Motor**.
- **Reason:** It features internal **Metal Gears** to handle operational stress and shocks, and delivers a strong torque of **11 kg·cm** at 6V.

### 5. Initial Torque Calculation (Hip Joint)
- **Total Weight ($m$):** $1.2 \text{ kg} \rightarrow \text{Total Force } (F) = 1.2 \times 9.8 = 11.76 \text{ N}$
- **Force Per Leg ($F_{\text{leg}}$):** Assuming 2 legs share the weight while walking $\rightarrow 11.76 \text{ N} / 2 = 5.88 \text{ N}$
- **Leg Length ($r$):** $10 \text{ cm} = 0.1 \text{ m}$

$$\text{Torque } (\tau) = F_{\text{leg}} \times r = 5.88 \text{ N} \times 0.1 \text{ m} = 0.588 \text{ N}\cdot\text{m}$$
Converting to servo standard unit ($\text{kg}\cdot\text{cm}$):
$$\tau = 0.588 \times 10.2 \approx \mathbf{6.0 \text{ kg}\cdot\text{cm}}$$
*Since the MG996R servo provides 11 kg·cm (which is greater than 6.0 kg·cm), the motor choice is perfect and safe.*

### 6. Stability & Center of Gravity (CoG)
- Heavy internal parts (like the LiPo battery and control boards) are mounted **low and exactly in the center** of the chassis.
- This keeps the Center of Gravity low to prevent the robot from tipping over.

### 7. Proposed Walking Gait
- **Gait Type:** **Creep Gait** (Slow crawl walking).
- **How it works:** The robot moves **only 1 leg at a time** while keeping the other 3 legs flat on the ground. This forms a continuous "support triangle" keeping the robot perfectly balanced.

### 8. Expected Mechanical Problems & Solutions
1. **Slippage on Smooth Floors:**
   * *Solution:* Adding high-friction **rubber tips** to the bottom of the feet.
2. **Joint Vibration (Backlash):**
   * *Solution:* Using high-quality mounting brackets and tightening all bolts securely.
3. **High Current / Power Reset:**
   * *Solution:* Separating the motor power line from the microcontroller using a dedicated power distribution board (like PCA9685).
