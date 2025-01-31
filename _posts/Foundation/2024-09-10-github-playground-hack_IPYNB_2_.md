---
layout: post
title: Sprint 4 reflection
description: this is what I learned and did during Sprint 4
type: issues
comments: True
---
# Fridge API blog

The Fridge Feature helps users manage ingredients and discover recipes based on what they have on hand. Users can add ingredients (e.g., "tomato, mozzarella, basil") to their virtual fridge, which are stored and linked to their user ID for personalized use. Through various endpoints, users can add ingredients via a POST request, retrieve their stored ingredients with a GET request, or search for recipes that utilize their available items. This functionality simplifies meal planning and reduces waste by making the most of existing ingredients.

# Frontend Features

# Adding your ingredients
<script>
const addFridgeBtn = document.getElementById('addFridgeBtn');
const ingredientsInput = document.getElementById('ingredients');
const userIdInput = document.getElementById('user_id');
const fridgeList = document.getElementById('fridgeList');

const API_URL = "http://localhost:8887/fridge";

// Add ingredients to fridge
addFridgeBtn.addEventListener('click', async () => {
    try {
        const response = await fetch(API_URL, {
            method: 'POST', // Specifies a POST request
            headers: {
                'Content-Type': 'application/json', // Sets the content type as JSON
            },
            body: JSON.stringify({
                ingredients: ingredientsInput.value, // Ingredients input by user
                user_id: userIdInput.value,         // User ID input by user
            }),
        });

        if (!response.ok) {
            throw new Error(`HTTP error! Status: ${response.status}`);
        }

        const data = await response.json();
        alert('Ingredients added successfully');
        displayFridgeItems(userIdInput.value); // Refreshes the fridge list for the user
    } catch (error) {
        console.error('Error:', error);
        alert(`An error occurred: ${error.message}`);
    }
});
</script>
