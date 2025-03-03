---
layout: post
title: MCQ (2) Review
toc: true
comments: true
---

<style>
    body {
        font-family: Arial, sans-serif;
        padding: 20px;
        background-color: #f9f9f9;
    }
    table {
        width: 100%;
        border-collapse: collapse;
        margin-top: 20px;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        border-radius: 8px;
        overflow: hidden;
        margin-left: auto; /* Center the table */
        margin-right: auto; /* Center the table */
    }
    th, td {
        padding: 16px;
        text-align: left;
        border-bottom: 1px solid #ddd;
        transition: background-color 0.3s;
        font-size: 18px; /* Increased font size */
        font-weight: bold; /* Increased font weight */
    }
    th {
        background-color: #4caf50;
        color: white;
        font-weight: bold;
    }
    tr:hover {
        background-color: #e0f7fa;
        cursor: pointer;
        transition: 0.3s;
    }
    .bar-container {
        width: 100%;
        background-color: #e0e0e0;
        border-radius: 8px;
        overflow: hidden;
        height: 24px;
        margin: 5px 0;
    }
    .bar {
        height: 24px;
        border-radius: 8px;
        transition: width 0.5s;
    }
    .gray-bar { background-color: #888; }
    .green-bar { background-color: #66bb6a; }
    .yellow-bar { background-color: #ffca28; }
    .modal {
        display: none;
        position: fixed;
        z-index: 10;
        left: 0;
        top: 0;
        width: 100%;
        height: 100%;
        overflow: auto;
        background-color: rgba(0,0,0,0.6);
        padding-top: 60px;
    }
    .modal-content {
        background-color: white;
        margin: 5% auto;
        padding: 30px;
        border-radius: 10px;
        width: 80%;
        max-width: 600px;
        box-shadow: 0 6px 12px rgba(0, 0, 0, 0.2);
    }
    .close {
        color: #333;
        float: right;
        font-size: 28px;
        font-weight: bold;
    }
    .close:hover, .close:focus {
        color: #000;
        text-decoration: none;
        cursor: pointer;
    }
    h2 {
        color: #333;
        margin-top: 0;
    }
    p {
        color: #555;
    }
</style>

<h2 style="text-align:center;">Performance Table</h2>
<table>
    <tr>
        <th>Topic</th>
        <th>Number of Questions</th>
        <th>Average Performance %</th>
    </tr>
    <tr onclick="showModal('Variables and Assignments')">
        <td>Variables and Assignments</td>
        <td>1</td>
        <td><div class='bar-container'><div class='bar yellow-bar' style='width: 0%'>0%</div></div></td>
    </tr>
    <tr onclick="showModal('Algorithmic Efficiency')">
        <td>Algorithmic Efficiency</td>
        <td>2</td>
        <td><div class='bar-container'><div class='bar yellow-bar' style='width: 0%'>0%</div></div></td>
    </tr>
    <tr onclick="showModal('Nested Conditionals')">
        <td>Nested Conditionals</td>
        <td>2</td>
        <td><div class='bar-container'><div class='bar green-bar' style='width: 50%'>50%</div></div></td>
    </tr>
    <tr onclick="showModal('Iteration')">
        <td>Iteration</td>
        <td>5</td>
        <td><div class='bar-container'><div class='bar green-bar' style='width: 60%'>60%</div></div></td>
    </tr>
</table>

<div id="modal" class="modal">
    <div class="modal-content">
        <span class="close" onclick="closeModal()">&times;</span>
        <h2 id="modalTitle">Topic Details</h2>
        <p id="modalContent">Here you can display specific questions and answers for the selected topic.</p>
    </div>
</div>

<script>
    function showModal(topic) {
        document.getElementById('modalTitle').innerText = topic;
        if (topic === 'Iteration') {
            document.getElementById('modalContent').innerHTML = "<p><strong>Question:</strong> Algorithm to move robot to goal</p><p><strong>Error:</strong> Incorrectly moves the robot off the grid.</p><p><strong>Correct Answer:</strong> The correct answer was Option C, as it used the correct movement pattern to navigate the robot to the gray square without exceeding boundaries.</p><p><strong>Concepts Involved:</strong> Iteration and conditional statements to control a loop until a goal is reached.</p><p><strong>Tip:</strong> Always visualize the steps of a loop in grid-based problems to avoid boundary errors.</p>";
        } else {
            document.getElementById('modalContent').innerText = "Questions and details will be displayed here for " + topic;
        }
        document.getElementById('modal').style.display = 'block';
    }

    function closeModal() {
        document.getElementById('modal').style.display = 'none';
    }

    window.onclick = function(event) {
        if (event.target == document.getElementById('modal')) {
            closeModal();
        }
    }
</script>
