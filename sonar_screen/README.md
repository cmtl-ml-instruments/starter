# Starter

Setup and code for each session. Copy it, flash it, then make it your own.

## Setup (once)

1. **Install Arduino:** [arduino.cc/en/software](https://www.arduino.cc/en/software)
2. **Add the ESP32 boards:** in Arduino, **Tools → Board → Boards Manager**, search `esp32`, install **esp32 by Espressif Systems**. It's a big download, so start it first.
3. **Add the screen library:** **Tools → Manage Libraries**, search `Adafruit ILI9341`, install it, and choose **Install all** when asked.

<details>
<summary><code>esp32</code> doesn't show up in the Boards Manager?</summary>

Open **Arduino IDE → Settings** (Mac) or **File → Preferences** (Windows), paste this into **Additional boards manager URLs**, and search again:

```
https://espressif.github.io/arduino-esp32/package_esp32_index.json
```
</details>

## Distance sensor

**Wire it** to the board's small four-pin socket:

| Sensor | Board |
|---|---|
| VCC | 3V3 (not 5V) |
| GND | GND |
| Trig | IO15 (SCL) |
| Echo | IO16 (SDA) |

**Flash it:**

1. Open [`sonar_screen/sonar_screen.ino`](sonar_screen/sonar_screen.ino) and click **Copy raw file** (top right of the code).
2. In Arduino: **File → New Sketch**, select everything, paste.
3. **Tools → Board → esp32 → ESP32S3 Dev Module**, then **Tools → Port** → the one that appeared when you plugged in.
4. Click **Upload** (the arrow).

Move your hand in front of the sensor. To see it as a moving line on your laptop, set **Tools → USB CDC On Boot → Enabled**, upload again, and open **Tools → Serial Plotter**.

**Upload fails?** Hold **BOOT**, tap **RESET**, let go of **BOOT**, and upload again. Tap **RESET** when it finishes.
