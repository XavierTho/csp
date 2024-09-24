---
layout: base
title: Home
description: Home Page
author: Xavier Thompson
hide: true
---

<style>
  body {
    font-family: 'Arial', sans-serif;
    background-color: #f0f0f5;
    color: #333;
    margin: 0;
    padding: 0;
  }

  .typewriter {
    font-size: 2rem;
    font-weight: bold;
    margin: 20% auto;
    width: fit-content;
    color: #0072ff;
    border-right: 2px solid #0072ff;
    white-space: nowrap;
    overflow: hidden;
    max-width: 80%; /* Handles overflow for longer text */
  }

  .blink-cursor {
    animation: blink 0.75s step-end infinite;
  }

  @keyframes blink {
    from, to {
      border-color: transparent;
    }
    50% {
      border-color: #0072ff;
    }
  }
</style>

<body>
  <div class="typewriter" aria-live="polite">
    <span id="typing-text"></span><span class="blink-cursor">|</span>
  </div>

  <script>
    const texts = [
      "Hello, my name is Xavier.",
      "Welcome to my website!",
    ];

    // Configuration settings
    let index = 0;
    let charIndex = 0;
    const typingSpeed = 100;  // Speed of typing (in ms)
    const deletingSpeed = 50; // Speed of deleting (in ms)
    const delayBetweenTexts = 2000; // Delay between deleting and typing next sentence (in ms)
    const delayBeforeDeleting = 1500; // Time before starting to delete the text (in ms)
    const initialDelay = 1000; // Initial delay before starting the typing effect (in ms)

    const typingTextElement = document.getElementById('typing-text');

    function typeText() {
      if (charIndex < texts[index].length) {
        typingTextElement.textContent += texts[index].charAt(charIndex);
        charIndex++;
        setTimeout(typeText, typingSpeed);
      } else {
        setTimeout(deleteText, delayBeforeDeleting); // Pause before deleting
      }
    }

    function deleteText() {
      if (charIndex > 0) {
        typingTextElement.textContent = texts[index].substring(0, charIndex - 1);
        charIndex--;
        setTimeout(deleteText, deletingSpeed);
      } else {
        index = (index + 1) % texts.length; // Move to the next sentence or loop back
        setTimeout(typeText, delayBetweenTexts); // Pause before typing new text
      }
    }

    // Start typing when the page loads
    window.onload = () => {
      setTimeout(typeText, initialDelay); // Optional: delay before starting the typing effect
    };
  </script>
</body>
