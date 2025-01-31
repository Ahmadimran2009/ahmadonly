---
layout: page
title: 3.6 and 3.7 homework
permalink: /homework/
---
# Homework for 3.6 and 3.7
I made a statement that represents age and it will show if you are a child, teeneager or adult.
# Function to classify age group
def classify_age(age):
    if 3 <= age <= 12:
        return "Child"
    elif 13 <= age <= 17:
        return "Teenager"
    else:
        return "Adult"

# Main program
try:
    # Get user input
    age_input = int(input("Please enter your age: "))
    # Classify and print result
    age_group = classify_age(age_input)
    print(f"You are classified as: {age_group}")
except ValueError:
    print("Please enter a valid number for age.")
