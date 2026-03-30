# Tacoma Gear Pattern Assist

## What this does
AI-assisted workflow for setting up ring and pinion gears on a Toyota Tacoma.

This skill helps a technician:
- interpret gear mesh patterns (drive + coast)
- avoid false acceptance
- apply correct shim adjustments
- reach manufacturer-spec gear setup
- validate setup using a confirmation-pass workflow

---

## Who this is for
- Automotive technicians
- DIY mechanics working on 4x4 drivetrains
- Shops installing aftermarket gear sets (Yukon, Nitro, etc.)

---

## Supported scope
- Toyota Tacoma differentials
- Aftermarket ring & pinion gear installs
- New and used gear setups
- Pattern-based pinion depth adjustment

---

## Required inputs
The skill expects:

- Drive-side pattern image
- Coast-side pattern image
- Backlash measurement (inches)
- Gear condition:
  - `new`
  - `used`

---

## Workflow

1. Capture gear pattern (drive + coast)
2. Provide backlash value
3. AI analyzes pattern
4. AI recommends:
   - increase pinion depth
   - decrease pinion depth
   - recapture images
5. Repeat until pattern is acceptable
6. Complete confirmation passes
7. Accept setup

---

## Acceptance Gate (Critical)

The system will NOT allow completion unless:

- Backlash is provided
- Both drive and coast images are present
- Images are readable
- Drive AND coast patterns are centered
- Confidence is at least medium
- 2 confirmation passes are completed

---

## Confirmation Pass Workflow

Once pattern appears acceptable:

- Pass 1:
  - repaint gears
  - capture new pattern
- Pass 2:
  - confirm pattern still centered

Only after both passes:
→ Setup is accepted

---

## Recovery Behavior

If the system detects repeated uncertainty:

- Requests better images (lighting / clarity)
- After repeated failures:
  - applies micro-adjustments
- Near spec:
  - switches to fine adjustment mode

---

## Example Usage

Input:
- drive: centered
- coast: centered
- backlash: 0.006

Output:
- classification: acceptable
- action: confirmation pass required

---

## Safety Notes

- Never accept a pattern based on a single observation
- Always verify coast-side pattern
- Always repaint gears between checks
- Do not skip confirmation passes

---

## Known Limitations

- Pattern interpretation assumes correct preload setup
- Does not validate torque specs or bearing preload
- Not yet tied to real image recognition (pattern assumed via input)

---

## Future Roadmap

- Vision model for real pattern recognition
- Manufacturer-specific pattern tuning
- Integration with scan tools (XTool, etc.)
- Technician performance scoring

---
