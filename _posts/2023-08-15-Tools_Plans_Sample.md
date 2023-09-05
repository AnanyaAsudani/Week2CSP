---
toc: true
comments: false
layout: post
title: Daily Plan Sample
description: Example Blog!!!  This shows planning and notes from hacks.
type: plans
courses: { compsci: {week: 0} }
---

### PBL Unit 1 / Week 0
Learning outcome.  Installing Tools and showing usage of VSCode.
- Wednesday - Pick pair share partner, Pick crossover pair, Establish team of four.  Spend some time talking and getting to know each other, particularly with Computer Science experience and goals.  You should be matched with someone that has similar experience.
- Thursday - Setup Tools on laptop and/or Cloud Computer.
- Friday - Review and test as a Pair. Spend 25 minutes at one keyboard then switch for next 25 minutes.

<!DOCTYPE html>
<html>
<head>
  <title>Wordle Game</title>
</head>
<body>
  <h1>Wordle Game</h1>
  <div>
    <label for="guessInput">Enter your guess:</label>
    <input type="text" id="guessInput" />
    <button id="submitGuess">Submit</button>
  </div>
  <div id="feedback"></div>

  <script>
    const targetWord = "apple"; // Change this to the actual target word
    let attempts = 0;

    document.getElementById("submitGuess").addEventListener("click", checkGuess);

    function checkGuess() {
      const guessInput = document.getElementById("guessInput");
      const guess = guessInput.value.toLowerCase();

      if (guess.length !== targetWord.length) {
        displayFeedback("Guess must be " + targetWord.length + " letters long.");
        return;
      }

      attempts++;

      if (guess === targetWord) {
        displayFeedback(`Congratulations! You guessed the word "${targetWord}" in ${attempts} attempts.`);
      } else {
        displayFeedback(getFeedbackForGuess(guess));
      }
    }

    function getFeedbackForGuess(guess) {
      let feedback = "";

      for (let i = 0; i < guess.length; i++) {
        if (guess[i] === targetWord[i]) {
          feedback += guess[i].toUpperCase();
        } else if (targetWord.includes(guess[i])) {
          feedback += guess[i];
        } else {
          feedback += "-";
        }
      }

      return feedback;
    }

    function displayFeedback(message) {
      const feedbackElement = document.getElementById("feedback");
      feedbackElement.textContent = message;
    }
  </script>
</body>
</html>
