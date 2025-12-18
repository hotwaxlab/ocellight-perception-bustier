# Firmware  
### Making Proximity Glow
The firmware for **Ocellight: The Perception Bustier** is responsible for a simple but expressive task: listening to the space around the body and responding with light.
Rather than attempting to be clever, adaptive, or opaque, the firmware favors immediacy and legibility. When something approaches, the garment reacts. When it moves away, the light recedes. Cause and effect are intentionally visible.
This is not a system that watches. It is a system that *senses*.
---
## Core Behavior
At its heart, the firmware performs a continuous loop:
1. Read proximity values from each sensor  
2. Map distance to color and brightness  
3. Update the corresponding LED ocelli  
4. Repeat, smoothly and predictably  

There is no data logging, wireless transmission, or background processing. All sensing is local, momentary, and embodied.
---
## Design Principles
The firmware is shaped by a few guiding ideas:
- **Transparency:** Sensor input maps directly to output behavior  
- **Predictability:** No hidden states or unexpected modes  
- **Low Cognitive Load:** Light communicates without demanding attention  
- **Graceful Failure:** If something breaks, it does so visibly  

The goal is not to simulate intelligence, but to extend perception.

---

## Sensor Handling

Each proximity sensor operates independently, allowing the garment to respond directionally rather than globally.

- Sensor thresholds are configurable  
- Response curves are tuned for human-scale distances  
- Noise filtering is intentionally minimal to preserve responsiveness  

The system favors immediacy over precision; a felt warning is more useful than a perfect measurement.

---

## LED Ocelli Mapping

Each sensor controls a cluster of LEDs—an ocellus.

- Color shifts indicate proximity  
- Brightness increases as distance closes  
- Patterns are designed to be glanceable and peripheral  

Light is used as a biological metaphor, not a display.

---

## Timing & Performance

The firmware loop is designed to run continuously without blocking or noticeable latency.

- Update rates prioritize smooth fades over sharp transitions  
- Power draw is kept low to support extended wear  
- Thermal output is monitored through conservative duty cycles  

The body should never feel like it is wearing a computer.

---

## Configuration

Key parameters—thresholds, color ranges, and timing—are exposed as constants within the code.

Builders are encouraged to tune these values based on garment placement, sensor choice, and personal comfort.

---

## Open Source Use

This firmware is shared as part of an open hardware project.

You are encouraged to adapt, simplify, or repurpose it for other wearable or body-mounted interfaces. If you do, consider how behavior, feedback, and failure will be *felt*, not just measured.

---

## Notes for Builders

Before wearing:

- Test all sensors individually  
- Verify LED behavior under varied lighting  
- Monitor heat during extended operation  

Firmware is part of the garment’s voice. Listen closely to how it speaks.
