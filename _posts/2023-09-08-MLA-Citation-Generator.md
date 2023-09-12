---
toc: true
comments: false
layout: post
title: MLA Citation Generator
description: This is a MLA Citation generator for books
type: hacks
courses: { compsci: {week: 3} }
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MLA Citation Generator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }

        #container {
            margin: 20px;
        }

        label {
            font-weight: bold;
        }

        #citation {
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div id="container">
        <h1>MLA Citation Generator</h1>
        <label for="bookTitle">Book Title:</label>
        <input type="text" id="bookTitle">
        <br>
        <label for="author">Author:</label>
        <input type="text" id="author">
        <br>
        <label for="publisher">Publisher:</label>
        <input type="text" id="publisher">
        <br>
        <label for="year">Publication Year:</label>
        <input type="text" id="year">
        <br>
        <button id="generateButton">Generate Citation</button>
        <div id="citation">
            <!-- The MLA citation will be displayed here -->
        </div>
    </div>

    <script>
        const generateButton = document.getElementById('generateButton');
        generateButton.addEventListener('click', generateMLACitation);

        function generateMLACitation() {
            const bookTitle = document.getElementById('bookTitle').value;
            const author = document.getElementById('author').value;
            const publisher = document.getElementById('publisher').value;
            const year = document.getElementById('year').value;

            const citation = `${author}. ${bookTitle}. ${publisher}, ${year}.`;

            const citationDiv = document.getElementById('citation');
            citationDiv.innerText = citation;
        }
    </script>
</body>
</html>
