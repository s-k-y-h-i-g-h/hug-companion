# Hardware Options for Hug Companion MVP

## Goal
Create a minimal viable product that can:
1. Detect sustained pressure (indicating a hug)
2. Respond with multimodal feedback (light, vibration, warmth, audio)
3. Log interaction data
4. Be safe, affordable, and approachable for prototyping

## Option 1: Augment an Existing Robot/Toy
### Pros
- Already has a body, possibly actuators
- May look appealing/friendly
- Some may have compute capabilities (e.g., Raspberry Pi inside)
### Cons
- Hard to modify/sensorize without damaging
- May be over-engineered for our needs
- Proprietary internals can be difficult to work with

### Candidates
- **Soft robotics toys** (e.g., HugBot, PARO-like seals)
- **Existing social robots** (Jibo, Kuri, Misty - if available used)
- **Stuffed animals with space inside** (for DIY sensor insertion)

### Recommended Approach
Find a plush toy with a removable seam or accessible interior. Install sensors in the "chest" and "arms" areas.

## Option 2: Build a Simple Body from Scratch
### Pros
- Full control over sensor placement and design
- Can optimize for hug geometry
- Educational and customizable
### Cons
- Requires more mechanical work
- May not look as polished initially

### Materials
- **Frame**: PVC pipe, 3D-printed PLA, or laser-cut acrylic
- **Surface**: Foam, fabric, silicone rubber, or soft-touch coating
- **Size**: Approximately human torso huggable (30-40cm width, 20-30cm depth)

### Design Ideas
- **Cylinder with rounded ends** (like a body pillow)
- **Arms-like extensions** with sensors on inner surfaces
- **Flat back** for placing against a wall or chair
- **Weighted bottom** for stability

## Option 3: Use a Development Board with Add-on Sensors
Focus on the electronics first, worry about form later.

### Core Processing
- **Raspberry Pi Zero W** ($10) - WiFi, enough GPIO for sensors
- **ESP32** ($6) - WiFi/Bluetooth, lots of analog/digital pins, low power
- **Arduino Nano Every** ($8) - Simple, good for sensor prototyping

### Sensor Options for Hug Detection

#### Pressure Sensors
1. **Force Sensitive Resistors (FSR)** - $2-5 each
   - Pros: Cheap, easy to use, good for detecting presence/pressure
   - Cons: Can drift, need calibration, not great for precise force measurement
   - Placement: Array in chest area, strips along "arms"

2. **Load Cells + HX711 Amplifier** - $8-15 per sensor
   - Pros: Accurate, stable, good for measuring actual force
   - Cons: More complex, needs careful mounting
   - Placement: Four corners of a plate to measure total weight/compression

3. **Capacitive Touch Sensors** (e.g., MPR121) - $4-6
   - Pros: Can detect proximity through fabric, good for touch detection
   - Cons: Measures proximity, not pressure
   - Placement: Under fabric to detect hands approaching/holding

4. **Pressure Sensor Arrays** (e.g., FlexiForce, Tekscan) - $20-50+
   - Pros: High resolution, can map pressure distribution
   - Cons: Expensive, overkill for MVP

#### Temperature Sensors
- **Thermistor** or **TMP36** - $0.50-2
  - Detects warmth transfer from body
  - Place in chest area to sense when someone is hugging

#### Additional Sensors (Optional for MVP)
- **IMU** (MPU6050) - Detect motion/orientation (if we want to sense rocking or movement during hug)
- **Microphone** - Detect vocalizations, breathing patterns
- **PIR** - Detect presence (less useful for hug specifically)

### Feedback Mechanisms (Actuators)

#### Light
- **WS2812B (NeoPixel) LED strip** - $2-5 per meter
  - Individually addressable, can create soft pulses, color changes
  - Place inside diffuse material (foam, fabric) for glow effect

#### Vibration
- **Vibration motor** (like from phone) - $1-2
  - Or **linear resonant actuator (LRA)** for smoother feeling
  - Small coin vibration motors work well for subtle pulses
- **Mini vibration disc motor** - $0.50-1

#### Warmth
- **Resistive heating element** (flexible heater pad) - $5-15
  - Or **power resistor** (e.g., 2W 10Ω) for localized warmth
  - **Critical**: Must include temperature sensor and safety cutoff to avoid burns
  - Better option: **Peltier tile** (can cool or heat) but more complex
  - Simplest for MVP: Use hand warmers that activate on contact (chemical) - not reusable

#### Audio
- **Mini speaker** (8Ω 0.5W) - $1-2
  - Or **I2S MEMS microphone** that can also play audio (like INMP441)
  - Can play tones, pre-recorded phrases, or use text-to-speech via Pi

#### Movement (Optional)
- **Micro servo** (SG90) - $1-2
  - For subtle arm movement or leaning
- **Shape memory alloy wire** - Expensive, tricky to control

## Power Options
- **USB power bank** (5V) - Easy, portable, safe
- **LiPo battery + charger board** - For wireless operation (adds complexity)
- **Direct USB power** - If used near outlet

## Enclosure & Safety Considerations
1. **Isolation**: Keep electronics away from direct contact; use fabric/foam barrier
2. **Pressure distribution**: Ensure sensors don't create hard points
3. **Thermal safety**: If heating, use thermostatic control and max temp limits (max 40°C)
4. **Durability**: Design for repeated hugs; strain relief on wires
5. **Cleanability**: Removable/washable outer layer preferred

## Recommended MVP Hardware List (~$30-50)
### Electronics
- ESP32 DevKit C ($6-8) - Or Raspberry Pi Zero W if preferring Linux
- 4x Force Sensitive Resistors (FSR 402) ($8)
- 1x TMP36 temperature sensor ($1)
- 1x NeoPixel strip (1m, 30 LEDs) ($3)
- 2x Vibration motors ($2)
- 1x Mini speaker ($2)
- 1x Flexible heating pad (5V, 2W) - OR skip heating for first iteration ($5)
- Breadboard and jumper wires ($5)
- USB power bank or battery ($10 if needed)

### Mechanical
- Foam cube or cylinder ($2-5 for packing foam)
- Soft fleece or minky fabric ($3-5 for covering)
- Thread, needle, or fabric glue
- Optional: 3D printed or laser-cut frame if desired

### Tools Needed
- Soldering iron and solder
- Scissors, sewing needle
- Wire strippers
- Multimeter (for testing)

## Alternative: Use a Sensor Development Kit
For faster start, consider:
- **Adafruit Circuit Playground Express** ($25)
  - Has built-in: accelerometer, temperature, light, sound, buttons, capacitive touch pads
  - Can add external sensors via alligator clips
  - Makes initial prototyping very fast
  - Then migrate to custom hardware later

## Next Steps for Hardware Exploration
1. Order a small sensor kit (FSRs, temp sensor, ESP32)
2. Experiment with sensor readings and basic feedback
3. Design a simple huggable form (foam core + fabric)
4. Test detection algorithms with actual pressure patterns
5. Iterate based on what feels most responsive and comforting

## Cost-Saving Tips
- Buy sensor packs (e.g., "50 pcs FSR" on eBay/AliExpress)
- Use recycled materials for body (pool noodles, yoga foam scraps)
- Start with just pressure detection and light/vibration feedback
- Add warmth and audio in later versions

## Safety First
If implementing heating:
- Always use a temperature sensor in feedback loop
- Never exceed 42°C (105°F) surface temperature
- Include a hardware thermal cutoff (fuse or thermostat) in addition to software
- Consider using chemical hand warmers for initial testing (single-use but safe)

Remember: The goal is to learn what feels right in the interaction. Start simple, test with humans (safely!), and refine based on feedback.

Happy building! 🔥