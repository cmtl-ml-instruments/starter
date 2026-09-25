# Resources

Links, not files. Everything here is something you can open, read, and follow on
your own. Finding the rest is part of the work.

## Your board

You have one of two, and they work the same way:

- 2.8 inch — https://www.lcdwiki.com/2.8inch_ESP32-S3_Display
- 3.5 inch — https://www.lcdwiki.com/3.5inch_ESP32-S3_Display

## The code

- Arduino language reference — https://docs.arduino.cc/language-reference/
- ESP32 Arduino documentation, for anything the Arduino docs don't cover —
  https://docs.espressif.com/projects/arduino-esp32/en/latest/
- Class starter code — https://github.com/cmtl-ml-instruments/starter

## Your sensors

- LSM6DSOX accelerometer and gyroscope, wiring and example code —
  https://learn.adafruit.com/lsm6dsox-and-ism330dhc-6-dof-imu
- VL53L4CX distance sensor, same —
  https://learn.adafruit.com/adafruit-vl53l4cx-time-of-flight-distance-sensor

## Getting numbers into Max

- Max's `serial` object — https://docs.cycling74.com/max8/refpages/serial
- Arduino's `Serial.println()`, the other end of the same pipe —
  https://docs.arduino.cc/language-reference/en/functions/communication/serial/println/

The board prints one number per line. Max reads bytes, so the patch has to
gather the bytes between line breaks and turn them back into a number.

## Machine learning that maps gestures to sound

- Wekinator, the tool this whole field grew out of — http://www.wekinator.org/
- Fiebrink & Sonami, the paper you read —
  https://www.nime.org/proceedings/2020/nime2020_paper45.pdf

### iris

- **The library** — https://github.com/kylebsmith/iris
  A small C library that learns the mapping from sensor readings to sound settings
  from a handful of demonstrations, on the board itself, with nothing to install.
  Three calls: `iris_record` (this gesture goes with this sound), `iris_train`
  (learn it), `iris_predict` (play). The smallest complete sketch is
  `examples/iris_smallest/`. It is the embedded descendant of Wekinator's
  record, train, play loop.
- **The starter kit** — https://github.com/kylebsmith/iris-starter
  Sketches that run on your board with a motion sensor. Setup is in
  `GET-STARTED.md`, parts and wiring in `PARTS.md`, and fixes for the usual
  problems in `TROUBLESHOOTING.md`. In this order:
  1. `iris_scope`, with its Processing plotter — the curve demo from class. Watch
     it learn, bend it with a bad demonstration, delete that one, watch it recover.
  2. `iris_tilt` — play it by tilting the board.
  3. `boilerplate/any_sensor` — plug in your own sensor.
  4. `iris_instrument` — the board becomes a MIDI controller for a synthesizer.

**Board settings**, under Tools with ESP32S3 Dev Module selected: USB Mode
*USB-OTG (TinyUSB)* · USB CDC On Boot *Enabled* · Flash Size *16MB* · PSRAM
*OPI PSRAM* · Partition Scheme *16M Flash (3MB APP/9.9MB FATFS)* · Upload Mode
*USB-OTG CDC (TinyUSB)*. The last one is the one people miss: without it your
second upload fails with `No serial data received`. Serial Monitor at 115200.

**Where it fits.** Get your sensors reading first, and get your sound responding
to something, anything. iris goes in between once both work: it replaces a
mapping you could never write down by hand — several sensors, several sound
controls, messy numbers underneath — with one you demonstrate instead. Anything
you can write as a simple rule, write it by hand.

## From class

- **What the machine is actually doing** (`what-the-machine-is-actually-doing.pdf`)
  — how a machine learns by trial and error (the pole-balancing machine, and the
  problem of working out which of its own actions to blame), and why learning from
  a few demonstrations means fitting a curve through them: guess, measure how
  wrong, nudge, repeat. Delete a bad demonstration and the curve re-fits. Figures
  and explanations from a 1988 tutorial by Jeff Smith, used with his permission.

## Finding your own

The NIME archive is every paper in this field, free —
https://www.nime.org/archives/

Two threads worth pulling on, both open questions in the field rather than
settled answers:

- **Instruments made of several devices.** More than one board, more than one
  player, or an instrument spread across a room. Search the archive for
  *network*, *distributed*, *ensemble*, *telematic*.
- **The instrument as an environment.** The idea that a player, an instrument
  and a room shape each other, so an instrument isn't a set of controls to be
  commanded — it pushes back, and playing is adapting to it. Sonami's Spring
  Spyre is the example you've already read. Search for *ecological*,
  *affordance*, *performance ecosystem*.

If you find something good, put it in your mood board with a line on why.

## Synthesis

- AMY, a synthesizer library that runs on this board — https://github.com/shorepine/amy

## Papers

The one everyone read:

- Fiebrink & Sonami, *Reflections on Eight Years of Instrument Creation with
  Machine Learning* — https://www.nime.org/proceedings/2020/nime2020_paper45.pdf

What you found in week one, so the rest of us can read them too:

- *IMPSY*, machine learning that plays alongside you —
  https://nime.org/proceedings/2026/nime2026_16.pdf
- *Dextoria*, guitar effects controlled by the gestures guitarists already make —
  https://nime.org/proceedings/2024/nime2024_56.pdf
- *iXeRemin*, a mixed-reality instrument played with fingertips —
  https://nime.org/proceedings/2026/nime2026_136.pdf
- *SenSynth*, a phone's sensors mapped to a synthesizer —
  https://www.nime.org/proceedings/2012/nime2012_149.pdf
- *Machine Learning for a Music Glove Instrument* —
  https://arxiv.org/abs/2001.09551
- *Networked Remote Music Collaboration using Machine Learning* -
  https://ieeexplore.ieee.org/document/9027481
