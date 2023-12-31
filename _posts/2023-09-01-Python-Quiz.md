---
toc: true
comments: true
layout: post
title: Python Quiz
description: This is a simple python quiz which shows how to use python correctly.
type: hacks
courses: { compsci: {week: 3} }
---

``` python
class Question:
    def __init__(self, text, choices, correct_choice):
        self.text = text
        self.choices = choices
        self.correct_choice = correct_choice

    def is_correct(self, user_choice):
        return user_choice == self.correct_choice


class Quiz:
    def __init__(self, questions):
        self.questions = questions
        self.score = 0
        self.current_question_index = 0

    def get_current_question(self):
        return self.questions[self.current_question_index]

    def display_question(self):
        current_question = self.get_current_question()
        print(current_question.text)
        for index, choice in enumerate(current_question.choices, start=1):
            print(f"{index}. {choice}")
        user_choice = input("Enter the number of your choice: ")
        return int(user_choice)

    def play(self):
        for question in self.questions:
            user_choice = self.display_question()
            if question.is_correct(user_choice):
                print("Correct!\n")
                self.score += 1
            else:
                print("Incorrect.\n")
            self.current_question_index += 1
        print(f"You scored {self.score}/{len(self.questions)}")


# Create some quiz questions
questions = [
    Question("What is the capital of France?", ["Paris", "London", "Berlin"], 1),
    Question("Which planet is known as the Red Planet?", ["Mars", "Venus", "Jupiter"], 0),
    Question("What is the largest mammal on Earth?", ["Elephant", "Giraffe", "Blue Whale"], 2),
]

# Create a quiz with the questions
quiz = Quiz(questions)

# Start the quiz
print("Welcome to the General Knowledge Quiz!")
quiz.play()
```

    Welcome to the General Knowledge Quiz!
    What is the capital of France?
    1. Paris
    2. London
    3. Berlin
    Correct!

    Which planet is known as the Red Planet?
    1. Mars
    2. Venus
    3. Jupiter
    Incorrect.

    What is the largest mammal on Earth?
    1. Elephant
    2. Giraffe
    3. Blue Whale
    Incorrect.

    You scored 1/3

<script src="https://utteranc.es/client.js"
        repo="Week2CSP"
        issue-term="pathname"
        theme="github-light"
        crossorigin="anonymous"
        async>