# Accessibility & Photosensitive Epilepsy Safety

**AstrOsint01 — Earth in Transition**  
NASA Space Apps Challenge 2026

This document describes how AstrOsint01 is designed to minimize risk for users with photosensitive epilepsy and related seizure disorders. All measures are grounded in official standards and peer-reviewed guidance.

---

## 1. Core Commitment

Scientific evidence should never put users at physical risk.

AstrOsint01 is built with the explicit goal of being **usable and safe** for people with photosensitive epilepsy. We treat this as a non-negotiable design requirement, not an optional enhancement.

---

## 2. Official Standards Applied

### WCAG 2.2 Success Criterion 2.3.1 — Three Flashes or Below Threshold (Level A)

> Web pages do not contain anything that flashes more than three times in any one second period, or the flash is below the general flash and red flash thresholds.

**Source:** W3C Web Accessibility Initiative  
https://www.w3.org/WAI/WCAG22/Understanding/three-flashes-or-below-threshold.html

### WCAG 2.2 Success Criterion 2.3.2 — Three Flashes (Level AAA)

> Web pages do not contain anything that flashes more than three times in any one second period.

This stricter criterion removes exceptions based on size or brightness. AstrOsint01 targets this higher standard.

**Source:** W3C  
https://www.w3.org/WAI/WCAG22/Understanding/three-flashes.html

---

## 3. Key Risk Factors for Photosensitive Seizures

According to the Epilepsy Foundation and international consensus:

- Flashing frequencies between approximately **3 Hz and 30 Hz** (especially 10–20 Hz) carry the highest risk.
- **Saturated red** flashing is more provocative than other colours.
- Large area of the visual field occupied by the flash increases risk.
- High contrast between light and dark states increases risk.
- Certain static patterns (high-contrast stripes, checkerboards) can also act as triggers.

**Primary sources:**
- Epilepsy Foundation — Photosensitivity and Seizures  
  https://www.epilepsy.com/what-is-epilepsy/seizure-triggers/photosensitivity
- Fisher et al. (2025/2026). Visually-provoked seizures: Consensus of the Epilepsy Foundation Working Group. *Epilepsia*.  
  https://doi.org/10.1111/epi.18702

---

## 4. Design Rules Implemented in AstrOsint01

| Rule | Implementation |
|------|----------------|
| **No content flashes more than 3 times per second** | Strictly enforced. No decorative strobing, pulsing loaders, or high-frequency animations. |
| **Respect `prefers-reduced-motion`** | All non-essential motion is disabled when the user has this system preference enabled. |
| **Manual Safe Mode** | Users can activate a global “Safe Mode” that removes remaining transitions and animations. |
| **No saturated red flashing** | Colour palette avoids pure red strobing effects. |
| **Data tables always available** | Every chart has a structured, screen-reader accessible data table alternative. |
| **Keyboard & screen-reader support** | Full navigation without reliance on motion or visual-only cues. |
| **Optional data sonification** | Trends can be explored through sound, reducing dependence on visual motion. |

---

## 5. Practical Implementation Measures

- CSS media query for `prefers-reduced-motion: reduce` forces near-zero animation duration.
- Global attribute `data-epilepsy-safe="true"` disables remaining transitions when Safe Mode is active.
- Charts use static or very slow transitions only.
- Map interactions avoid rapid zoom/pan animations by default.
- No autoplaying video or GIF content with potential flash risk.
- All visual change is under user control wherever possible.

---

## 6. Testing Commitment

Accessibility features will be **tested**, not merely declared.

Planned verification includes:

- Manual review of all interactive components for flash frequency.
- Testing with operating-system “Reduce Motion” enabled.
- Keyboard-only navigation testing.
- Screen-reader testing (VoiceOver / NVDA).
- Optional use of tools such as the Photosensitive Epilepsy Analysis Tool (PEAT) for any media assets.

---

## 7. References (Primary Sources)

1. W3C. *Understanding SC 2.3.1: Three Flashes or Below Threshold* (WCAG 2.2).  
   https://www.w3.org/WAI/WCAG22/Understanding/three-flashes-or-below-threshold.html

2. W3C. *Understanding SC 2.3.2: Three Flashes* (WCAG 2.2).  
   https://www.w3.org/WAI/WCAG22/Understanding/three-flashes.html

3. Epilepsy Foundation. *Photosensitivity and Seizures*.  
   https://www.epilepsy.com/what-is-epilepsy/seizure-triggers/photosensitivity

4. Fisher, R. S., et al. (2025/2026). Visually-provoked seizures: Consensus of the Epilepsy Foundation Working Group. *Epilepsia*.  
   https://doi.org/10.1111/epi.18702

5. MDN Web Docs. *Web accessibility for seizures and physical reactions*.  
   https://developer.mozilla.org/en-US/docs/Web/Accessibility/Guides/Seizure_disorders

6. Epilepsy Action (UK). *Photosensitive epilepsy and online content*.  
   https://www.epilepsy.org.uk/press/photosensitive-epilepsy-and-online-content

---

**AstrOsint01 OSINT Cell**  
Accessibility is a core requirement, not an afterthought.
