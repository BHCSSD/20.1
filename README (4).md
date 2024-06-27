# 20.1.5-Units-Converter
S&T

```
function setup() {
	createCanvas(800, 600);
  background(200,100,80);

    textSize(40);
    fill(255);
    text("Units Converter", 50, 50);
    textSize(20);
    text("Press t to convert temperature", 50 , 100);
    text("Press c to convert centimetres to feet and inches", 50, 130);

}//end setup

function draw() {  
}//end draw

function mousePressed() {
    print("MouseX: " + mouseX +"     MouseY: " + mouseY  );
}//end mousePressed

function keyPressed() {

    if(key === 't'){
        let fahrenheit = window.prompt("What is the temperature in fahrenheit?");
        getTemp(fahrenheit);
    }

    if(key === 'c'){
        let centimetres = window.prompt("What is the length in centimetres?");
        getInches(centimetres);
    }
}//end keyPressed
    
 
function getInches ( c  ){
    fill(0);
    rect(20, 170, 500, 150);
    fill(255);
    text("Total length in centimetres: " + c, 50, 200);
    


}//end getInches



function getTemp (  f  ){
    fill(0);
    rect(20, 170, 500, 150);
    fill(255);
    text("Fahrenheit: " + f, 50, 200);

    

}//end getTemp

```
