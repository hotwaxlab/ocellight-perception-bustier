# ocellight-perception-bustier
### Ocellight: The Perception Bustier

Inspired by the facial features of your friendly neighborhood spider, **Ocellight: The Perception Bustier** is an open-source wearable that manifests nearby motion through domes of illuminating ocelli embedded in a symbolically charged female garment.

Proximity becomes light. Personal space becomes visible. What is usually felt subconsciously is made explicit — sensed and seen on the body.

This project explores how sensing technology can be integrated into wearables in ways that feel visceral rather than ornamental, expressive rather than distracting. Beyond adding electronics “because we can,” Ocellight asks what it means to *wear* perception.

---

## What This Is

Ocellight = [Ocelli](https://en.wikipedia.org/wiki/Simple_eye_in_invertebrates "Wikipedia: Simple eye in invertibrates") + Light

**Ocellight** is a body-mounted proximity-sensing system that translates spatial awareness into immediate visual feedback using light.

- Environmental objects approach  
- Sensors detect distance  
- Clusters of LED form “ocelli” that respond in color and intensity  

The result is a wearable interface that reacts to the world around it without screens, sound, or notifications – borrowing from non-human vision systems to extend human awareness.

---

## Why a Bustier?

The form is intentional.

As a symbolically-charged garment worn on the chest, Ocellight intersects with ideas of vulnerability, visibility, and personal boundaries — particularly as they relate to female bodies. The flashing ocelli act as both warning and signal: a biological metaphor rendered in electronics. In the same way spider eyes sense proximity as danger, so too do the bustier cups of Ocellight.

This project leverages electronics to advance wearable art to a design space rich with social meaning.

---

## Hardware Overview

Under the theatrics is a relatively straightforward hardware system:

- **Sensors:** Proximity sensors selected for short-range, human-scale interaction  
- **Outputs:** LED clusters chosen for immediate, glanceable feedback without screens  
- **Control:** Microcontroller-based system with simple, predictable behavior
- **Intensity:** Potentiometer controls light brightness
- **PCB:** Custom board used to reduce wiring complexity and improve reliability  
- **Power:** Designed for low current draw and manageable thermal output  

A high-level hardware and PCB overview can be found in  
`hardware/pcb/overview.pdf`.

---

## Firmware

Sensor input is mapped directly to light output, with tunable thresholds and transparent behavior. Without any obfuscated decision-making, environmental cause and effect are made plain and visible.

Algorithms for lighting pattern mimics the jitters of life-like fluctuations, smoothing out various signal spikes and dips.

More detail is available in `firmware/README.md`.

---

## Wearability as a Constraint

Building electronics for the body means designing for:

- Curved and moving surfaces  
- Heat near skin  
- Cable strain and connection fatigue 
- Component moisture and heat tolerance 
- Comfort and safety over time  
- Public visibility and performance  

These constraints shape every part of the system, from component placement to firmware timing.

---

## Open Source Intent

Ocellight is shared as an open hardware case study.

- Hardware files, firmware, and documentation are intended for reuse  
- The architecture is modular and adaptable beyond this garment  
- Patterns documented here may be useful for other wearable, assistive, or expressive interfaces  

---

## Media

- **Demo video:** see `media/demo-video.md`  
- **Process and build images:** available in `media/photos/`

---

## Project Status

This repository documents an active prototype.

The design continues to evolve through iteration, presentation, and use.

---

## Acknowledgements

This project is made possible by the Designer Development Award from the [**World of WearableArt**](https://worldofwearableart.com "World of WearableArt Website") in New Zealand.

---

## Contact

Questions, reuse inquiries, and collaborations are welcome via this repository.
