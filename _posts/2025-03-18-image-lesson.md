---
layout: post
title: Color Codes, Images, Base64 Blog
toc: True
permalink: /image-lesson
comments: True
---

# Lesson: Color Codes, Images, and Base64

## Overview
- **Objective:** Learn how colors are represented, how digital images work, and how to embed images as Base64.
- **Who it’s for:** Anyone—even if you’ve never coded before.
- **How to use:** Read each section, follow examples, and work through the exercises.
- **Presentation tips:**
  - Keep your slides simple—one concept per slide.
  - Read the bullet points aloud; they guide you.
  - Point to code examples on the screen.
  - Pause for each exercise and invite participation.

---

## 1. Color Codes

### What Are Color Codes?
- Represent colors in computers and on the web.
- Essential for web design, digital art, UI layouts.

### Common Formats
- **Hex** (`#RRGGBB` or `#RRGGBBAA`):
  - Two hexadecimal digits for Red, Green, Blue (and optional Alpha).
  - Ranges from `00` to `FF` per channel.
- **RGB** (`rgb(R, G, B)`):
  - Decimal values 0–255 for each channel.
- **RGBA** (`rgba(R, G, B, A)`):
  - Adds an **alpha** (opacity) channel from 0 (transparent) to 1 (opaque).

### Key Examples
- **Red** → `#FF0000` → `rgb(255,0,0)` → `rgba(255,0,0,1)`
- **Blue** → `#0000FF` → `rgb(0,0,255)` → `rgba(0,0,255,0.3)`
- **Orange** → `#FF5733` → `rgb(255,87,51)` → `rgba(255,87,51,0.5)`

### ▶️ Exercise 1
1. Convert these hex codes to RGB & RGBA (A = 1):
   - `#1E90FF`
   - `#32CD32`
   - `#FFD700`
2. Write an **RGBA** for 50%-transparent teal (`rgb(0,128,128)`).

### Presenter Notes
- Define “hexadecimal” as base-16 numbering.
- Show how `FF` equals 255 in decimal.
- Emphasize that RGBA alpha is a fraction.
- Allow learners to shout out answers.

---

## 2. Digital Images

### What Is a Digital Image?
- A **grid** of tiny colored squares called **pixels**.
- Each pixel stores an RGB(A) value.

### Common File Formats
- **JPEG**
  - Use for photos.
  - Doesn’t support transparency.
  - Lossy compression → smaller files, some quality loss.
- **PNG**
  - Use for graphics, logos.
  - Supports transparency.
  - Lossless compression → larger but crisp.
- **GIF**
  - Use for simple animations.
  - Limited to 256 colors.
  - Supports transparency.
- **SVG**
  - Vector graphics (XML text).
  - Scales without losing quality.
  - No “pixels” — resolution independent.

### Raw Pixel Example
Suppose a 3×1 image:
```
[FF5733] [000000] [FFFFFF]
```
- Pixel 1 → orange
- Pixel 2 → black
- Pixel 3 → white

### ▶️ Exercise 2
1. **Design** a 2×2 icon:
   - Pick 4 colors, list each hex code.
2. **Calculate** storage for that 2×2 image at 24-bit color depth:
   - Bits per pixel × number of pixels → total bits.

### Presenter Notes
- Draw a simple 2×2 grid on a whiteboard.
- Explain “24-bit” → 8 bits × 3 channels.
- Walk through bit calculation step by step.

---

## 3. Base64 Encoding

### What Is Base64?
- A way to convert **binary data** into **plain text**.
- Uses only ASCII characters (`A–Z`, `a–z`, `0–9`, `+`, `/`, `=`).

### Why Base64?
- Embed images directly in **HTML**, **CSS**, **JSON**.
- Prevents corruption in text-based protocols.
- Avoids extra file requests in emails or small icons.

### Quick Conversion Example
1. Text `"Hi"` → bytes `[0x48, 0x69]`
2. Binary → `01001000 01101001`
3. Split into 6-bit chunks: `010010 000110 1001`
4. Map to Base64 chars → `"SGl="`

### Embedding in HTML
```html
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABQAAA...">
```

### ▶️ Exercise 3
1. Base64-encode the string:
   - `Cat`
2. Create a **1×1 red PNG**, convert it to Base64, and embed in `<img>` tag.

### Presenter Notes
- Show an online Base64 encoder demo.
- Explain padding with `=` characters.
- Highlight “data URI” format prefix.

---

## 4. Combining Color Codes & Base64

You can **overlay** a semi-transparent color on a Base64 image using CSS:
```css
.icon {
  background-image: url("data:image/png;base64,...");
  background-color: rgba(255,87,51,0.4);
  width: 100px;
  height: 100px;
}
```

### Why?
- Quick icon theming.
- No extra image files needed.

### Presenter Notes
- Demonstrate live by toggling alpha value.
- Show effect on different background colors.

---

## 5. AP CSP Practice Questions

<img src="{{site.baseurl}}/images/example-image-question.png">

### Presenter Notes
- Provide formula sheets for quick reference.
- Have calculators ready (or use on-screen).
- Walk through the first question in class.

---

## Summary & Key Takeaways

- **Color Codes:** Hex, RGB, RGBA → know formats and conversions.
- **Digital Images:** Pixel grids → file formats & compression trade-offs.
- **Base64:** Embed images as text → data URIs in web contexts.
- **Combining:** Use CSS to theme embedded images.
- **Practice:** Solidify with AP-style questions.

---

## Further Resources
- [MDN Web Docs – Base64](https://developer.mozilla.org/en-US/docs/Glossary/Base64)
- [W3Schools Color Picker](https://www.w3schools.com/colors/colors_picker.asp)
- [Base64 Image Encoder](https://www.base64-image.de/)
- [HTML `<img>` Tag Reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img)
- [CSS Colors Guide](https://developer.mozilla.org/en-US/docs/Web/CSS/color)

---


