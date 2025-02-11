---
layout: page
title:  BMI Calculator
permalink: /about/
---
 
# BMI Calculator

Enter your weight and height to calculate your Body Mass Index (BMI).


<label for="weight">Weight (kg):</label>
<input type="number" id="weight" />
<label for="height">Height (cm):</label>
<input type="number" id="height" />
<button onclick="calculateBMI()">Calculate BMI</button>
<p id="bmiResult"></p>

<script>
function calculateBMI() {
    let weight = document.getElementById("weight").value;
    let height = document.getElementById("height").value / 100; // Convert cm to meters
    if (weight > 0 && height > 0) {
        let bmi = weight / (height * height);
        let category = "";

        if (bmi < 18.5) category = "Underweight";
        else if (bmi < 24.9) category = "Normal weight";
        else if (bmi < 29.9) category = "Overweight";
        else category = "Obese";

        document.getElementById("bmiResult").innerText = 
            `Your BMI: ${bmi.toFixed(2)} (${category})`;
    } else {
        document.getElementById("bmiResult").innerText = "Please enter valid values.";
    }
}
</script>

