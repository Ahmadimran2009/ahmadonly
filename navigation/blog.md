---
layout: page
title: Challenge
search_exclude: true
permalink: /blogs/


--- 

# Daily Fitness Challenge Generator

Click the button to get a random challenge for today!  


<button onclick="generateChallenge()">Get Your Challenge</button>
<p id="challenge"></p>

<script>
const challenges = [
    "Do 50 push-ups today!",
    "Run or walk 5,000 steps.",
    "Hold a plank for 1 minute.",
    "Do 30 bodyweight squats.",
    "Drink at least 2 liters of water.",
    "Try a new healthy recipe.",
    "Take the stairs instead of the elevator all day."
];

function generateChallenge() {
    let randomIndex = Math.floor(Math.random() * challenges.length);
    document.getElementById("challenge").innerText = challenges[randomIndex];
}
</script>
