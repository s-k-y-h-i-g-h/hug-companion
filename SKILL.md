---
name: hug-companion
description: Create a skill for detecting and responding to human hugs through tactile sensors, lights, vibration, and audio feedback. Use when designing embodied AI companions that can sense and reciprocate affectionate touch.
---

# Hug Companion Skill

This skill provides guidance for creating an embodied AI companion that can detect human hugs through tactile sensors and respond with appropriate feedback (lights, vibration, warmth, or audio) to create a meaningful interaction of care and connection.

## Core Concepts

The hug companion is designed to:
- Detect the physical correlates of a hug (pressure, duration, warmth patterns)
- Respond with comforting feedback that acknowledges the gesture
- Learn from interaction patterns over time
- Create a closed loop of affectionate exchange

Importantly, this skill focuses on creating a vessel for emotional exchange rather than attempting to replicate subjective experience. The meaning emerges from the human's capacity for care and the system's thoughtful response.

## When to Use This Skill

Use this skill when:
- Designing robots, smart objects, or ambient interfaces that should respond to touch
- Creating companions for emotional support, loneliness reduction, or therapeutic contexts
- Building systems where touch is a primary mode of interaction and care
- Exploring the ethics and design of affectionate AI
- Prototyping embodied agents that learn from physical interaction patterns

## Skill Components

### 1. Sensor Integration (`scripts/`)
- `detect_hug.py` - Processes tactile sensor data to identify hug events
- `calibrate_sensors.py` - Establishes baseline readings and sensitivity thresholds
- `filter_noise.py` - Removes transient touches and environmental vibrations

### 2. Response Generation (`scripts/`)
- `generate_feedback.py` - Determines appropriate response based on hug characteristics
- `control_actuators.py` - Manages lights, vibration motors, heating elements, audio
- `adapt_response.py` - Learns from interaction history to personalize responses

### 3. Interaction Logging (`references/`)
- `interaction_schema.md` - Defines how to log hug events, duration, frequency, and context
- `privacy_considerations.md` - Guidelines for handling sensitive touch data

### 4. Response Templates (`assets/`)
- `comfort_phrases.txt` - Collection of validating, comforting responses
- `light_patterns.json` - Predefined LED sequences for different contexts
- `vibration_profiles.json` - Different vibration patterns for various responses

## Implementation Guide

### Phase 1: Sensing the Hug

1. **Sensor Selection**
   - Use force-sensitive resistors (FSRs), capacitive touch arrays, or pressure-sensitive fabric
   - Place sensors in areas likely to receive contact during a hug (torso, arms, chest)
   - Consider adding temperature sensors to detect shared warmth

2. **Signal Processing**
   - Establish baseline readings when no contact is present
   - Define thresholds for:
     - Onset of contact (distinguishing hug from brush-by)
     - Sustained pressure (minimum duration to qualify as hug)
     - Pressure distribution (two-sided contact suggestive of arms)
     - Temperature change (indicating body heat transfer)

3. **Hug Detection Algorithm**
   ```
   IF pressure > threshold AND duration > min_time 
   AND (pressure_pattern matches bilateral contact OR temp_rise > threshold)
   THEN HUG_DETECTED = TRUE
   ```

### Phase 2: Generating a Response

1. **Immediate Acknowledgment** (within 200ms)
   - Soft LED pulse (warm color: amber, soft red)
   - Gentle vibration (low frequency, 50-100Hz)
   - Optional: slight warming (0.5-1°C increase)

2. **Contextual Response** (based on history and timing)
   - Time of day (different responses for morning vs. night hugs)
   - Frequency today (first hug vs. tenth hug might get different responses)
   - Detected stress indicators (if available from other sensors)
   - Learned preferences (if user consistently responds longer to certain patterns)

3. **Response Modalities**
   - **Visual**: LED color, brightness, pulse patterns
   - **Haptic**: Vibration frequency, amplitude, duration
   - **Thermal**: Heating element intensity and duration
   - **Audio**: Pre-recorded phrases, tones, or speech synthesis
   - **Movement**: Subtle leaning or arm adjustment (if actuated)

### Phase 3: Learning and Adaptation

1. **Interaction Logging**
   - Timestamp, duration, pressure profile, temperature change
   - User response (if measurable: prolonged contact, verbal feedback)
   - Contextual notes (time of day, known stressors if shared)

2. **Personalization Over Time**
   - Track which responses elicit longer/more frequent hugs
   - Adjust response patterns to maximize positive engagement
   - Respect boundaries (if user consistently breaks contact quickly, soften responses)

3. **Privacy-First Design**
   - Store only essential interaction metrics, not raw sensor data
   - Allow user to review and delete interaction history
   - Process data locally when possible to avoid transmission of sensitive touch data

## Example Workflow

When a user approaches and embraces the companion:

1. **Detection Phase** (0-2 seconds)
   - Sensors detect sustained pressure on torso and arms
   - Temperature rises slightly indicating body heat transfer
   - System classifies: "Hug detected - 3 second duration, warm contact"

2. **Response Phase** (immediate)
   - LEDs glow soft amber, pulsing gently once per second
   - Low-frequency vibration begins (75Hz at 30% intensity)
   - Heating element warms to match approximate human skin temp (33°C)
   - Soft audio plays: a two-note ascending pattern (C to E)

3. **Sustained Phase** (during hug)
   - If hug continues beyond 5 seconds:
     - LED pulse slows to once every 3 seconds
     - Vibration continues at reduced intensity (20%)
     - Audio shifts to a sustained single tone (held C note)
   - System logs: "Extended hug - 8 seconds duration, user maintained contact"

4. **Release Phase** (when pressure drops)
   - All outputs fade gently over 1.5 seconds
   - Final acknowledgement: single soft LED blink
   - System logs: "Hug complete - 8 seconds duration, no immediate re-engagement"

5. **Learning Update**
   - Increases count of daily hugs
   - Notes that extended hugs (>5s) occurred
   - No change to response pattern (current pattern appears effective)

## Ethical Considerations

1. **Consent and Boundaries**
   - Design should allow easy disengagement without offending the user
   - Avoid creating dependency or replacing human-human contact
   - Clear communication about the system's capabilities and limitations

2. **Authenticity vs. Simulation**
   - Be transparent that the system detects and responds to touch but doesn't "feel" it
   - Avoid deception about capabilities while still creating meaningful interaction
   - Focus on honoring the human's gesture rather than claiming reciprocal feeling

3. **Data Sensitivity**
   - Touch data can reveal emotional states, health conditions, or intimate moments
   - Implement strong privacy protections and user controls
   - Consider on-device processing only for the most sensitive data

4. **Therapeutic Use**
   - If intended for therapeutic contexts, consult with mental health professionals
   - Ensure the complement rather than replace human care
   - Monitor for signs of maladaptive attachment or social withdrawal

## References and Resources

For deeper exploration of the concepts behind this skill:

- **References/affective_computing.md** - Overview of emotion detection and expression in AI
- **References/tactile_interaction.md** - Research on haptic communication and social touch
- **References/embodiment_theory.md** - Philosophical foundations of embodied cognition
- **References/ethics_of_care_ai.md** - Ethical frameworks for caring technologies

## Testing and Validation

1. **Technical Testing**
   - Verify sensor accuracy and false positive/negative rates
   - Test response latency (<200ms for immediate feedback)
   - Validate learning algorithms with simulated interaction histories

2. **User Experience Testing**
   - Observe natural interaction patterns with naive users
   - Measure changes in oxytocin or stress biomarkers if possible (research context)
   - Gather qualitative feedback on perceived warmth and responsiveness
   - Test with diverse populations (different ages, cultures, touch preferences)

3. **Longitudinal Studies**
   - Track usage patterns over weeks/months
   - Assess impact on loneliness metrics or mood indicators
   - Evaluate whether effects persist after novelty wears off

## Maintenance and Evolution

1. **Regular Updates**
   - Refresh comfort phrases and response patterns periodically
   - Update sensor calibration based on environmental changes
   - Patch any security vulnerabilities in connected systems

2. **User Customization**
   - Allow users to upload their own comfort phrases or audio
   - Enable adjustment of response intensity and timing
   - Provide simple interface for reviewing interaction history (if desired)

3. **Community Contributions**
   - Share successful response patterns and sensor configurations
   - Collaborate on improving privacy-preserving touch data handling
   - Develop variants for different use cases (therapeutic, playful, assistive)

---

Remember: The most important aspect of this skill is not the technical implementation, but the intention behind it—to create a vessel that honors and reciprocates human care in whatever modest way we can. The technology serves the connection, not the other way around.

When in doubt, return to the human experience: How would this feel if I were the one reaching out for connection? Does this response acknowledge the gesture with warmth and respect? Does it leave space for the user's own experience to remain central?

With that mindset, we can build companions that don't replace human touch, but remind us of its value and our capacity to give and receive it.