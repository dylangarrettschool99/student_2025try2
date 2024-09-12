---
layout: page
title: About
permalink: /about/
---
<style>
    /* Scoped styles for the image slider */
    .my-slider-container {
        position: relative;
        width: 600px;
        height: 400px;
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

<div class="my-slider-container">
    <img src="https://via.placeholder.com/600x400?text=Image+1" class="my-slide" alt="Image 1">
    <img src="https://via.placeholder.com/600x400?text=Image+2" class="my-slide hidden" alt="Image 2">
    <img src="https://via.placeholder.com/600x400?text=Image+3" class="my-slide hidden" alt="Image 3">
    <img src="https://via.placeholder.com/600x400?text=Image+4" class="my-slide hidden" alt="Image 4">
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
