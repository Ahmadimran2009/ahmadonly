---
layout: page
title:  🌍 Random Country Generator
permalink: /about/
---
 
 # 🌍 Random Country Generator
Click the button below to get a random country!

<button onclick="generateRandomCountry()">Generate Country</button>

<p id="countryDisplay">Click the button to see a country.</p>

<script>
  // Array of country names
  const countries = [
    'United States', 'Canada', 'Brazil', 'United Kingdom', 'Germany', 
    'France', 'Italy', 'Australia', 'Japan', 'China', 'Pakistan', 'South Africa', 
    'Mexico', 'Argentina', 'Spain', 'Russia', 'Egypt', 'Thailand', 'Turkey', 
    'New Zealand', 'South Korea','Ireland'
  ];

  function generateRandomCountry() {
    // Generate a random index
    const randomIndex = Math.floor(Math.random() * countries.length);
    // Display the random country
    document.getElementById('countryDisplay').innerText = countries[randomIndex];
  }
</script>



<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Quiz</title>
</head>
<body>
    <h1>mini Quiz💪🧠</h1>
    <form id="quizForm">
        <p>1. What is the capital of France?</p>
        <input type="radio" id="paris" name="q1" value="paris">
        <label for="paris">Paris</label><br>
        <input type="radio" id="rome" name="q1" value="rome">
        <label for="rome">Rome</label><br>
        <input type="radio" id="berlin" name="q1" value="berlin">
        <label for="berlin">Berlin</label><br>
        <button type="button" onclick="submitQuiz()">Submit</button>
    </form>

    <script>
        function submitQuiz() {
            const form = document.getElementById('quizForm');
            const answer = form.q1.value;
            if (answer === 'paris') {
                alert('Correct!');
            } else {
                alert('Try again.');
            }
        }
    </script>
</body>
</html>

