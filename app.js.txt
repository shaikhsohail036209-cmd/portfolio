const typingTexts = [
"Web Developer",
"Python Programmer",
"Computer Science Student",
"Future Software Engineer"
];

let textIndex = 0;
let charIndex = 0;
let deleting = false;

const typingElement = document.getElementById("typing");

function typeEffect() {

if (!typingElement) return;

const currentText = typingTexts[textIndex];

if (!deleting) {

typingElement.textContent =
currentText.substring(0, charIndex + 1);

charIndex++;

if (charIndex === currentText.length) {

deleting = true;

setTimeout(typeEffect, 1500);

return;
}

} else {

typingElement.textContent =
currentText.substring(0, charIndex - 1);

charIndex--;

if (charIndex === 0) {

deleting = false;

textIndex++;

if (textIndex >= typingTexts.length) {
textIndex = 0;
}

}

}

setTimeout(typeEffect, deleting ? 60 : 100);
}

typeEffect();

/* Dark Light Mode */

const themeBtn =
document.getElementById("themeToggle");

if (themeBtn) {

themeBtn.addEventListener("click", () => {

document.body.classList.toggle("light-mode");

const icon =
themeBtn.querySelector("i");

if (
document.body.classList.contains("light-mode")
) {

icon.classList.remove("bi-moon-stars");
icon.classList.add("bi-sun");

} else {

icon.classList.remove("bi-sun");
icon.classList.add("bi-moon-stars");

}

});

}

/* Scroll Animation */

const revealElements =
document.querySelectorAll(
".glass-card,.project-card"
);

function revealOnScroll() {

revealElements.forEach(element => {

const position =
element.getBoundingClientRect().top;

const windowHeight =
window.innerHeight;

if (position < windowHeight - 100) {

element.style.opacity = "1";
element.style.transform =
"translateY(0)";

}

});

}

revealElements.forEach(element => {

element.style.opacity = "0";

element.style.transform =
"translateY(40px)";

element.style.transition =
"all 0.8s ease";

});

window.addEventListener(
"scroll",
revealOnScroll
);

revealOnScroll();

/* Active Navbar Link */

const sections =
document.querySelectorAll("section");

const navLinks =
document.querySelectorAll(".nav-link");

window.addEventListener("scroll", () => {

let current = "";

sections.forEach(section => {

const sectionTop =
section.offsetTop - 150;

if (
window.scrollY >= sectionTop
) {
current = section.getAttribute("id");
}

});

navLinks.forEach(link => {

link.classList.remove("active");

if (
link.getAttribute("href") ===
"#" + current
) {

link.classList.add("active");

}

});

});

console.log(
"Advanced Portfolio Loaded Successfully"
);
