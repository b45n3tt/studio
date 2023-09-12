---
title: "Timing Carousel"
date: 2023-08-31
draft: false
---
Animated note lengths guided loosely by the principles of music theory. 
{{< rawhtml >}}
  
    <style>
.wheel {
    border: 0px solid black;
    border-radius: 50%;
    margin-left: 50px;
    position: absolute;
    height: 55vw;
    width: 55vw;
    max-width: 500px;
    max-height: 500px;
    animation-name: wheel;
   
    animation-duration: 30s;
    animation-iteration-count: infinite;
    animation-timing-function: linear;
    
    margin: 180px 30%;
  }
  
  .line {
    background-color: black;
    width: 100%;
    height: 3px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform-origin: 0% 0%;
  }
  
  
  .line:nth-of-type(2) {
    transform: rotate(30deg);
    height: 0px;
  }
  .line:nth-of-type(3) {
    transform: rotate(60deg);
    height: 0px;
  }
  .line:nth-of-type(4) {
    transform: rotate(90deg);
    height: 0px;
  }
  .line:nth-of-type(5) {
    /*third*/
    transform: rotate(120deg);
    width: 66.4%;
  }
  .line:nth-of-type(6) {
    transform: rotate(150deg);
    height: 0px;
  }
  .line:nth-of-type(7) {
    transform: rotate(180deg);
    height: 0px;
  }
  .line:nth-of-type(8) {
  /*fifth*/
    transform: rotate(210deg);
    width: 41.5%;
  }
  .line:nth-of-type(9) {
    transform: rotate(240deg);
    height: 0px;
  }
  .line:nth-of-type(10) {
    transform: rotate(270deg);
    height: 0px;
  }
  .line:nth-of-type(11) {
    transform: rotate(300deg);
    height: 0px;
  }
  .line:nth-of-type(12) {
    /*seventh*/
    transform: rotate(330deg);
    width: 8.3%;
  }
  
  .cabin {
    
    width: 120%;
    height: 2%;
    position: absolute;
    border: 2px solid;
    transform-origin: 50% 0%;
    animation: cabins 15s ease-in-out infinite;
  }
  
  .cabin:nth-of-type(1) {
    right: -8.5%;
    top: 50%;
    background-color: black;
  }
  .cabin:nth-of-type(2) {
    right: -3%;
    top: 75%;
    background-color: black;
  }
  .cabin:nth-of-type(3) {
    right: 17%;
    top: 93.5%;
    background-color: black;
  }
  .cabin:nth-of-type(4) {
    left: 39%;
    top: 100%;
    background-color: black;
  }
  .cabin:nth-of-type(5) {
     /*third*/
    left: 14%;
    top: 93.5%;
  }
  .cabin:nth-of-type(6) {
    left: -5%;
    top: 75%;
    background-color: black;
  }
  .cabin:nth-of-type(7) {
    left: -8.5%;
    top: 50%;
    background-color: black;
  }
  .cabin:nth-of-type(8) {
    /*fifth*/
    left: -5%;
    top: 25%;
  }
  .cabin:nth-of-type(9) {
    left: 14%;
    top: 6%;
    background-color: black;
  }
  .cabin:nth-of-type(10) {
    right: 39%;
    top: 0%;
    background-color: black;
  }
  .cabin:nth-of-type(11) {
    right: 15%;
    top: 7%;
    background-color: black;
  }
  .cabin:nth-of-type(12) {
    /*seventh*/
    right: -3%;
    top: 25%;
  }
  
  
  
  @keyframes wheel {
     0% {
       transform: rotate(0deg);
     }
     100% {
       transform: rotate(360deg);
     }
  }
  
  @keyframes cabins {
    0% {
      transform: rotate(0deg);
    }
    25% {
      background-color: yellow;
    }
    50% {
      
      transform: rotate(-360deg);
    }
    75% {
      background-color: rgb(255, 0, 255);
    }
    100% {
      transform: rotate(0deg);
    }
  }
    </style>
</head>
<body>
   
        <div class="wheel">
          <span class="line"></span>
          <span class="line"></span>
          <span class="line"></span>
          <span class="line"></span>
          <span class="line"></span>
          <span class="line"></span>
          <span class="line"></span>
          <span class="line"></span>
          <span class="line"></span>
          <span class="line"></span>
          <span class="line"></span>
          <span class="line"></span>
    
          <div class="cabin"></div>
          <div class="cabin"></div>
          <div class="cabin"></div>
          <div class="cabin"></div>
          <div class="cabin"></div>
          <div class="cabin"></div>
          <div class="cabin"></div>
          <div class="cabin"></div>
          <div class="cabin"></div>
          <div class="cabin"></div>
          <div class="cabin"></div>
          <div class="cabin"></div>
        </div>
      
</body>
</html>
{{< /rawhtml >}}
