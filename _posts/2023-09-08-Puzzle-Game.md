---
toc: true
comments: true
layout: post
title: Puzzle Game
description: This is a simple number puzzle (get all 9 lined up)
type: hacks
courses: { compsci: {week: 3} }
---

<html>
<head>
    <title>Sliding Puzzle</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
        }

        .puzzle {
            display: grid;
            grid-template-columns: repeat(3, 100px);
            grid-gap: 5px;
            margin: 20px auto;
        }

        .tile {
            width: 100px;
            height: 100px;
            background-color: lightblue;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            font-weight: bold;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div class="puzzle" id="puzzle"></div>
    <button onclick="shufflePuzzle()">Shuffle Puzzle</button>

    <script>
        const puzzleSize = 3;
        const tileCount = puzzleSize * puzzleSize;
        const puzzle = document.getElementById('puzzle');
        let tiles = [];

        // Initialize the puzzle
        function initPuzzle() {
            tiles = [];
            puzzle.innerHTML = '';

            for (let i = 1; i < tileCount; i++) {
                const tile = document.createElement('div');
                tile.className = 'tile';
                tile.textContent = i;
                tile.dataset.value = i;
                tile.addEventListener('click', () => moveTile(tile));
                tiles.push(tile);
            }

            // Add an empty tile
            const emptyTile = document.createElement('div');
            emptyTile.className = 'tile empty';
            tiles.push(emptyTile);

            tiles = shuffleArray(tiles);
            tiles.forEach(tile => puzzle.appendChild(tile));
        }

        // Shuffle the puzzle
        function shuffleArray(array) {
            const shuffledArray = [...array];
            for (let i = shuffledArray.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [shuffledArray[i], shuffledArray[j]] = [shuffledArray[j], shuffledArray[i]];
            }
            return shuffledArray;
        }

        // Move a tile
        function moveTile(tile) {
            const emptyTileIndex = tiles.findIndex(t => t.classList.contains('empty'));
            const tileIndex = tiles.indexOf(tile);

            if (Math.abs(emptyTileIndex - tileIndex) === 1 || Math.abs(emptyTileIndex - tileIndex) === puzzleSize) {
                // Swap the tiles
                [tiles[emptyTileIndex], tiles[tileIndex]] = [tiles[tileIndex], tiles[emptyTileIndex]];
                tiles.forEach((t, index) => t.style.order = index + 1);
            }

            if (isSolved()) {
                alert('Congratulations! You solved the puzzle!');
            }
        }

        // Check if the puzzle is solved
        function isSolved() {
            return tiles.every((tile, index) => (tile.dataset.value ? tile.dataset.value : '') === (index + 1).toString());
        }

        // Shuffle the puzzle and initialize
        function shufflePuzzle() {
            initPuzzle();
        }

        // Initialize the puzzle on page load
        window.addEventListener('load', initPuzzle);
    </script>
</body>
</html>
