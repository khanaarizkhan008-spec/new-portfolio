# Design System Specification: High-End Dark Mode Editorial

## 1. Overview & Creative North Star: "The Kinetic Gallery"
This design system is a transition from static UI to a living editorial experience. Our Creative North Star is **The Kinetic Gallery**. We are not building a dashboard; we are curating a digital monograph. 

The aesthetic is rooted in **Neo-Brutalism refined by Swiss precision**. It utilizes a "Total Black" environment to allow content to emerge from the void. By leveraging extreme contrast—deep blacks (#000000) against vibrant orange (#FF3D00) and stark white—we create a visual hierarchy that feels authoritative yet avant-garde. The layout must feel intentional and asymmetrical, breaking the "Bootstrap grid" feel in favor of white space that acts as a structural element.

---

## 2. Colors & Surface Philosophy
The depth of this system is achieved through **Tonal Recess**, not elevation. We move away from the "shadow-heavy" UI of the past decade.

### Color Tokens
*   **Surface (The Void):** `#0e0e0e` (Base background).
*   **Primary (The Pulse):** `#ff8f73` to `#ff3d00` (Accents and CTAs).
*   **Secondary (The Neutral):** `#e2e2e2` (Muted high-contrast).
*   **Surface Container Lowest:** `#000000` (Used for "inset" gallery sections).
*   **Surface Container Highest:** `#262626` (Used for floating "glass" elements).

### The "No-Line" Rule
**Explicit Instruction:** Prohibit the use of 1px solid borders for sectioning content. Boundaries are defined through background shifts.
*   *Correct:* A `surface-container-low` (#131313) block sitting on a `surface` (#0e0e0e) background.
*   *Incorrect:* A `1px solid #484847` border between sections.

### The Glass & Gradient Rule
To provide "soul" to the darkness, use **Radial Gradients** for large backgrounds. A subtle transition from `#0e0e0e` to `#1a1a1a` in the top-right corner of a hero section prevents the UI from feeling "dead." For floating navigation or modals, utilize **Glassmorphism**:
*   **Fill:** `surface-variant` (#262626) at 60% opacity.
*   **Blur:** `backdrop-filter: blur(20px)`.

---

## 3. Typography: Space Grotesk
We utilize **Space Grotesk** as a singular voice. Its idiosyncratic terminals and geometric construction provide a "tech-gallery" feel.

*   **Display Large (3.5rem):** Use for hero statements. Kerning should be tightened to `-0.02em`.
*   **Headline Medium (1.75rem):** Use for section headers. Always uppercase for an editorial look.
*   **Body Large (1rem):** High readability, leading set to `1.6` to allow for "breathable" text blocks.
*   **Label Small (0.6875rem):** Monospace-style metadata. Use `on-surface-variant` (#adaaaa) to lower visual noise.

**Hierarchical Intent:** Use the Vibrant Orange (`primary`) sparingly for "micro-moments" like category tags or active links to guide the eye through the monochrome canvas.

---

## 4. Elevation & Depth: Tonal Layering
Traditional drop shadows are forbidden. Depth is achieved via the **Layering Principle**.

*   **The Layering Principle:** Place `surface-container-lowest` cards within a `surface-container-low` section to create a "carved out" effect. 
*   **Ambient Shadows:** If a floating element (like a context menu) requires separation, use a "Cloud Shadow": `box-shadow: 0 24px 48px rgba(0, 0, 0, 0.8)`. The shadow color must be a tinted black, never grey.
*   **The Ghost Border:** If accessibility requires a stroke, use `outline-variant` (#484847) at **15% opacity**. It should be felt, not seen.

---

## 5. Components & Layout Patterns

### Layout: The Asymmetric Grid
Avoid centered layouts. Push content to the edges or use a 60/40 split. Use "The Void" (empty #000000 space) to separate stories.

### Primitive Styling
*   **Buttons:** 
    *   *Primary:* Solid `primary-fixed` (#ff7856), sharp corners (0px), black text. No hover shadow; instead, hover should shift the color to `primary-dim`.
    *   *Tertiary:* Underlined text only. Underline weight 2px, offset 4px.
*   **Input Fields:** Ghost style. No background fill. Only a 1px bottom border using `outline`. On focus, the border transitions to Orange.
*   **Cards:** No borders, no shadows. Use a subtle background shift (`surface-container`). Images inside cards should have a `0.9` opacity, shifting to `1.0` on hover.
*   **Dividers:** Strictly forbidden. Use **48px / 64px / 96px** vertical white space intervals to denote content breaks.

---

## 6. Motion: High-End Entrance Animations
The "Kinetic Gallery" feels premium through deliberate, staggered motion.

### Text Entrance (The "Rise & Reveal")
*   **Mechanism:** Wrap lines or characters in a container with `overflow: hidden`.
*   **Animation:** TranslateY(100%) to TranslateY(0%).
*   **Easing:** `cubic-bezier(0.16, 1, 0.3, 1)` (The "Expo Out" curve). 
*   **Duration:** 800ms with a 50ms stagger per line.

### Page Transitions
Elements should not "fade in"; they should "materialize." Use a subtle scale-down from 1.02 to 1.0 combined with an opacity ramp.

---

## 7. Do's and Don'ts

### Do
*   **DO** use 0px border-radius everywhere. Sharp edges convey precision.
*   **DO** use pure #000000 for image backgrounds to create a "seamless" blend between media and UI.
*   **DO** leverage oversized typography as a graphic element.

### Don't
*   **DON'T** use grey text on a grey background. Maintain high contrast (White on Black) for body copy.
*   **DON'T** use rounded corners. It breaks the "Architectural" intent of the system.
*   **DON'T** use "Standard" easing (ease-in-out). It feels "web-standard." Use custom cubic beziers for a bespoke feel.

---
**Director's Note:** Every pixel must feel like it was placed by a curator. If a component feels "default," strip it back until only the typography and the color remains. The void is your most powerful tool.