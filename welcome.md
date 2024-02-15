---
layout: default
title: Welcome
permalink: /welcome
---
# Welcome ALL TO OUR GREAT WEBSITE                                                  
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Parallax Scrolling</title>
    <style>
        /* Add some basic styling */
        body, html {
            margin: 0;
            padding: 0;
            height: 100%;
        }
        .parallax-container {
            height: 200%; /* Set the height to 200% to allow for scrolling */
            width: 100%;
            overflow-x: hidden;
            overflow-y: auto;
            position: relative;
            margin-bottom: 10px; /* Leave 10px of blank space at the bottom */
        }
        .parallax-image {
            background-size: cover;
            background-position: center;
            height: calc(70vh - 3px); /* Set the height to 50% of the viewport height minus 3 pixels */
            width: 100%;
            border: 8px ;
            box-sizing: border-box;
            display: flex;
            justify-content: center;
            align-items: center;
            margin-top: calc(10vh + 3px); /* Center the image vertically */
            position: relative;
        }
        /* Create the parallax scrolling effect */
        .parallax-image {
            background-attachment: fixed;
        }
        .parallax-image a {
            font-size: 48px; /* Make the font two times bigger */
            font-weight: bold; /* Make the font bold */
            position: absolute;
            top: 10px; /* Adjust vertical position */
            color: white; /* Set text color */
            text-decoration: none; /* Remove underline */
            z-index: 1; /* Ensure the title is above the image */
        }
        /* Customize title colors */
        .parallax-image:nth-child(1) a { color: #000000; } /* Red */
        .parallax-image:nth-child(2) a { color: #FC28FF; } /* Green */
        .parallax-image:nth-child(3) a { color: #8628FF; } /* Blue */
        .parallax-image:nth-child(4) a { color: #000000; } /* Yellow */
    </style>
</head>
<body>
<div class="parallax-container">
    <div class="parallax-image" style="background-image: url('https://w0.peakpx.com/wallpaper/595/522/HD-wallpaper-grapefruit-lemonade-pink-drink-lemon-lime.jpg')">
        <a href="http://127.0.0.1:4200/student/drink">Drinks</a>
    </div>
    <div class="parallax-image" style="background-image: url('https://wallpapers.com/images/hd/heartbeat-neon-dark-pink-sdmjcfbn14ol4nvy.jpg')">
        <a href="http://127.0.0.1:4200/student/pulse">Heart Rate</a>
    </div>
    <div class="parallax-image" style="background-image: url('https://img.freepik.com/premium-photo/bed-sleep-stands-pink-clouds-good-soft-sleep_124715-2921.jpg ')">
        <a href="/page3">Sleep</a>
    </div>
    <div class="parallax-image" style="background-image: url('https://images.squarespace-cdn.com/content/v1/5b147413a9e02837b93f4066/1587961394040-XMRUTY3OL4NT6B50TIXD/PopTennis-14x11.jpg')">
        <a href="http://127.0.0.1:4200/student/Fitness">Fitness</a>
    </div>
    <div class="parallax-bar bar1"></div>
    <div class="parallax-bar bar2"></div>
    <div class="parallax-bar bar3"></div>
    <div class="parallax-bar bar4"></div>
</div>
</body>
</html>