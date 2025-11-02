+++
title = "Projects"
url = "/projects/"
ShowReadingTime = false
draft = false
+++

## MCP Servers

I've built several Model Context Protocol servers:

- **International Weather** - This is a local MCP server that you can download from my github and use with application like claude desktop to give models access to international weather data. This was the second MCP server that I made and it was programmed in typescript. https://github.com/Zachwitte21/Open-Meteo-MCP-Server
- **National Weather Service** - This is a local MCP server that I built using python to give AI models access to the National Weather Service Forcasts and Alerts. https://github.com/Zachwitte21/weather-mcp

## University of Delaware Virtual Campus

During college at the University of Delaware I conducted drone research on a small team of 6 students where we used drones to take scans of buildings and then recreate them as 3d models using photogrammetry and machine learning. At the end of the year I took those scans and create a virtual tour website that anyone can use to fly around the UDel campus and see what it looks like.

Link: https://github.com/Zachwitte21/drone-virtual-tour 

## Python Compiler

This is a project that I build during college at the University of Delaware. It is a basic compiler that I built in python! Through this project I learned a lot about how compilers work, code coverage, and unit testing. 

Link: https://github.com/Zachwitte21/python-compiler

## Stock Management Application

During the last semester of my senior year, myself and 4 other students built a stock management application for an engineering lab on campus. This involved meeting with the client and working with them to build an application that met their needs. In the end we build out a website that had authentication for administrators to track the current stock of everything in the lab and employees to use on ipads to take out stock whenever someone needed something. Then I deployed the completed dockerized stack onto AWS, leaving the client with a polished, deployed, and secure application. 

<style>
.carousel-container {
  position: relative;
  max-width: 800px;
  margin: 2rem auto;
  overflow: hidden;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  background-color: #f0f0f0;
}
.carousel-inner {
  display: flex;
  transition: transform 0.5s ease-in-out;
}
.carousel-item {
  min-width: 100%;
  height: 500px;
  object-fit: contain;
  background-color: #f0f0f0;
}
.carousel-controls {
  position: absolute;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 10px;
  z-index: 10;
}
.carousel-dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background-color: rgba(255, 255, 255, 0.5);
  border: 2px solid rgba(255, 255, 255, 0.8);
  cursor: pointer;
  transition: background-color 0.3s;
}
.carousel-dot.active {
  background-color: rgba(255, 255, 255, 0.9);
}
.carousel-arrow {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background-color: rgba(0, 0, 0, 0.5);
  color: white;
  border: none;
  font-size: 24px;
  padding: 10px 15px;
  cursor: pointer;
  border-radius: 4px;
  transition: background-color 0.3s;
  z-index: 10;
}
.carousel-arrow:hover {
  background-color: rgba(0, 0, 0, 0.7);
}
.carousel-arrow.left {
  left: 10px;
}
.carousel-arrow.right {
  right: 10px;
}
</style>

<div class="carousel-container">
  <div class="carousel-inner" id="carouselInner">
    <img src="/images/makerspace1.png" class="carousel-item" alt="UDel Makerspace 1">
    <img src="/images/makerspace2.png" class="carousel-item" alt="UDel Makerspace 2">
    <img src="/images/makerspace3.png" class="carousel-item" alt="UDel Makerspace 3">
    <img src="/images/makerspace4.png" class="carousel-item" alt="UDel Makerspace 4">
    <img src="/images/makerspace5.png" class="carousel-item" alt="UDel Makerspace 5">
  </div>
  <button class="carousel-arrow left" onclick="moveSlide(-1)">&#10094;</button>
  <button class="carousel-arrow right" onclick="moveSlide(1)">&#10095;</button>
  <div class="carousel-controls" id="carouselDots"></div>
</div>

<script>
let currentSlide = 0;
const slides = document.querySelectorAll('.carousel-item');
const totalSlides = slides.length;
const dotsContainer = document.getElementById('carouselDots');

// Create dots
for (let i = 0; i < totalSlides; i++) {
  const dot = document.createElement('div');
  dot.className = 'carousel-dot';
  if (i === 0) dot.classList.add('active');
  dot.onclick = () => goToSlide(i);
  dotsContainer.appendChild(dot);
}

function updateCarousel() {
  const carouselInner = document.getElementById('carouselInner');
  carouselInner.style.transform = `translateX(-${currentSlide * 100}%)`;

  // Update dots
  document.querySelectorAll('.carousel-dot').forEach((dot, index) => {
    dot.classList.toggle('active', index === currentSlide);
  });
}

function moveSlide(direction) {
  currentSlide = (currentSlide + direction + totalSlides) % totalSlides;
  updateCarousel();
}

function goToSlide(index) {
  currentSlide = index;
  updateCarousel();
}

// Auto-advance every 4 seconds
setInterval(() => {
  moveSlide(1);
}, 4000);
</script>

---

*More projects coming soon. Check back or follow me on Github at https://github.com/Zachwitte21*