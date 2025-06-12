---
layout: post
title: Bitshift Review
toc: False
comments: True
---

## 🎮 What is Project BitShift?

**Project BitShift** is an interactive educational game built to make binary concepts *click*. Instead of lectures and worksheets, users enter a 3D world filled with logic puzzles, visualizations, and hands-on experimentation.

Whether you're a curious student or just want to understand the 1s and 0s that power computers, BitShift helps you learn through exploration—making computing concepts intuitive and fun.

## 🌟 My Role: Frontend Developer

As part of the BitShift development team, I focused on crafting the **frontend experience**, ensuring the user interface was not only functional but engaging, accessible, and immersive.

### 🛠️ Technologies & Tools Used

- **HTML/CSS/JavaScript**
- **Custom Modal and Carousel Systems**
- **Embedded YouTube Integration**
- **Interactive Binary Visualizer**
- **Dynamic UI Components (e.g., Tech & Item Dictionary, Control Panels)**

---

## 💡 Key Features I Built

### 🔁 Image Carousel + Modal Viewer

Implemented a horizontally sliding carousel with modal popups for each screenshot:

```js
// Center active slide and shift carousel
function updateSlides() {
  slides.forEach((slide, i) => {
    slide.classList.toggle('active', i === index);
  });
  dots.forEach((dot, i) => {
    dot.classList.toggle('active', i === index);
  });

  const offset = (index * -220) + (carousel.offsetWidth / 2 - 110);
  track.style.transform = `translateX(${offset}px)`;
}
```

---

### 🎮 Interactive Controls Panel

Displays all game control keys using styled `<kbd>` tags:

```html
<ul>
  <li><kbd>W</kbd> <kbd>A</kbd> <kbd>S</kbd> <kbd>D</kbd> — Move</li>
  <li><kbd>↑</kbd> <kbd>↓</kbd> <kbd>←</kbd> <kbd>→</kbd> — Look around</li>
  <li><kbd>Space</kbd> — Enter binary puzzle</li>
</ul>
```

---

### 🧩 In-Game Tech & Item Dictionary

Created a toggleable panel that displays item descriptions dynamically:

```js
function toggleItems() {
  const panel = document.getElementById("itemsIndex");
  const btn = document.querySelector(".toggle-items");

  const isOpen = panel.style.display === "block";
  panel.style.display = isOpen ? "none" : "block";
  btn.textContent = isOpen
    ? "Open Tech & Items Dictionary"
    : "Close Tech & Items Dictionary";
}
```

---

### 📹 Embedded Video Experience

Integrated a YouTube walkthrough inside a responsive container with custom styling:

```html
<iframe 
  src="https://www.youtube.com/embed/x7uzsDoNcd4"
  allowfullscreen
  style="position: absolute; width: 100%; height: 100%; border-radius: 12px;">
</iframe>
```

---

### 🔢 Binary Visualizer Page

Built a tool for converting and visualizing binary ↔ decimal in real time:

```js
function updateExplanation(dec) {
  const bin = dec.toString(2).padStart(8, "0");
  let mathExp = "";

  for (let i = 0; i < bin.length; i++) {
    if (bin[i] === "1") {
      mathExp += (mathExp ? " + " : "") + `1×${128 >> i}`;
    }
  }

  explanation.innerHTML = `<strong>${dec}</strong> in binary is <strong>${bin}</strong><br>It equals: ${mathExp}`;
}
```

---

## 🧩 Challenges Solved

- Built fluid, responsive layouts that worked across screen sizes  
- Balanced technical UI detail with accessibility and clarity  
- Optimized DOM interactions for fast, clean user feedback

## 📈 Impact

- Lowered the barrier for understanding binary by turning it into a game  
- Enhanced frontend interactivity and visual clarity  
- Brought abstract logic into physical spaces that users could explore

---

👉 **Check out the GitHub repo:** [Project BitShift on GitHub](https://github.com/frogpants/Project-Bitshift)
