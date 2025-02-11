## **3. Personalized Workout Plan Generator**  
Select their fitness goal, and the site generates a workout plan!  

# Personalized Workout Plan

Choose your goal and get a custom workout plan!  

<label for="goal">Select your goal:</label>
<select id="goal">
    <option value="muscle">Build Muscle</option>
    <option value="weight_loss">Lose Weight</option>
    <option value="endurance">Improve Endurance</option>
</select>
<button onclick="generateWorkout()">Get Workout Plan</button>
<p id="workoutPlan"></p>

<script>
function generateWorkout() {
    let goal = document.getElementById("goal").value;
    let workout = "";

    if (goal === "muscle") {
        workout = "🏋️‍♂️ Strength Workout: 3 sets of 8 reps (Squats, Deadlifts, Bench Press, Pull-ups).";
    } else if (goal === "weight_loss") {
        workout = "🔥 Fat Burn Workout: 30 mins HIIT (Jump Rope, Burpees, Mountain Climbers, Jump Squats).";
    } else if (goal === "endurance") {
        workout = "🏃‍♂️ Cardio Workout: 45 mins running or cycling + 15 mins bodyweight exercises.";
    }

    document.getElementById("workoutPlan").innerText = workout;
}
</script>