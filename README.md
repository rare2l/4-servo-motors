Servo Control & Humanoid Walking Algorithm

Project Overview

This project includes two main components:

1. **Servo Control with Arduino:**
   - Control 4 servo motors.
   - Perform a sweep motion for 2 seconds.
   - Then hold all servos at 90 degrees.
     (https://www.tinkercad.com/things/kEMBPNXMAyy-fantastic-sango)
     
2. **Humanoid Robot Walking Algorithm:**
   - Logical step-by-step motion design for humanoid walking using servo joints.

---

Part 1 – Servo Sweep + Hold (Arduino Code)

```cpp
#include <Servo.h>

Servo s1, s2, s3, s4;

void setup() {
  s1.attach(3);
  s2.attach(5);
  s3.attach(6);
  s4.attach(9);
}

void loop() {
  unsigned long startTime = millis();
  while (millis() - startTime < 2000) {
    for (int pos = 0; pos <= 180; pos++) {
      s1.write(pos);
      s2.write(pos);
      s3.write(pos);
      s4.write(pos);
      delay(5);
    }
    for (int pos = 180; pos >= 0; pos--) {
      s1.write(pos);
      s2.write(pos);
      s3.write(pos);
      s4.write(pos);
      delay(5);
    }
  }

  // Hold at 90°
  s1.write(90);
  s2.write(90);
  s3.write(90);
  s4.write(90);

  while (true); // Stop loop
}
```

---
 Part 2 – Humanoid Walking Algorithm

Steps:

1. Start in a stable standing position.
2. Shift the center of gravity to the **right leg**.
3. Lift the **left leg** by bending the **hip** and **knee**.
4. Move the **left leg forward** and place it on the ground.
5. Shift the weight to the **left leg**.
6. Lift the **right leg**, move it forward, and place it down.
7. Repeat steps 2–6 for continuous walking.
8. Swing arms in the **opposite direction** for balance.
9. Use servos for:
   - Hips (lifting legs)
   - Knees (bending)
   - Ankles (optional)
   - Arms (balancing motion)

---



This project combines hardware-based servo control with logical algorithm design for humanoid robot locomotion. Ideal for beginners working with Arduino and robotics logic.
