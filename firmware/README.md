# Ocellight: The Perception Bustier

#### Open-Source Wearable Hardware Project

### Firmware

---

## Design Principles

The user interface encapsulated by the firmware is shaped by a number of guiding ideas:

- **Transparency**: Sensor input maps directly to output behavior
- **Predictability**: No hidden states or unexpected modes
- **Low cognitive load**: Light communicates without demanding attention
- **Graceful failure**: If something breaks, it does so visibly

The goal is not to simulate intelligence, but to extend perception.

---

## Core Behavior

The firmware logic loop (heartbeat) continuously performs the following sequence:

1. Read the proximity value of each sensor
1. Apply time-based smoothing to those values
1. For each pixel in both ocelli, perform a PID (proportional&ndash;integral&ndash;differential) mapping of both proximity values to color and brightness
1. Apply a brightness modifier, based on the position of a wearer-adjustable potentiometer.
1. Drive each LED accordingly

If serial communication is enabled, the firmware can communicate key operational parameters to a debugger/monitor, and an external user can drive and modify the firmware's behavior.

All sensing and recording is local and short-term. There is no long-term data logging or wireless transmission.

---

## Hardware Considerations

### Ultrasonic Sensors

Each proximity sensor operates independently, allowing the garment to respond directionally rather than globally.

- Sensor thresholds are configurable
- Response curves are tuned for human-scale distances
- Noise filtering is intentionally minimal to preserve responsiveness

The system favors immediacy over precision; a felt warning is more useful than a perfect measurement.

### LEDs

Each cup of the bustier represents an *ocellus* *(pl. ocelli),* the simple eye found in many spiders and other creatures.

Within the cup lies a cluster of individually addressable LEDs.
Continuous inputs received from the sensors are mapped to the LEDs in multiple ways:

- Noticeability:
	- Patterns are noticeable to an observer who views them either directly or peripherally
	- The wearer has limited ability to observe the LED patterns directly
- Parsability:
	- Patterns can be parsed at a glance
	- Color shifts indicate proximity
	- Brightness increases as distance closes
	- Background can be set to a visually intriguing color or texture

---

## Timing and Performance

The firmware loop runs continuously and regularly.

- Blocking and noticeable latency are avoided
- Update rate prioritizes smooth fades over sharp transitions
- Low power draw supports extended wear (on the order of 100s of minutes for )
- Conservative duty cycles help temper thermal output

System startup takes less than two seconds.

---

## Configuration

### Key Parameters

Various operational parameters are exposed as constants within the code.
These include minimum and maximum proximity, color ranges and patterns, loop frequency, and smoothing functions.

Builders are encouraged to tune these values, particularly based on such use considerations as ambient lighting, sensor parameters, and personal comfort.

?? can also change the smoothing function. We use a moving average. Could use median filter or other.

?? things that can interfere: other sensors sending while we're listening for an echo

### Perceived Limitations

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

---

## Open Source Use

This firmware is shared as part of an open hardware project.

You are encouraged to adapt, simplify, or repurpose it for other wearable or body-mounted interfaces.
If you do, consider how behavior, feedback, and failure will be *felt,* not just measured.

---
