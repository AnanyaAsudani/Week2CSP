---
toc: true
comments: false
layout: post
title: Tic Tac Toe
description: My version of Tic Tac Toe
type: hacks
courses: { compsci: {week: 2} }
---

<html>
<head>
  <style>
    .board {
      display: grid;
      grid-template-columns: repeat(3, 100px);
      grid-gap: 2px;
    }
    .cell {
      width: 100px;
      height: 100px;
      font-size: 2em;
      text-align: center;
      vertical-align: middle;
      border: 1px solid black;
    }
  </style>
</head>
<body>
<div class="board" id="board">
  <div class="cell" onclick="makeMove(0, 0)"></div>
  <div class="cell" onclick="makeMove(0, 1)"></div>
  <div class="cell" onclick="makeMove(0, 2)"></div>
  <div class="cell" onclick="makeMove(1, 0)"></div>
  <div class="cell" onclick="makeMove(1, 1)"></div>
  <div class="cell" onclick="makeMove(1, 2)"></div>
  <div class="cell" onclick="makeMove(2, 0)"></div>
  <div class="cell" onclick="makeMove(2, 1)"></div>
  <div class="cell" onclick="makeMove(2, 2)"></div>
</div>
<script>
  const board = [
    ['', '', ''],
    ['', '', ''],
    ['', '', '']
  ];
  let currentPlayer = 'X';
  function makeMove(row, col) {
    const cell = document.getElementById('board').children[row * 3 + col];
    if (board[row][col] === '') {
      cell.innerText = currentPlayer;
      board[row][col] = currentPlayer;
      if (checkWinner(currentPlayer)) {
        alert(`Player ${currentPlayer} wins!`);
        resetBoard();
      } else {
        currentPlayer = (currentPlayer === 'X') ? 'O' : 'X';
      }
    } else {
      alert('Invalid move. Cell is already occupied.');
    }
  }
  function checkWinner(player) {
    // Check rows, columns, and diagonals
    for (let i = 0; i < 3; i++) {
      if (
        (board[i][0] === player && board[i][1] === player && board[i][2] === player) ||
        (board[0][i] === player && board[1][i] === player && board[2][i] === player)
      ) {
        return true;
      }
    }
    if (
      (board[0][0] === player && board[1][1] === player && board[2][2] === player) ||
      (board[0][2] === player && board[1][1] === player && board[2][0] === player)
    ) {
      return true;
    }
    return false;
  }
  function resetBoard() {
    for (let row = 0; row < 3; row++) {
      for (let col = 0; col < 3; col++) {
        board[row][col] = '';
        document.getElementById('board').children[row * 3 + col].innerText = '';
      }
    }
    currentPlayer = 'X';
  }
</script>
</body>
</html>