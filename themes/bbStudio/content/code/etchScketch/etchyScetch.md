---
title: "Sketch"
date: 2023-09-06
draft: false
---
Etch-e-scetch model with alterations. 
{{< rawhtml >}}
  
    <style>
body {
    width: 100%; 
    height: 100vh;
    box-sizing: border-box;
    border: 1px solid black;
    margin: 0 auto;
    padding: 5px;
}
.grid-container {
    display: grid;
    grid-template-columns: repeat(size, minmax(0, 1fr));
    grid-template-rows: repeat(size, minmax(0, 1fr));
    /* gap: 1px; */
    width: 100%; 
    height: 100%; 
  }

.grid-item {
    border: 1px solid black;
}
 
  @keyframes pulseOne {
    0% {
      background-color: red;
    }
    33% {
      background-color: rgb(255, 177, 0);
    } 
    50% {
      background-color: rgb(255, 177, 0);
    }
    100% {
      background-color: red;
    }
  }
  
  @keyframes pulseTwo {
    0% {
      background-color: red;
    }
    43% {
      background-color: rgb(255, 177, 0);
    } 
    60% {
      background-color: rgb(255, 177, 0);
    }
    100% {
      background-color: red;
    }
  }

  @keyframes pulseThree {
    0% {
      background-color: red;
    }
    53% {
      background-color: rgb(255, 177, 0);
    } 
    70% {
      background-color: rgb(255, 177, 0);
    }
    100% {
      background-color: red;
    }
  }

  .pulsating,.clear-button,.setColor-button {
    animation: pulseOne 5s infinite;
  }

   .wash-button{
    animation: pulseTwo 5s infinite;
  }

   .gridNumber-button{
    animation: pulseThree 5s infinite;
  }
  .clear-button, .setColor-button, .wash-button, .gridNumber-button{
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: bolder;
    font-family: 'Courier New', Courier, monospace;
    margin: 5px;
    min-width: 15px;
    min-height: 5px;
  }
  </style>

  <!-- html -->

<head>
  <!-- <title>Grid of Square Divs</title>
  <link rel="stylesheet" href="styles.css"> -->
</head>
<body>
  <div class="grid-container"></div>
  <script src="compiled.js" defer></script> 
</body>

<!-- JAvaScript -->

<script>
document.addEventListener("DOMContentLoaded", function() {
    const container = document.querySelector(".grid-container");
    let isMouseDown = false; // Flag to track mouse state
    let clearButton = null; // Variable to hold the clear button element
    let currentColor = "#000000"; // Variable to hold the current background color for the trail
    let setColorButton = null; // Variable to hold the set color button element
    let washColorButton = null; // Variable to wash multiples colors into one
    let gridNumberButton = null;
    let size = 16; // Default grid size
    
    // Create 16x16 grid
    createGrid();
   
    function createGrid() {
      // Set the grid template columns and rows based on the size variable
      container.style.gridTemplateColumns = `repeat(${size}, minmax(0, 1fr))`;
      container.style.gridTemplateRows = `repeat(${size}, minmax(0, 1fr))`;

      // Clear the previous grid items
      container.innerHTML = "";

    // Create new grid items
    for (let i = 0; i < size; i++) {
      for (let j = 0; j < size; j++) {
        const gridItem = document.createElement("div");
        gridItem.classList.add("grid-item");
        container.appendChild(gridItem);
  
        // Mouse hover event listener
        gridItem.addEventListener("mouseover", function(event) {
            gridItem.classList.add("pulsating"); // Apply the pulsating animation on mouse hover. if only this is set all squares pulse
          if (isMouseDown) {
            if (event.target === clearButton) {
              clearGrid();
            } else if (event.target === setColorButton) {
              setColor();
            } else if (event.target === washColorButton) {
              washColor();
            } else {
              event.target.style.backgroundColor = currentColor; // Set the background color on mouse hover
            }
          }
        });
  
        // Remove the animation on mouse leave
        gridItem.addEventListener("mouseleave", function() {
            gridItem.classList.remove("pulsating");
        });

        gridItem.addEventListener("mousedown", function(event) {
          isMouseDown = true;
          if (event.target === clearButton) {
            clearGrid();
          } else if (event.target === setColorButton) {
            setColor();
          } else if (event.target === washColorButton) {
            washColor();
          } else {
            event.target.style.backgroundColor = event.target.style.backgroundColor === "black" ? "transparent" : "black"; // Toggle between black and transparen, Set the background color on mouse down
          }
        });
  
        // Add mouse up event listener
        gridItem.addEventListener("mouseup", function() {
          isMouseDown = false;
        });
  
        // Set the first grid item as the clear button
        if (i === 0 && j === 0) {
          gridItem.textContent = String.fromCodePoint(0x21BB); // U+21BB: Unicode character for "↻"
          gridItem.classList.add("clear-button");
          clearButton = gridItem;
        }
  
        // Set the second grid item as the set color button
        if (i === 0 && j === 2) {
          gridItem.textContent = String.fromCodePoint(0x1F308);
          gridItem.classList.add("setColor-button");
          setColorButton = gridItem;
        }

        // Set the third grid item as the wash button
        if (i === 0 && j === 1) {
            gridItem.textContent = String.fromCodePoint(0x1F30A);
            gridItem.classList.add("wash-button");
            washColorButton = gridItem;
          }
           if (i === 0 && j === 3) {
          gridItem.textContent = String.fromCodePoint(0x0023);
          gridItem.classList.add("gridNumber-button");
          gridNumberButton = gridItem;
          gridItem.addEventListener("click", function() {
            changeGridSize();
          });
        }
      }
    }
  }
  
  function changeGridSize() {
    const newSize = parseInt(prompt("Enter the new grid size 4-100 (e.g., 16 for a 16x16 grid):"));
    if (isNaN(newSize) || newSize < 4 || newSize > 100) {
      alert("Invalid grid size. Please enter a valid number.");
    } else {
      size = newSize;
      createGrid();
    }
  }
  
    function clearGrid() {
      const gridItems = document.querySelectorAll(".grid-item");
      gridItems.forEach(function(item) {
        item.style.backgroundColor = "transparent"; // Reset the background color of all grid items
      });
    }
  
    function getRandomColor() {
      const letters = "0123456789ABCDEF";
      let color = "#";
      for (let i = 0; i < 6; i++) {
        color += letters[Math.floor(Math.random() * 16)];
      }
      return color;
    }
  
    function setColor() {
      currentColor = getRandomColor(); // Generate a random color and assign it to the currentColor variable
    }

    function washColor() {
        const gridItems = document.querySelectorAll(".grid-item");
        gridItems.forEach(function(item) {
          const currentBackgroundColor = item.style.backgroundColor;
          if (currentBackgroundColor) {
            item.style.backgroundColor = currentColor;  // Set the background color to a new color for items with a background color
            item.style.transition = "background-color 1s";  
        }
        });
     }
  });
      </script>
</html>
{{< /rawhtml >}}