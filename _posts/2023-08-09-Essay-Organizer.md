---
toc: true
comments: false
layout: post
title: Essay Organizer
description: This is a simple tool you can use to organize your essay or to put it together after writing the paragraphs
type: hacks
courses: { compsci: {week: 3} }
---

<html>
<head>
    <title>Essay Organizer</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f5f5f5;
        }

        #organizer-container {
            width: 600px;
            margin: 20px auto;
            padding: 20px;
            background-color: #fff;
            border: 1px solid #ccc;
            border-radius: 5px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);
        }

        label {
            font-weight: bold;
        }

        textarea {
            width: 100%;
            height: 150px;
            padding: 5px;
            margin-bottom: 10px;
        }

        button {
            background-color: #007bff;
            color: #fff;
            padding: 10px 20px;
            border: none;
            cursor: pointer;
        }

        #output {
            font-weight: bold;
            margin-top: 10px;
            text-align: left;
        }
    </style>
</head>
<body>
    <div id="organizer-container">
        <h1>Essay Organizer</h1>
        <label for="introduction">Introduction:</label>
        <textarea id="introduction" placeholder="Enter the introduction of your essay here"></textarea>
        <label for="body">Body:</label>
        <textarea id="body" placeholder="Enter the body of your essay here"></textarea>
        <label for="conclusion">Conclusion:</label>
        <textarea id="conclusion" placeholder="Enter the conclusion of your essay here"></textarea>
        <button onclick="generateEssay()">Generate Essay</button>
        <div id="output"></div>
    </div>

    <script>
        function generateEssay() {
            const introduction = document.getElementById('introduction').value;
            const body = document.getElementById('body').value;
            const conclusion = document.getElementById('conclusion').value;

            const essay = `
                Introduction:
                ${introduction}

                Body:
                ${body}

                Conclusion:
                ${conclusion}
            `;

            document.getElementById('output').textContent = essay;
        }
    </script>
</body>
</html>
