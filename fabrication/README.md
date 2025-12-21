# Ocellight: The Perception Bustier

#### Open-Source Wearable Hardware Project

### Firmware

---

## Overview

The user interface encapsulated by the firmware is shaped by a number of design principles:

- **Transparency**: Sensor input maps directly to output behavior
- **Predictability**: No hidden states or unexpected modes
- **Low cognitive load**: Light communicates without demanding attention
- **Graceful failure**: If something breaks, it does so visibly

The goal is not to simulate intelligence, but to extend perception.

---

## Core Behavior

The firmware logic loop (heartbeat) continuously performs the following sequence:

1. Read the proximity value (distance to nearest object) of each sensor
1. Read the position of the wearer-adjustable potentiometer
1. Apply time-based smoothing to all the above readings
1. Compute the color and base brightness of each pixel, using a distance-weighted PID (proportional&ndash;integral&ndash;differential) mapping to merge the proximity values from both sensors with a default (background) texture
1. Apply an overall brightness modifier to all pixels, according to the position of the brightness potentiometer
1. Drive each LED accordingly

If serial communication is enabled, the firmware can communicate key operational parameters to a debugger/monitor, and an external user can query and modify the firmware’s behavior.

All sensing and recording is local and short-term.
There is no long-term data logging, wireless transmission, etc.

---

### Ultrasonic Sensor Tuning

Each proximity sensor operates independently, giving the garment’s responses a certain amount of directionality.

Sensor thresholds, response curves, and ping frequencies are tuned for human-scale distances and interactions.

---

### LED Interpretation

Inputs received from the sensors are continually mapped to the individually addressable LEDs within each cup in multiple ways:

- Noticeability:

	- Patterns are noticeable to an observer who views them either directly or peripherally
	- The wearer has limited ability to observe the LED patterns directly

- Parsability:

	- Patterns can be parsed at a glance
	- Color shifts indicate proximity
	- Brightness increases as distance closes
	- Background can be set to an appropriate color or texture

---

### Timing and Performance

The firmware loop runs continuously and regularly.

- Blocking and noticeable latency are avoided
- Update rate prioritizes smooth fades over sharp transitions
- Low power draw supports extended wear (on the order of 100s of minutes for )
- Conservative duty cycles help temper thermal output

System startup takes less than two seconds.

---

## Operational Parameters and Future Expandability

The modular firmware design supports adding and swapping various components and behaviors.

Several operational parameters are exposed as constants within the code.
These include minimum and maximum proximity, color ranges and patterns, loop frequency, and smoothing functions.

Builders are encouraged to tune and alter these values, particularly based on such use considerations as ambient lighting, sensor sensitivity, and wearer comfort.

[//]: # (
\ TODO: Things that can interfere: other sensors sending while one is still listening for an echo
)

See the [expansion ideas][expansion-ideas] file for some suggested avenues of inquiry.

[expansion-ideas]: /docs/expansion-ideas.md "Expansion ideas"

---

## Limitations and Workarounds

### Proximity Measurement Precision

Each ultrasonic sensor signal is converted to a *z-*<span></span>distance by multiplying the round-trip delay time by one-half the speed of sound.
This is subject to a number of limitations, including the following:

1. The strength of the echo detected by each ultrasonic sensor may vary based on such factors as the number, size, composition, configuration, and acoustic reflectivity of the intruding object(s).

1. Due to temporal disconnects within and between the microcontroller unit and the ultrasonic transmitter and receiver, the round-trip delay time cannot be measured exactly.
A hard-wired correction value is applied; its value is an approximation and is based on a calibration procedure performed during development.

1. The apparent speed of sound in air varies with ambient temperature, humidity, wind velocity, and other parameters (though not, interestingly, with altitude).
The distance conversion uses a nominal speed value that is approximately correct over a reasonable range of anticipated conditions.
No calibration is performed, and there are no sensors to detect ambient temperature, humidity, wind velocity, etc.

1. The minimum round-trip flight time that can be measured must be somewhat greater than the duration of the sensing pulse (200&thinsp;&micro;sec. = eight cycles of a 40&thinsp;kHz signal).
This corresponds to a proximity of roughly 4&thinsp;cm under standard conditions.

Due to these and other environmental and timing uncertainties, the empirically observed measurement granularity (&plusmn;4&thinsp;cm) is somewhat larger than the value computed for an ideal physical system (&plusmn;3&thinsp;mm).
However, **Ocellight** favors responsiveness over precision in any case, since for its purposes, a “felt” warning is not only as good as, but in many ways more apropos than, a perfect measurement.

---
