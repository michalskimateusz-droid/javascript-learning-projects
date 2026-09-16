# 🎲 Pig Game

A browser-based two-player dice game created while developing my JavaScript fundamentals.

Compared with my earlier JavaScript learning projects, Pig Game introduced more complex application state and game logic. The project required tracking two players, switching the active player, updating multiple scores and controlling whether the game was still running.

Building the game step by step helped me better understand how several pieces of application state can work together to control the behavior of an interactive application.

## 🎮 How the Game Works

The game is played by two players taking turns.

During a turn:

- The active player rolls a dice.
- If the player rolls a number between 2 and 6, it is added to the current score.
- The player can continue rolling and accumulating points.
- The player can choose **Hold** to save the current score and pass the turn to the other player.
- If the player rolls a 1, the current score is lost and the turn immediately switches.
- The first player to reach the winning score wins the game.
- A new game can be started without reloading the page.

## 🛠️ Technologies

- JavaScript
- HTML5
- CSS3

## 🧠 What I Practiced

### Application State

One of the most important concepts in this project was managing several pieces of application state at the same time.

The game uses variables such as:

```javascript
let scores = [0, 0];
let currentScore = 0;
let activePlayer = 0;
let playing = true;
```

Each variable represents a different part of the current game state:

- `scores` stores the total score of both players,
- `currentScore` stores points accumulated during the current turn,
- `activePlayer` identifies whose turn it is,
- `playing` determines whether the game is still active.

This helped me understand that application behavior can be controlled by data representing its current state.

### Random Dice Generation

Each dice roll is generated using JavaScript.
To simulate a dice roll, I used `Math.random()` to generate a random value and scaled it to the six possible dice faces.

```javascript
const dice = Math.trunc(Math.random() * 6) + 1;
```

The generated value is then used both by the game logic and to display the corresponding dice image - for example, rolling `1` displays the image representing one pip.

### Dynamic DOM Updates

The interface changes dynamically depending on the current state of the game.

This includes:

- displaying the generated dice,
- updating the current score,
- updating each player's total score,
- visually indicating the active player,
- displaying the winning player,
- resetting the interface when a new game begins.

The project gave me more practice connecting JavaScript application logic with visible changes in the browser.

### Working with Arrays

Instead of storing each player's score in separate variables, the total scores are stored in an array:

```javascript
let scores = [0, 0];
```

The `activePlayer` value can then be used as an index:

```javascript
scores[activePlayer];
```

This made it possible to use the same game logic for both players rather than creating separate implementations for Player 1 and Player 2.

### Switching the Active Player

An important part of the game was implementing the turn-switching mechanism.

The active player can be changed using a conditional expression:

```javascript
activePlayer = activePlayer === 0 ? 1 : 0;
```

The first player is represented by index `0`, while the second player is represented by index `1`. This allows the active player to be switched by changing the index.

The switch also requires resetting the current score and updating the user interface.

As the project developed, this repeated behavior was extracted into a reusable function:

```javascript
const switchPlayer = function () {
  document.getElementById(`current--${activePlayer}`).textContent = 0;
  currentScore = 0;
  activePlayer = activePlayer === 0 ? 1 : 0;
  player0El.classList.toggle("player--active");
  player1El.classList.toggle("player--active");
};
```

This was another practical example of applying the DRY principle by moving repeated application logic into a single reusable function.

### Holding the Score

The **Hold** action introduced another important part of the game logic.

When the player decides to hold:

1. The current score is added to the active player's total score.
2. The total score is updated in the interface.
3. The game checks whether the player has reached the winning score.
4. If not, the turn switches to the other player.

This helped me work with several state changes triggered by a single user action.

### Controlling the Game State

The `playing` variable was introduced to prevent the game from continuing after a player had already won:

```javascript
let playing = true;
```

Event handlers execute the game logic only while:

```javascript
if (playing) {
  // game logic
}
```

After a player wins:

```javascript
playing = false;
```

This introduced me to using a boolean flag to control whether particular application behavior should still be available.

## 🔄 Game Initialization and Reset

As the project became more complex, resetting the game required restoring several values and UI elements.

The initialization logic was therefore extracted into an `initGame()` function.

Its responsibilities include:

- resetting both players' scores,
- resetting the current score,
- restoring Player 1 as the active player,
- setting `playing` back to `true`,
- hiding the dice,
- removing the winner state,
- restoring the correct active-player styling.

The same function can be used both when the application first loads and when the user starts a new game.

This showed me how initialization logic can be centralized instead of duplicating the same reset operations in multiple places.

## ♻️ Refactoring and Reusable Logic

Pig Game was another project where the implementation evolved during development.

Some behaviors initially existed directly inside event handlers and were later moved into reusable functions such as:

- `switchPlayer()`
- `initGame()`

This continued the refactoring concepts I had already encountered in my earlier JavaScript exercises.

It also helped me understand that as an application becomes more complex, separating responsibilities into functions makes the code easier to read, modify and maintain.

## 📈 Learning Process

The project was developed incrementally.

The learning process included:

1. Selecting the required DOM elements
2. Generating random dice rolls
3. Dynamically displaying dice images
4. Updating the current score
5. Tracking the active player
6. Storing player scores in an array
7. Switching turns between players
8. Implementing the Hold functionality
9. Detecting the winning condition
10. Controlling the running state of the game
11. Implementing a complete game reset
12. Refactoring repeated logic into reusable functions

Compared with my earlier JavaScript exercises, this project required me to think more about how multiple variables, events and UI elements interact as one application.

## 💡 Ideas for Future Development

While working on the project, I also wrote down ideas for extending the original game beyond the course exercise.

One concept was a **Russian Roulette-inspired game mode** based on randomized risk.

Possible extensions included:

- supporting more than two players,
- introducing a randomized elimination mechanic inspired by a revolver cylinder,
- rotating the virtual cylinder after each player's turn,
- preventing previously selected chamber positions from being selected again,
- tracking a high score,
- expanding the game rules beyond the original Pig Game implementation.

These ideas were not implemented in the current version and are documented here as possible directions for future development.

They represent some of my first attempts to think beyond the provided exercise and consider how an existing application could be extended with additional rules and state.

## 🕹️ Running the Project

This is where the fun starts!

No installation or additional dependencies are required. Just:

1. Clone or download the repository.
2. Open the `pig-game` directory.
3. Open `index.html` in a web browser.
4. Roll the dice and try your luck.

Just remember — sometimes holding the score is smarter than rolling one more time. 😄

## 📚 Project Origin

This project was originally created while completing a JavaScript course as part of my programming education.

The implementation follows the course exercise, while my personal learning notes documented how the application was developed step by step — from generating the first dice roll to managing players, scores, winning conditions and complete game initialization.

The ideas listed under **Future Development** came from my own notes and were concepts I considered while working through the project. They are not part of the current implementation.

I have included Pig Game in this repository because it represents another step in the development of my programming foundations and required more application-state management than my earlier JavaScript exercises.

---

Part of my [JavaScript Learning Projects](../README.md) portfolio.
