# Ocellight: The Perception Bustier

#### Open-Source Wearable Hardware Project

### Expansion Ideas

---

## Overview

This document gives a number of suggestions for extending and altering **Ocellight**.
Those interested in adapting the project are encouraged to think in these and other directions.

---

## Physical Configuration

The original physical configuration of **Ocellight** is that of a bustier resembling a giant spider’s head, its cups reminiscent of ocelli.
The original conception&mdash;as a spatial and temporayl visualization of the dynamics of personal space&mdash;remains central to the project’s initial context, but expansion projects need not hew to it with any particular fidelity.
Configuration options are not limited to the arachnids, nor even to existing lifeforms as a whole, and may include fantastical creatures and non-representational constructions.

Multiple instances of **Ocellight** may also be designed to interact with one another, cooperatively as well as competitively.

---

## Hardware

The modular hardware design of **Ocellight**, based around a multi-channel microcontroller, supports adding and swapping various peripherals and key components, including:

- Input devices

	- Sensors

		- Ultrasonic
		- Thermal
		- Humidity
		- Motion
		- Capacitive touch
			- e.g., to distinguish objects closer than the minimum proximity of the ultrasonic sensors
		- Infrared
			- e.g., to distinguish live intruders from inanimate ones
		- Inertial measurement units/accelerometers/GPS modules
			- e.g., to distinguish between being approached and approaching an object

	- Camera

	- Tuning/selection devices

		- Hue potentiometer
		- Sensitivity potentiometer

- Output devices

	- Additional LED clusters (many spiders have eight ocelli)
	- Individual LEDs
	- Actuators
	- Speakers/sound generators

- Combined input/output devices

	- Wireless communication (WiFi, Bluetooth, etc.)

- Microcontrollers

	- Alternative options, including single-board computers (SBCs)

---

## Firmware

### Tuning

The algorithm that converts proximity information to visible light patterns can be tuned in various ways, including:

- Smoothing functions

	- The nominal smoothing function used by the sensors and the brightness potentiometer is a moving average.
Modifications that could be made include:
		- Window size
		- Sampling frequency
	- Other functions could be used, e.g.:
		- Median filter
		- Outlier discarding

- Attack, decay, sustain, release (ADSR) parameters

	- The nominal behavior of the LED displays is to react immediately to the intrusion of an object into the space, to remain steadily lit while the object’s proximity remains unchanged, and to fade back to baseline only gradually after the object departs.
	- This can be modified by applying different ADSR curves.

- Color mixing

	- The mixing function used to determine the color of each pixel at any given moment uses a weighted PID function.
	- This function can be modified or replaced.
	- Noise and jitter can be added to give less deterministic results.

- Frame rate

	- The nominal frame rate is around 20&thinsp;Hz.
	- Higher or lower frame rates may give different visual smoothness and different apparent responsiveness.

### Expansion

Overall processing capabilities can be expanded in nearly limitless ways, including:

- Memory/history

	- E.g., a second approach within a short period of time might give a more “fearful” light pattern
	- E.g., the longer an intruder lingers, even without moving, the “angrier” the light pattern might become

- Pattern shaping

	- E.g., both ocelli look “toward” the nearest object like tracking eyes

- Communication capabilities

	- Some microcontrollers support wireless communication (e.g., WiFi, Bluetooth)
	- The unit could interact with its environment
	- Multiple units could interact with one another

---
