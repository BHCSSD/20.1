# 20.1.1-fish-tank-example
How to load images

# How to load images

## 0) Variables
Make your variables so the computer knows where to store the images in its memory
- let octPic;

## 1) preload() 
Called directly before setup(), the preload() function is used to load external files before any other code can run. If a preload function is defined, setup() will wait until any load calls within have finished. Nothing besides load calls (loadImage, loadJSON, loadFont, loadStrings, etc.) should be inside the preload function.
- octPic = loadImage(path)
  - loads the image into the variable 

## 2) show the image
Tells p5 where to load and show the image
- image(octPic, 0, 0)

Starter code: 
```
let oceanPic, coralPic;
let octPic;

let fishX = 300;

function preload() {

    

}//end preload

function setup() {
    createCanvas(800, 600);
   
    
    //drawSchool(400, 300, 10);
}//end setup

function draw() {

    //drawSchool(400, 300, 10);
    //drawCoral(725,200,400);


    drawFish(fishX, 200, 118);
    fishX+=3;
    
    if(fishX>width){
        fishX = 0;
    }
}//end draw

function mousePressed() {
    print("MouseX: " + mouseX + "     MouseY: " + mouseY);
}//end mousePressed



function drawFish( centerX, centerY, bodyLength){
//------- Begin Fish -------------
    var bodyHeight = bodyLength*0.6;
    var bodyColor = color(162, 0, 255);

    noStroke();
    fill(bodyColor);
    // body
    ellipse(centerX, centerY, bodyLength, bodyHeight);
    // tail
    var tailWidth = bodyLength / 4;
    var tailHeight = bodyHeight / 2;
    triangle(centerX - bodyLength / 2, centerY,
        centerX - bodyLength / 2 - tailWidth, centerY - tailHeight,
        centerX - bodyLength / 2 - tailWidth, centerY + tailHeight);
    // eye
    fill(33, 33, 33);
    ellipse(centerX + bodyLength / 4, centerY, bodyHeight / 5, bodyHeight / 5);

};   //end drawFish


function drawSchool(schoolX, schoolY, numFish){
    for(let i=0; i<numFish; i++){
        let centerX = random(-50, 50)+ schoolX;
        let centerY = random(-50, 50)+ schoolY;
        let fishSize = random(25, 75);
        image(octPic, centerX, centerY, fishSize, fishSize);
    }
}//end drawSchool

```
