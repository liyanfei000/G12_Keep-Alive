# G12_Keep-Alive
##Project idea
This project is aimed to simulate an experience of breathing in air-polluted cities. 
In this application, different cities can be chosen. The more serious the pollution is, the more mask protection you need, the more difficult to breathe, the more time you need to press the mouse.

##Challenges related to it
  *How to choose different cities.
  *How to visualize the different level of air pollution. 
  *How to visualize the protection level.
  *How to simulate an experience of breathing.
##Difficulties
  *Make the PM10 dots move as the same way of masks（like a wave line）.

##Reused code
https://p5js.org/examples/math-sine-wave.html
[p5js](https://p5js.org/)

var xspacing = 16;    // Distance between each horizontal location
var w;                // Width of entire wave
var theta = 0.0;      // Start angle at 0
var amplitude = 75.0; // Height of wave
var period = 500.0;   // How many pixels before the wave repeats
var dx;               // Value for incrementing x
var yvalues;  // Using an array to store height values for the wave

function setup() {
  createCanvas(710, 400);
  w = width+16;
  dx = (TWO_PI / period) * xspacing;
  yvalues = new Array(floor(w/xspacing));
}

function draw() {
  background(0);
  calcWave();
  renderWave();
}

function calcWave() {
   theta += 0.02;
  var x = theta;
  for (var i = 0; i < yvalues.length; i++) {
    yvalues[i] = sin(x)*amplitude;
    x+=dx;
  }
}

function renderWave() {
  noStroke();
  fill(255);
  // A simple way to draw the wave with an ellipse at each location
  for (var x = 0; x < yvalues.length; x++) {
    ellipse(x*xspacing, height/2+yvalues[x], 16, 16);
  }
}
