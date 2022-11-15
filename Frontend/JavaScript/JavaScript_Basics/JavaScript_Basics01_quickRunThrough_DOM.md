# JavaScript Basics

JavaScript is a programming language that makes your website more interactive.

- Add this to your index.html file, just before the body tag.."<script src="scripts/main.js"></script>" add defer keyword to make sure the script is loading in the background while the DOM is building.Scripts with defer never block the page.
  Scripts with defer always execute when the DOM is ready (but before DOMContentLoaded event).
  Create a folder name scripts and a file named main.js in it, and implement any javascript and it will render bc because of the script link.

- Variables are containers that store values.

- An Array is a structure that allows you to store multiple values in a single reference.

- An Object can be anything. Everything in JavaScript is an object and can be stored in a variable. Keep this in mind as you learn.
  e.glet myVariable = document.querySelector('h1');

- A Function is a way to package functionality that you wish to reuse...

  - We can Create anonymous functions without names.. solely using parenthesis...

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

- If it is, the code changes the src value to the path of the second image, forcing the other image to be loaded inside the imgs element.
- If it isn't (meaning it must already have changed), the src value swaps back to the original image path, to the original state.

### Other key takeaways from the DOM

- The e.preventDefault() method cancels the event if it is cancelable, meaning that the default action that belongs to the event will not occur.

- If you need to get access to an element which doesn't have an ID, you can use querySelector() to find the element using any selector.

- document.createElement('div') to create a element
- document.getElementById to get the element with this specific ID
- document.querySelector(""), if the element you want doesnt have an id
- document.getElementsByTagName, if you want to get an element through its tag name( h1,
  span').
- myImage.getAttribute('src") if you want to get the attribute value src of an element referenced by myImage.
- bookDiv.classList.add('add'), if you want to add a class(add) to the div(bookdiv) **you can declare the class and its properties in a stylesheet, and add them to any element.**
- bookDiv.appendChild('insert element'); if you want to add a child into the parent (bookdiv) element
- removeBtn.textContent = 'Remove'; if you want to add text content to the (removeBtn) element
  -bookDiv.innerHtml = "iiii" ... innerHtml effects the text only , while textContent can effect the styling aswell

copied from W3Schools

The innerHTML property returns:
The text content of the element, including all spacing and inner HTML tags.
The innerText property returns:
Just the text content of the element and all its children, without CSS hidden text spacing and tags, except <script> and <style> elements.
The textContent property returns:
The text content of the element and all descendaces, with spacing and CSS hidden text, but without tags.
