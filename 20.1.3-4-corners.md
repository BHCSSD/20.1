# 20.1.3-4-corners
Marked

## todo
1. Change size to 600x400
2. set up an if statement that changes the colour of the background into a unique color depending on which quadrant the mouse is clicked in.
  - You will need to do some problem-solving...
  - remember: and = &&,  or = ||
  - to find out if 2 things are equal we use 3 equal signs.  5===(3+2) is true,  5===(3+3) is false
  - you will need mouseX and mouseY for this to work. 

```
//20.1.2-4-corners

function setup() {
  createCanvas(400, 400);
  background(220);
}

function draw() {
  // This function is called continuously
}

function mouseClicked() {
// Check which quadrant the mouse click is in.
// think of this as your hitbox. if your mouse is inside of this, the code will run.
// if( this is true){
// this will run
// } else if (the first  if is not true, test this){
// run this
// }else{
// if all else fails do this
// }


  if (mouseX < ___ && mouseY < ___) {
    // Top-left quadrant (Change color to red)
    
   }// else if(){
     // Bottom-right quadrant (Change color to yellow)
  
  // }
}



// goal is to change color in every corner 

```
