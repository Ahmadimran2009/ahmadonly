---
layout: page
title: planner
permalink: /cookieclicker/
---
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Workout Planner</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            padding: 20px;
        }
        .container {
            background-color: #fff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            max-width: 400px;
            margin: auto;
        }
        h1 {
            text-align: center;
        }
        input, textarea, button {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            background-color: #28a745;
            color: white;
            cursor: pointer;
        }
        button:hover {
            background-color: #218838;
        }
        ul {
            list-style-type: none;
            padding: 0;
        }
        li {
            background: #e9ecef;
            margin: 5px 0;
            padding: 10px;
            border-radius: 5px;
        }
        .comment {
            font-style: italic;
            color: #555;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Workout Planner</h1>
        <input type="text" id="workout" placeholder="Workout Name">
        <input type="number" id="sets" placeholder="Sets">
        <input type="number" id="reps" placeholder="Reps">
        <textarea id="comments" placeholder="Add comments about the workout"></textarea>
        <button onclick="addWorkout()">Add Workout</button>
        <h2>Planned Workouts</h2>
        <ul id="workoutList"></ul>
    </div>
    <script>
        function addWorkout() {
            const workout = document.getElementById('workout').value;
            const sets = document.getElementById('sets').value;
            const reps = document.getElementById('reps').value;
            const comments = document.getElementById('comments').value;
            if (workout && sets && reps) {
                const li = document.createElement('li');
                li.innerHTML = `<strong>${workout}</strong> - ${sets} sets x ${reps} reps`;
                if (comments) {
                    const commentElement = document.createElement('p');
                    commentElement.className = 'comment';
                    commentElement.textContent = `Comment: ${comments}`;
                    li.appendChild(commentElement);
                }
                document.getElementById('workoutList').appendChild(li);
                document.getElementById('workout').value = '';
                document.getElementById('sets').value = '';
                document.getElementById('reps').value = '';
                document.getElementById('comments').value = '';
            } else {
                alert('Please fill out all fields except comments, which is optional.');
            }
        }
    </script>
</body>
</html>
