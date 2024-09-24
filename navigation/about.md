---
layout: page
title: About
permalink: /about/
---

<style>
    .grid-container {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); 
        gap: 10px;
    }
    .grid-item {
        text-align: center;
    }
    .grid-item img {
        width: 100%;
        height: 100px;
        object-fit: contain;
    }
    .grid-item p {
        margin: 5px 0;
    }

    .image-gallery {
        display: flex;
        flex-wrap: nowrap;
        overflow-x: auto;
        gap: 10px;
    }

    .image-gallery img {
        max-height: 150px;
        object-fit: cover;
        border-radius: 5px;
    }
</style>

<div class="grid-container" id="grid_container"></div>

<script>
    var container = document.getElementById("grid_container");

    var http_source = "https://upload.wikimedia.org/wikipedia/commons/";
    var living_in_the_world = [
        {"flag": "0/0a/Flag_of_Jamaica.svg", "greeting": "Wah gwaan", "description": "Jamaica - my roots"},
        {"flag": "9/99/Flag_of_the_Philippines.svg", "greeting": "Kamusta", "description": "Philippines - cultural influence"},
        {"flag": "a/a4/Flag_of_the_United_States.svg", "greeting": "Hey", "description": "USA - where I currently thrive"},
    ];

    for (const location of living_in_the_world) {
        var gridItem = document.createElement("div");
        gridItem.className = "grid-item";
        var img = document.createElement("img");
        img.src = http_source + location.flag;
        img.alt = location.flag + " Flag";

        var description = document.createElement("p");
        description.textContent = location.description;

        var greeting = document.createElement("p");
        greeting.textContent = location.greeting;

        gridItem.appendChild(img);
        gridItem.appendChild(description);
        gridItem.appendChild(greeting);
        container.appendChild(gridItem);
    }
</script>

### My Journey

- 🌍 Lived in San Diego all my life
- 🎓 School journey: MRES, OVMS, & now DNHS
- 💻 Career aspirations: AGI, cybersecurity, etc.