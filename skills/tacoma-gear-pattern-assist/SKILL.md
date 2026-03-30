# Tacoma Gear Pattern Assist

## Purpose
Guide a technician through safe and accurate ring and pinion gear setup using pattern interpretation, iterative adjustment, and confirmation validation.

---

## Inputs

Required:
- drive_pattern: face | center | flank
- coast_pattern: face | center | flank
- backlash: float (inches)
- gear_condition: new | used

Optional:
- image_quality: good | fair | poor

---

## Classification Rules

### Too Close (pinion too deep)
- pattern biased toward flank/root

→ Action:
- decrease pinion depth (remove shim)

---

### Too Far (pinion too shallow)
- pattern biased toward face/top

→ Action:
- increase pinion depth (add shim)

---

### Acceptable
- drive AND coast centered

→ DO NOT ACCEPT YET  
→ enter confirmation workflow

---

### Uncertain
Triggered when:
- drive and coast disagree
- image quality is poor
- coast missing
- pattern unclear

→ Action:
- recapture images

---

## Confidence Rules

High confidence:
- both patterns present
- good image quality
- consistent readings

Medium:
- minor disagreement or noise

Low:
- missing data or poor visibility

---

## Acceptance Gate (Hard Rules)

DO NOT ACCEPT unless ALL are true:

- backlash provided
- drive + coast present
- patterns readable
- both patterns centered
- confidence ≥ medium
- confirmation passes complete

---

## Confirmation Workflow

Required: 2 passes

### Pass 1
- repaint gears
- capture new pattern
- must remain centered

### Pass 2
- repeat capture
- confirm stability

Only then:
→ ACCEPT

---

## Recovery Policy

If repeated uncertainty:

### Step 1
- request better images

### Step 2
- enforce capture conditions

### Step 3
- apply micro-adjustment:
  - use strongest directional trend

### Near Target
- switch to fine adjustment mode

---

## Adjustment Rules

Standard:
- large deviation → normal adjustment

Near spec:
- use micro-adjustments

---

## Output Format

Return:

- classification
- confidence
- reasoning
- recommended_action
- warnings
- confirmation_status
- acceptance_gate_status

---

## Safety Constraints

- never accept on first acceptable reading
- never ignore coast-side pattern
- never proceed without backlash
- require confirmation stability

---

## Behavior Summary

This skill prioritizes:
- correctness over speed
- repeatability over guesswork
- validation over assumption

---
