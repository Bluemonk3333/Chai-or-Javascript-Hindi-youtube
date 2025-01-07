# Chai-or-Javascript-Hindi-youtube
A code repo for javascript series  at chai or code youtube channel

# Project 1 Solution code

---

## Background Changer using html, css & javascript

[Click here](https://google.com)

---

# Solution Code

## project 1

```javascript
console.log("white-wolf");
// code start from here
const buttons = document.querySelectorAll(".button");
const body = document.querySelector("body");

buttons.forEach((btn) => {
  console.log(btn);
  btn.addEventListener("click", (e) => {
    console.log(e);
    console.log(e.target);
    switch (e.target.id) {
      case "grey":
        body.style.backgroundColor = e.target.id;
        break;
      case "orangered":
        body.style.backgroundColor = e.target.id;
        break;
      case "blue":
        body.style.backgroundColor = e.target.id;
        break;
      case "yellow":
        body.style.backgroundColor = e.target.id;
        break;
    }
  });
});
```

## Project 2

```javascript
const form = document.querySelector("form");
const under = document.querySelector(".under");
const normal = document.querySelector(".normal");
const over = document.querySelector(".over");

form.addEventListener("submit", (e) => {
  e.preventDefault();
  under.style.color = "";
  normal.style.color = "";
  over.style.color = "";
  const height = parseInt(document.querySelector("#height").value);
  const weight = parseInt(document.querySelector("#weight").value);
  const result = document.querySelector("#results");

  if (height === "" || height < 0 || isNaN(height)) {
    result.innerHTML = `Please! Enter a valid height... ${height}`;
  } else if (weight === "" || weight < 0 || isNaN(weight)) {
    result.innerHTML = `Please! Enter a valid weight... ${weight}`;
  } else {
    const bmi = (weight / ((height * height) / 10000)).toFixed(2);
    if (bmi <= 18.6) {
      under.style.color = "orange";
      result.innerHTML = `<span>Under Weight</span><br><span>BMI is: ${bmi}</span>`;
    } else if (bmi > 18.6 && bmi <= 24.9) {
      normal.style.color = "green";
      result.innerHTML = `<span>Normal Range</span><br><span>BMI is: ${bmi}</span>`;
    } else {
      over.style.color = "red";
      result.innerHTML = `<span>Over Weight</span><br><span>BMI is: ${bmi}</span>`;
    }
  }
});
```

## Project 3

```javascript
const clock = document.querySelector("#clock");

setInterval(function () {
  let date = new Date();
  clock.innerHTML = date.toLocaleTimeString();
}, 1000);
```

## Project 4

```javascript
let randomNumber = parseInt(Math.random() * 100 + 1);

const submit = document.querySelector("#subt");
const userInput = document.querySelector("#guessField");
const guessSlot = document.querySelector(".guesses");
const lastResult = document.querySelector(".lastResult");
const lowOrHi = document.querySelector(".lowOrHi");
const startOver = document.querySelector(".resultParas");

const p = document.createElement("p");

let prevGuess = [];
let numOfGuess = 1;
let playGame = true;

if (playGame) {
  submit.addEventListener("click", function (e) {
    e.preventDefault();
    const guess = parseInt(userInput.value);
    validateGuess(guess);
  });
}

const validateGuess = (guess) => {
  if (guess < 1 || guess > 100 || isNaN(guess)) {
    alert("Please! Enter a valid number, between 1 to 100...");
  } else {
    prevGuess.push(guess);
    if (numOfGuess > 10) {
      displayGuess(guess);
      displayMessage(`Game Over! Random number was ${randomNumber}`);
      endGame();
    } else {
      displayGuess(guess);
      checkGuess(guess);
    }
  }
};

const checkGuess = (guess) => {
  if (guess === randomNumber) {
    setInterval(() => {
      displayMessage(`'You guesses it right!'`);
    }, 3000);
    setInterval(() => {
      document.body.innerHTML = `<h1> 🥇 You Win! 🥇 </h1><h2>Game Over! The number was ${randomNumber}</h2>`;
    }, 5000);
    endGame();
  } else if (guess < randomNumber) {
    displayMessage(`Number is too low!`);
  } else if (guess > randomNumber) {
    displayMessage(`Number is too high!`);
  }
};

const displayGuess = (guess) => {
  userInput.value = "";
  guessSlot.innerHTML += `${guess} `;
  numOfGuess++;
  lastResult.innerHTML = `${11 - numOfGuess}`;
};

const displayMessage = (message) => {
  lowOrHi.innerHTML = `<h2>${message}</h2>`;
};

const newGame = () => {
  const newGameButton = document.querySelector("#newGame");
  newGameButton.addEventListener("click", function (e) {
    randomNumber = parseInt(Math.random() * 10 + 1);
    prevGuess = [];
    numOfGuess = 1;
    guessSlot.innerHTML = "";
    lastResult.innerHTML = `${11 - numOfGuess}`;
    userInput.removeAttribute("disabled");
    startOver.removeChild(p);
    displayMessage("");
    playGame = true;
  });
};

const endGame = () => {
  userInput.value = "";
  userInput.setAttribute("disabled", "");
  p.classList.add("button");
  p.innerHTML = `<h2 id='newGame'>Start new game</h2>`;
  p.style.textAlign = "center";
  p.style.cursor = "pointer";
  startOver.appendChild(p);
  playGame = false;
  newGame();
};
```

