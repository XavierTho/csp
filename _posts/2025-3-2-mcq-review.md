---
layout: post
title: MCQ (2) Review - Performance Dashboard
toc: false
comments: true
---

<style>
    /* Base Styles */
    body {
        font-family: 'Arial', sans-serif;
        padding: 20px;
        background-color: #1e1e2f;
        color: #dcdcdc;
        transition: background-color 0.5s, color 0.5s;
    }
    h2, h3, p {
        text-align: center;
        margin: 10px 0;
        color: #dcdcdc;
    }
    
    /* Table Styles */
    table {
        width: 80%;
        margin: 20px auto;
        border-collapse: collapse;
        background-color: #2b2b3d;
        border-radius: 10px;
        overflow: hidden;
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.5);
    }
    th, td {
        padding: 20px;
        border-bottom: 1px solid #3a3a50;
        font-size: 18px;
        color: #dcdcdc;
        text-align: center;
        vertical-align: middle;
        transition: background-color 0.3s;
        position: relative;
    }
    th {
        background-color: #3a3a50;
        font-weight: normal;
    }
    tr:hover {
        background-color: #2e2e44;
        cursor: pointer;
        transition: 0.3s;
    }
    
    /* Circular Progress Styles */
    .progress-container {
        position: relative;
        width: 80px;
        height: 80px;
        margin: 0 auto;
    }
    .progress-circle {
        stroke: #007acc;
        stroke-width: 8;
        fill: transparent;
        stroke-linecap: round;
        animation: progress-animation 1.5s ease-out forwards;
    }
    .progress-bg {
        stroke: #3a3a50;
        stroke-width: 8;
        fill: transparent;
    }
    .progress-text {
        fill: #dcdcdc;
        font-size: 16px;
        font-weight: bold;
        text-anchor: middle;
        dominant-baseline: middle;
    }
    @keyframes progress-animation {
        from { stroke-dasharray: 0 100; }
        to { stroke-dasharray: var(--progress) 100; }
    }
    
    /* Modal Styles */
    .modal {
        display: none;
        position: fixed;
        z-index: 10;
        left: 0;
        top: 0;
        width: 100%;
        height: 100%;
        overflow: auto;
        background-color: rgba(0,0,0,0.7);
        padding-top: 60px;
    }
    .modal-content {
        background-color: #2b2b3d;
        margin: 5% auto;
        padding: 30px;
        border-radius: 10px;
        width: 80%;
        max-width: 600px;
        color: #dcdcdc;
        box-shadow: 0 8px 16px rgba(0, 0, 0, 0.5);
    }
    .close {
        color: #dcdcdc;
        float: right;
        font-size: 28px;
        font-weight: bold;
        cursor: pointer;
    }
    .close:hover {
        color: #007acc;
    }
    
    /* Tooltip Styles */
    .tooltip {
        position: absolute;
        bottom: 120%;
        left: 50%;
        transform: translateX(-50%);
        background-color: #333;
        color: #fff;
        padding: 5px 10px;
        border-radius: 5px;
        white-space: nowrap;
        font-size: 14px;
        visibility: hidden;
        opacity: 0;
        transition: opacity 0.2s, visibility 0.2s;
        pointer-events: none;
        z-index: 10;
    }
    td:hover .tooltip {
        visibility: visible;
        opacity: 1;
    }
    
    /* Progress Indicator */
    .overall-progress-container {
        width: 80%;
        margin: 20px auto;
        background-color: #3a3a50;
        border-radius: 8px;
        overflow: hidden;
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.5);
        position: relative;
    }
    .overall-progress-bar {
        height: 24px;
        background-color: #007acc;
        width: 0;
        transition: width 1s;
    }
    .progress-label {
        position: absolute;
        top: 0;
        left: 50%;
        transform: translateX(-50%);
        color: #fff;
        font-size: 16px;
        font-weight: bold;
        line-height: 24px;
    }
</style>

<h2>📊 MCQ (2) Performance Dashboard 📊</h2>

<!-- Overall Progress Bar with Explicit Score -->
<div class="overall-progress-container" title="Overall Performance: 56/67 (83.6%)">
    <div class="overall-progress-bar" style="width: 83.6%;"></div>
    <div class="progress-label">56/67 (83.6%)</div>
</div>

<table>
    <tr>
        <th>🧠 Topic</th>
        <th>📋 Number of Questions</th>
        <th>📈 Performance</th>
    </tr>
    
    <tr onclick="showModal('Variables and Assignments')">
        <td>Variables and Assignments</td>
        <td>1</td>
        <td>0%</td>
    </tr>
    
    <tr onclick="showModal('Algorithmic Efficiency')">
        <td>Algorithmic Efficiency</td>
        <td>2</td>
        <td>0%</td>
    </tr>
    
    <tr onclick="showModal('Nested Conditionals')">
        <td>Nested Conditionals</td>
        <td>2</td>
        <td>50%</td>
    </tr>
    
    <tr onclick="showModal('Iteration')">
        <td>Iteration</td>
        <td>5</td>
        <td>60%</td>
    </tr>
</table>

<div id="modal" class="modal">
    <div class="modal-content">
        <span class="close" onclick="closeModal()">&times;</span>
        <h2 id="modalTitle">Topic Details</h2>
        <p id="modalContent">Details will appear here.</p>
    </div>
</div>

<script>
    function showModal(topic) {
        document.getElementById('modalTitle').innerText = topic + " - Performance Analysis";
        document.getElementById('modalContent').innerHTML = `
            <p><strong>Opportunities for Improvement:</strong></p>
            <ul>
                <li>Review the fundamentals of ${topic}.</li>
                <li>Engage in targeted practice exercises.</li>
                <li>Apply knowledge through real-world scenarios.</li>
            </ul>
        `;
        document.getElementById('modal').style.display = 'block';
    }

    function closeModal() {
        document.getElementById('modal').style.display = 'none';
    }
</script>

<img src="{{site.baseurl}}/images/tri-two-final-blog/example-question.png">