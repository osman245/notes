# JavaScript Basics

JavaScript is a programming language that makes your website more interactive.

- Add this to your index.html file, just before the body tag.."<script src="scripts/main.js"></script>"
  Create a folder name scripts and a file named main.js in it, and implement any javascript and it will render bc because of the script link.

- Variables are containers that store values.

- An Array is a structure that allows you to store multiple values in a single reference.

- An Object can be anything. Everything in JavaScript is an object and can be stored in a variable. Keep this in mind as you learn.
  e.glet myVariable = document.querySelector('h1');

- A Function is a way to package functionality that you wish to reuse...
  We can Create anonymous functions

- An Event is a code structure that listens for activity and runs code in reponse to that activity
  e.g) document.querySelector("html").addEventListener("click", function () {
  alert("Ouch! Stop poking me!");
  });

### A Breakdown of some JavaScript Code....

`
const myImage = document.querySelector("img");

myImage.onclick = () => {
const mySrc = myImage.getAttribute("src");
if (mySrc === "images/firefox-icon.png") {
myImage.setAttribute("src", "images/firefox2.png");
} else {
myImage.setAttribute("src", "images/firefox-icon.png");
}
};
`

- We store the img element in the myImage variable.
- We initialize the event handler property of myImage variable to an anonymous function
  so that everytime its clicked.
- The code retrieves the value of the image's src attribute.
- The code uses a conditional to check if the src value is equal to the path of the original image:

- If it is, the code changes the src value to the path of the second image, forcing the other image to be loaded inside the <img> element.
- If it isn't (meaning it must already have changed), the src value swaps back to the original image path, to the original state.
