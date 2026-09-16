# 🪟 Modal Window

A small browser-based user interface project created while learning JavaScript DOM manipulation and event handling.

The application demonstrates how modal windows can be opened and closed in response to different user interactions. Although the project itself is relatively simple, it introduced several important concepts related to selecting multiple DOM elements, manipulating CSS classes, handling different types of events and reusing application logic.

## 🎮 Features

- Multiple buttons capable of opening the modal window
- Modal visibility controlled dynamically with JavaScript
- Background overlay displayed while the modal is open
- Closing the modal using the close button
- Closing the modal by clicking the overlay
- Closing the modal using the `Escape` key

## 🛠️ Technologies

- JavaScript
- HTML5
- CSS3

## 🧠 What I Practiced

### Selecting Multiple DOM Elements

One of the first concepts explored in this project was the difference between:

`document.querySelector()`

and:

`document.querySelectorAll()`

The interface contains multiple buttons using the same `.show-modal` class.

While `querySelector()` returns the first matching element, `querySelectorAll()` allowed me to work with all matching buttons as a `NodeList`.

To select all buttons that allow the user to open the modal window, I used the `querySelectorAll()` method and passed the `.show-modal` CSS class as an argument.

```javascript
const btnsShowModal = document.querySelectorAll(".show-modal");
```

Then, I iterated over the collection to attach event listeners to each button:

```javascript
for (let i = 0; i < btnsShowModal.length; i++) {
  btnsShowModal[i].addEventListener("click", function () {
    // Open modal
  });
}
```

This helped me understand how the same application behavior can be applied to multiple elements in the user interface.

### CSS Class Manipulation

Instead of directly changing individual CSS properties, the application controls the visibility of the modal and overlay by adding and removing the `hidden` class.

To show modal:

```javascript
modal.classList.remove("hidden");
overlay.classList.remove("hidden");
```

Removing the `hidden` class also displays the overlay, creating a blurred background behind the modal.

To close the modal, I simply added the `hidden` class again:

```javascript
modal.classList.add("hidden");
overlay.classList.add("hidden");
```

CSS class manipulation introduced me to using JavaScript together with existing CSS classes to control the state of interface elements.

### Event Handling

The project uses several user interactions to trigger application behavior.

The modal can be closed by:

- clicking the close button,
- clicking the background overlay,
- pressing the `Escape` key.

This helped me understand that the same application action can be triggered by different events and interface elements.

### Reusing Functions

Initially, closing the modal could require repeating the same operations in multiple event handlers.

Instead, the closing logic was extracted into a reusable function:

```javascript
const closeModalFunction = function () {
  modal.classList.add("hidden");
  overlay.classList.add("hidden");
};
```

The same function can then be passed to multiple event listeners:

```javascript
btnCloseModal.addEventListener("click", closeModalFunction);
overlay.addEventListener("click", closeModalFunction);
```

This was another practical example of reducing duplicated logic (DRY principle) and making application behavior easier to maintain.

### Keyboard Events

The final stage of the project introduced keyboard interaction.

I used a `keydown` event listener attached to the document:

```javascript
document.addEventListener("keydown", function (event) {
  if (event.key === "Escape" && !modal.classList.contains("hidden")) {
    closeModalFunction();
  }
});
```

This introduced me to the event object and the `event.key` property, which can be used to identify which keyboard key triggered an event.

The additional condition:

```javascript
!modal.classList.contains("hidden");
```

ensures that the close action is executed only when the modal is currently visible.

## 📈 Learning Process

The project was developed incrementally while introducing new DOM and event-handling concepts.

The learning process included:

1. Selecting individual DOM elements
2. Selecting multiple elements with `querySelectorAll()`
3. Working with a `NodeList`
4. Attaching event listeners to multiple buttons
5. Manipulating CSS classes with `classList`
6. Extracting repeated behavior into a reusable function
7. Handling keyboard events
8. Working with the event object and `event.key`
9. Combining multiple conditions to control application behavior

The project helped me better understand how JavaScript can respond to different forms of user interaction while keeping the underlying interface logic reusable.

## 🕹️ Running the Project

This is where the fun starts!

No installation or additional dependencies are required. Just:

1. Clone or download the repository.
2. Open the `modal-window` directory.
3. Open `index.html` in a web browser.
4. Open and close the modal using the available interactions.

Try the buttons, overlay and `Escape` key.

## 📚 Project Origin

This project was originally created while completing a JavaScript course as part of my programming education.

The implementation follows the course exercise, while my personal learning notes documented the concepts introduced at each stage, including DOM selection, CSS class manipulation, reusable functions and keyboard event handling.

I have included the project in this repository to document the development of my JavaScript fundamentals and the programming concepts that later became useful in my development toward test automation.

---

Part of my [JavaScript Learning Projects](../README.md) portfolio.
