# 🎯 Guess My Number

A simple browser-based guessing game created while learning JavaScript fundamentals and DOM manipulation.

The player tries to guess a randomly generated number between 1 and 20. Each incorrect guess reduces the score, while the application provides feedback indicating whether the submitted number is too high or too low.

The project was developed step by step as part of my JavaScript learning process and helped me understand how JavaScript can control application logic and interact with a browser-based user interface.

## 🎮 Features

- Random number generation between 1 and 20
- User input validation
- Feedback for incorrect guesses
- "Too high" and "Too low" hints
- Score tracking
- High score tracking
- Visual feedback after winning
- Game reset without reloading the page

## 🛠️ Technologies

- JavaScript
- HTML5
- CSS3

## 🧠 What I Practiced

### DOM Manipulation:

One of the main goals of this project was learning how JavaScript communicates with elements displayed in the browser.

I practiced selecting elements using:

- document.querySelector();
  and also reading or modifying properties such as:
- .textContent
- .value
- .style

This helped me understand the connection between JavaScript application logic and the user interface.

### Event Handling:

The game introduced me to event-driven application behavior using:
.addEventListener()
The application reacts to user actions such as checking a number or starting a new game.

### Application Logic:

I implemented conditional logic responsible for comparing the player's guess with the generated secret number.

Depending on the result, the application:

- informs the player that the number is too high,
- informs the player that the number is too low,
- detects the correct answer,
- decreases the current score,
- or ends the game when the score reaches zero.

### Application State:

The game uses variables to maintain its current state, including:

- secretNumber
- score
- highScore

This was one of my first practical examples of understanding that application data needs to persist and change as the user interacts with the interface.

### Resetting the Game:

An additional part of the exercise was implementing the "Again!" functionality.

Instead of refreshing the browser, the application restores the initial game state by:

- generating a new secret number,
- resetting the score,
- clearing the input field,
- restoring the initial message,
- restoring the original UI styling.

The high score remains available between rounds.

### High Score:

The project was later extended with high score functionality.

After a successful guess, the current score is compared with the stored high score. The high score is updated only when the player achieves a better result.

This introduced me to maintaining values across multiple rounds of the same application session.

### Refactoring and the DRY Principle:

Robert C. Martin once said "Every piece of knowledge must have a single, unambiguous, authoritative representation within a system.". Following that particular good practice, all the code which I wrote and will write is based on DRY principle.
Regarding the above, important part of the project was revisiting the working implementation and identifying duplicated code.
The original version contained separate logic for guesses that were too high and too low, even though most of the behavior was identical.
This logic was simplified using conditional expressions, and repeated DOM manipulation was extracted into a reusable function:
"
const displayMessage = function (message) {
document.querySelector('.message').textContent = message;
};
"
This was an early practical introduction to the DRY (Don't Repeat Yourself) principle and showed me that working code can still be improved for readability and maintainability.

### Learning Process:

This project was built incrementally rather than as a finished solution from the beginning.

The learning process included:

- Selecting and reading DOM elements
- Modifying interface content
- Handling button click events
- Reading and converting user input
- Implementing the core game logic
- Managing score and game state
- Implementing game reset functionality
- Adding a high score
- Refactoring duplicated code

Keeping notes during development helped me understand not only what particular JavaScript features do, but also why and where they can be useful.

## 🕹️ Running the Project:

This is where the fun starts!

No installation or additional dependencies are required. Just:

1. Clone or download the repository.
2. Open the guess-my-number directory.
3. Open index.html in a web browser.
4. Start guessing!

## 📚 Project Origin:

This project was originally created while completing a JavaScript course as part of my programming education.

The implementation follows the course exercise, while my personal learning notes documented the development process, concepts introduced at each stage, and later code refactoring.

I have included the project in this repository to document the development of my programming foundations and the path that later supported my transition toward test automation.

Part of my "JavaScript Learning Projects portfolio".
