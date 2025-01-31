---
layout: base
title: home page 😎
description: Home page
hide: true
image: /images/mario_animation.png
---

<img src="images/PHOTO-2024-09-09-16-03-13.jpg" style="width:50%">


<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Button to Journey Page</title>
    <style>
        .my-button {
            background-color: #808080; /* Green background */
            border: none; /* Remove border */
            color: white; /* White text */
            padding: 15px 32px; /* Some padding */
            text-align: center; /* Centered text */
            text-decoration: none; /* Remove underline */
            display: inline-block; /* Make the button inline */
            font-size: 16px; /* Increase font size */
            margin: 4px 2px; /* Margins */
            cursor: pointer; /* Pointer cursor on hover */
            border-radius: 8px; /* Rounded corners */
            transition: background-color 0.3s ease; /* Smooth color transition */
        }
        .my-button:hover {
            background-color: #808080; /* Darker green on hover */
        }
    </style>
</head>
<body>
    <!-- Anchor styled as a button -->
    <a href="my%20jourey" class="my-button">Go to Journey Page</a>
</body>
</html>
<html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Redirect Button</title>
    <style>
        .redirect-button {
            padding: 10px 20px;
            font-size: 16px;
            color: white;
            background-color: #007bff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .redirect-button:hover {
            background-color: #00000;
        }
    </style>
</head>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Redirect Button</title>
    <style>
        .redirect-button {
            padding: 10px 20px;
            font-size: 16px;
            color: white;
            background-color: #007bff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .redirect-button:hover {
            background-color: #FF0000
        }
    </style>
</head>
<body>
    <button class="redirect-button" onclick="window.location.href='https://clicktheredbutton.com/';">
        Red button!
    </button>
</body>
</html>
<body>
    <button class="redirect-button" onclick="window.location.href='https://www.cheetos.com/';">
        Free Cheetos!!!
    </button>
</body>
</html>

<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
.dropbtn {
  background-color: #04AA6D;
  color: white;
  padding: 16px;
  font-size: 16px;
  border: none;
}

.dropdown {
  position: relative;
  display: inline-block;
}

.dropdown-content {
  display: none;
  position: absolute;
  background-color: #f1f1f1;
  min-width: 160px;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 1;
}

.dropdown-content a {
  color: black;
  padding: 12px 16px;
  text-decoration: none;
  display: block;
}

.dropdown-content a:hover {background-color: #ddd;}

.dropdown:hover .dropdown-content {display: block;}

.dropdown:hover .dropbtn {background-color: #3e8e41;}
</style>
</head>
<body style="background-color:white;">

<h2>Hi, my name is Ahmad</h2>
<p>Move the mouse over the button to open the dropdown menu.</p>

<div class="dropdown">
  <button class="dropbtn">sub menu</button>
  <div class="dropdown-content">
    <a href="#"><a href="http://127.0.0.1:4100/Ahmad_2025/aboutme/">about me</a>
</a>
    <a href="http://127.0.0.1:4100/Ahmad_2025/calculator/">calculator</a>
    <a href="http://127.0.0.1:4100/Ahmad_2025/cookieclicker/">cookie clicker</a>
  </div>
</div>

</body>
</html>


<p class=heb>
Monkeys are fascinating primates known for their intelligence, agility, and social behavior. They are found in diverse habitats across the globe, from tropical rainforests to savannas, and they play crucial roles in their ecosystems. With over 260 species, monkeys exhibit a wide range of sizes, colors, and adaptations. Some, like the capuchin, are adept tool users, demonstrating remarkable problem-solving skills, while others, such as the howler monkey, are known for their distinctive vocalizations that can be heard over long distances. Monkeys live in complex social structures, often forming tight-knit groups where they engage in intricate social interactions, grooming, and play. Their behaviors and adaptability continue to intrigue researchers and animal enthusiasts alike, highlighting the rich diversity and evolutionary success of these remarkable animals.
</p>
<!-- Liquid:  statements -->

<!-- Include submenu from _includes to top of pages -->
{% include nav/home.html %}
<!--- Concatenation of site URL to frontmatter image  --->
{% assign sprite_file = site.baseurl | append: page.image %}
<!--- Has is a list variable containing mario metadata for sprite --->
{% assign hash = site.data.mario_metadata %}  
<!--- Size width/height of Sprit images --->
{% assign pixels = 256 %}

<!--- HTML for page contains <p> tag named "Mario" and class properties for a "sprite"  -->

<p id="mario" class="sprite"></p>
  


<style>

  /*CSS style rules for the id and class of the sprite...
  */
  .sprite {
    height: {{pixels}}px;
    width: {{pixels}}px;
    background-image: url('{{sprite_file}}');
    background-repeat: no-repeat;
  }

  /*background position of sprite element
  */
  #mario {
    background-position: calc({{animations[0].col}} * {{pixels}} * -1px) calc({{animations[0].row}} * {{pixels}}* -1px);
  }
</style>

<!--- Embedded executable code--->
<script>
  ////////// convert YML hash to javascript key:value objects /////////

  var mario_metadata = {}; //key, value object
  {% for key in hash %}  
  
  var key = "{{key | first}}"  //key
  var values = {} //values object
  values["row"] = {{key.row}}
  values["col"] = {{key.col}}
  values["frames"] = {{key.frames}}
  mario_metadata[key] = values; //key with values added

  {% endfor %}

  ////////// game object for player /////////

  class Mario {
    constructor(meta_data) {
      this.tID = null;  //capture setInterval() task ID
      this.positionX = 0;  // current position of sprite in X direction
      this.currentSpeed = 0;
      this.marioElement = document.getElementById("mario"); //HTML element of sprite
      this.pixels = {{pixels}}; //pixel offset of images in the sprite, set by liquid constant
      this.interval = 100; //animation time interval
      this.obj = meta_data;
      this.marioElement.style.position = "absolute";
    }

    animate(obj, speed) {
      let frame = 0;
      const row = obj.row * this.pixels;
      this.currentSpeed = speed;

      this.tID = setInterval(() => {
        const col = (frame + obj.col) * this.pixels;
        this.marioElement.style.backgroundPosition = `-${col}px -${row}px`;
        this.marioElement.style.left = `${this.positionX}px`;

        this.positionX += speed;
        frame = (frame + 1) % obj.frames;

        const viewportWidth = window.innerWidth;
        if (this.positionX > viewportWidth - this.pixels) {
          document.documentElement.scrollLeft = this.positionX - viewportWidth + this.pixels;
        }
      }, this.interval);
    }

    startWalking() {
      this.stopAnimate();
      this.animate(this.obj["Walk"], 3);
    }

    startRunning() {
      this.stopAnimate();
      this.animate(this.obj["Run1"], 6);
    }

    startPuffing() {
      this.stopAnimate();
      this.animate(this.obj["Puff"], 0);
    }

    startCheering() {
      this.stopAnimate();
      this.animate(this.obj["Cheer"], 0);
    }

    startFlipping() {
      this.stopAnimate();
      this.animate(this.obj["Flip"], 0);
    }

    startResting() {
      this.stopAnimate();
      this.animate(this.obj["Rest"], 0);
    }

    stopAnimate() {
      clearInterval(this.tID);
    }
  }

  const mario = new Mario(mario_metadata);

  ////////// event control /////////

  window.addEventListener("keydown", (event) => {
    if (event.key === "ArrowRight") {
      event.preventDefault();
      if (event.repeat) {
        mario.startCheering();
      } else {
        if (mario.currentSpeed === 0) {
          mario.startWalking();
        } else if (mario.currentSpeed === 3) {
          mario.startRunning();
        }
      }
    } else if (event.key === "ArrowLeft") {
      event.preventDefault();
      if (event.repeat) {
        mario.stopAnimate();
      } else {
        mario.startPuffing();
      }
    }
  });

  //touch events that enable animations
  window.addEventListener("touchstart", (event) => {
    event.preventDefault(); // prevent default browser action
    if (event.touches[0].clientX > window.innerWidth / 2) {
      // move right
      if (currentSpeed === 0) { // if at rest, go to walking
        mario.startWalking();
      } else if (currentSpeed === 3) { // if walking, go to running
        mario.startRunning();
      }
    } else {
      // move left
      mario.startPuffing();
    }
  });

  //stop animation on window blur
  window.addEventListener("blur", () => {
    mario.stopAnimate();
  });

  //start animation on window focus
  window.addEventListener("focus", () => {
     mario.startFlipping();
  });

  //start animation on page load or page refresh
  document.addEventListener("DOMContentLoaded", () => {
    // adjust sprite size for high pixel density devices
    const scale = window.devicePixelRatio;
    const sprite = document.querySelector(".sprite");
    sprite.style.transform = `scale(${0.2 * scale})`;
    mario.startResting();
  });

</script>
<a href="https://www.treehugger.com/things-you-didnt-know-about-monkeys-4869728" style="font-size: 3vw;">interesting facts about monkeys!!!🙈 🙉 🙊 🐒</a>

<a href="https://en.wikipedia.org/wiki/Pakistan" style="font-size: 3vw;">Pakistan Zindabad!!!</a>


<p class=heb>
Pakistan is a diverse and culturally rich country located in South Asia, bordered by India, Afghanistan, Iran, and China. Established in 1947, it was created as a separate nation for Muslims of the Indian subcontinent, and it has a complex history shaped by its unique geographical and cultural landscapes. Pakistan is known for its stunning natural beauty, which includes the towering peaks of the Himalayas and the Karakoram Range, the lush greenery of the Punjab region, and the arid expanses of the Balochistan desert. The country boasts a rich cultural heritage that reflects a blend of South Asian, Central Asian, and Middle Eastern influences. Its cities, such as Karachi, Lahore, and Islamabad, are vibrant centers of commerce, history, and culture. Pakistan also has a growing economy and is strategically important in regional and global geopolitics. Despite facing various challenges, Pakistan continues to be a nation with a deep historical legacy and a dynamic, evolving identity.
</p>


<style>
    .heb {
        position: relative;
        
        border-style: dotted;
    }
</style>
