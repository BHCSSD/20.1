# 20.1.2-Band-Name

```
let allBands = ["The Beatles", "BTS", "Lil Nas X", "ACDC", "The Weeknd", "Migos", "Juice WRLD", "Halsey", "The Kid LAROI"];
let nameToCheck;

function setup() {
  createCanvas(800, 600);
  background(200, 0, 80);
}//end setup

function draw() {
  //Instructions box
  fill(255);
  strokeWeight(3);
  stroke(50, 50, 100);
  rect(20, 20, width - 40, 200);
  fill(0);
  noStroke();

  textSize(25);
  text("Welcome to the new band name analyzer.", 50, 100);
  textSize(15);
  text("This website will judge how much money your band name will generate.", 50, 130);
  text("Press b to enter your band name.", 50, 160);

}//end draw

function keyPressed() {
  if (key === 'b') {
    nameToCheck = window.prompt("What is your proposed band name?");
    fill(255);
    strokeWeight(3);
    stroke(50, 50, 100);
    rect(20, 230, width - 40, 150);
    
    fill(0);
    noStroke();
    textSize(15);
    text("Searching for: " + nameToCheck, 50, 270);
    
    let foundIndex = linearSearch(allBands, nameToCheck);
    if (foundIndex != -1) {
      text("Sorry, this name already exists.", 50, 300);
        if(nameToCheck.includes("s")){
          text("Perhaps try " + nameToCheck.replace("s","$$$"), 50, 330);
        }//end of nested if
 
      } else {
      text("Congratulations. This is a new name.", 50, 300);
      text("Press a to analyze.", 50, 330);   
      }//end of if

  }//end b key
  else if (key === 'a'){
    fill(255);
    strokeWeight(3);
    stroke(50, 50, 100);
    rect(20, 390, width - 40, 190);
    fill(0);
    noStroke();
    textSize(15);
    
    let namescore = 0;

// CODE TO ADD HERE
    if( nameToCheck. ____  ){
      namescore++;
    }
    if(nameToCheck. ____){
      namescore += 5;
    }
    if(nameToCheck. ____ ){
      namescore++;
    }
    if(nameToCheck. ____){
      namescore += 10;
    }
    if(  nameToCheck. ____){
      namescore+=100;
    }
    
    text(nameToCheck + " will make $" + namescore + " million.", 50, 420);
    allBands.push(nameToCheck);
  }//end a key
}//end keyPressed


function linearSearch(  array, searchTerm      ){
  for(let i=0; i<array.length; i++){
    if(array[i].toLowerCase()    === searchTerm.toLowerCase()   ){
      return i;
    }// end if
  }end for
  return -1;
}//end linearSearch





```
