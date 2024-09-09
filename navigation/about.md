---
layout: page
title: About
permalink: /about/
---
## About the creator

Here are some of my interests

<style>
    /* Style looks pretty compact, 
       - grid-container and grid-item are referenced in the code 
    */
    .grid-container {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); /* Dynamic columns */
        gap: 10px;
    }
    .grid-item {
        text-align: center;
    }
    .grid-item img {
        width: 100%;
        height: 100px; /* Fixed height for uniformity */
        object-fit: cover; /* Ensure the image fits within the fixed height */
        animation-name: cf3FadeInOut; /* Apply the animation */
        animation-timing-function: ease-in-out;
        animation-iteration-count: infinite;
        animation-duration: 10s;
        animation-direction: alternate;
    }
    .grid-item p {
        margin: 5px 0; /* Add some margin for spacing */
    }

    .image-gallery {
        display: flex;
        flex-wrap: nowrap;
        overflow-x: auto;
        gap: 10px;
    }

    .image-gallery img {
        max-height: 150px;
        object-fit: cover;
        border-radius: 5px;
    }

    /* Animation styles */
    @keyframes cf3FadeInOut {
        0% {
            opacity: 1;
        }
        45% {
            opacity: 1;
        }
        55% {
            opacity: 0;
        }
        100% {
            opacity: 0;
        }
    }
</style>

<!-- This grid_container class is used by CSS styling and the id is used by JavaScript connection -->
<div class="grid-container" id="grid_container">
    <!-- content will be added here by JavaScript -->
</div>

<script>
    // 1. Make a connection to the HTML container defined in the HTML div
    var container = document.getElementById("grid_container"); // This container connects to the HTML div

    // 2. Define a JavaScript object for our data rows for the Living in the World grid
    var living_in_the_world = [
        {
            image: "https://upload.wikimedia.org/wikipedia/commons/5/53/Example_Image_1.jpg", // Example image URL
            description: "Description for image 1",
            greeting: "Hello from image 1"
        },
        {
            image: "https://upload.wikimedia.org/wikipedia/commons/a/a0/Example_Image_2.jpg", // Example image URL
            description: "Description for image 2",
            greeting: "Hello from image 2"
        },
        {
            image: "https://upload.wikimedia.org/wikipedia/commons/b/b6/Example_Image_3.jpg", // Example image URL
            description: "Description for image 3",
            greeting: "Hello from image 3"
        },
        {
            image: "", // Example image URL
            description: "Description for image 4",
            greeting: "Hello from image 4"
        }
    ];

    // 3a. Consider how to update style count for size of container
    // The grid-template-columns has been defined as dynamic with auto-fill and minmax

    // 3b. Build grid items inside of our container for each row of data
    for (const location of living_in_the_world) {
        // Create a "div" with "class grid-item" for each row
        var gridItem = document.createElement("div");
        gridItem.className = "grid-item";  // This class name connects the gridItem to the CSS style elements

        // Add "img" HTML tag for the image
        var img = document.createElement("img");
        img.src = location.image; // Use the full image URL directly
        img.alt = location.description + " image"; // Use the description for alt text

        // Add "p" HTML tag for the description
        var description = document.createElement("p");
        description.textContent = location.description; // extract the description

        // Add "p" HTML tag for the greeting
        var greeting = document.createElement("p");
        greeting.textContent = location.greeting;  // extract the greeting

        // Append img and p HTML tags to the grid item DIV
        gridItem.appendChild(img);
        gridItem.appendChild(description);
        gridItem.appendChild(greeting);

        // Append the grid item DIV to the container DIV
        container.appendChild(gridItem);
    }
</script>
