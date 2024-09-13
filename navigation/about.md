---
layout: page
title: About
permalink: /about/
---
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Image Slider</title>
    <style>
        /* Scoped styles for the image slider */
        .my-slider-container {
            position: relative;
            width: 300px;
            height: 200px;
            overflow: hidden;
            border: 2px solid #ccc;
            margin: 0 auto; /* Center align the slider */
        }
        .my-slider-container .my-slide {
            position: absolute;
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: opacity 1s ease-in-out;
        }
        .my-slider-container .hidden {
            opacity: 0;
        }
    </style>
</head>
<body>
    <div class="my-slider-container">
        <!-- Image Slider -->
        <img src="https://github.com/user-attachments/assets/ca2851d0-3a81-4f74-adbb-6229d0a5c301" class="my-slide" alt="Image 1">
        <img src="https://github.com/user-attachments/assets/16f8c640-5ab6-4c36-8bb3-d5f7f3b3c2a1" class="my-slide hidden" alt="Image 2">
        <img src="https://github.com/user-attachments/assets/8bd4407d-9b96-4f54-b3d9-46f9ce54836c" class="my-slide hidden" alt="Image 3">
        <img src="https://github.com/user-attachments/assets/4fceec1b-dd7c-44f4-8cb5-61ca3c41c4c0" class="my-slide hidden" alt="Image 4">
    </div>

    <script>
        const slides = document.querySelectorAll('.my-slider-container .my-slide');
        let currentSlide = 0;

        function showNextSlide() {
            slides[currentSlide].classList.add('hidden');
            currentSlide = (currentSlide + 1) % slides.length;
            slides[currentSlide].classList.remove('hidden');
        }

        setInterval(showNextSlide, 3000); // Change image every 3 seconds
    </script>
<h3>
Things I enjoy doing in my free time
</h3>
</body>
</html>

- I have been hiking with my family for quite some time now, I enjoy just going anywhere in the area.

- I take many naps and enjoy sleeping a lot throughout the week, but now that school has started again, I have had reduced hours of sleep per day and I am starting to lose my sanity.

- While I havent gone fishing in a while, it is always a very nice feeling to catch something when I go out and do it.

- I like gaming, as any other teenage boy does. although my enjoyment has started to turn into an addiction so I may stop playing soon
<html>
<h3>
Family History
</h3>
<text>
My family comes from mostly all over europe, while my mom is a red head and my dad had blonde hair, I have dark brown hair. However, I have one branch of my family which is from new zealand.
</text>
</html>
<html>
</html>



<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Images Side by Side</title>
    <style>
        .container {
            display: flex;
            gap: 10px; /* Adjust spacing between images if needed */
        }
        .container img {
            width: 300px;
            height: 300px;
            object-fit: cover; /* Ensure the images cover the area without distortion */
        }
    </style>
</head>
<body>
    <div class="container">
        <img src="https://github.com/user-attachments/assets/f97b6be4-032c-4731-9306-9711fb89a1a1" alt="Image 5">
        <img src="https://github.com/user-attachments/assets/5d4651d5-7068-4aae-848e-bc130e772537" alt="Image 6">
    </div>
</body>

