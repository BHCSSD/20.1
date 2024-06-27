# 20.1.8-assignment-bobs-forest
Marked assignment 


This assignment is about making functions that take PARAMETERS as inputs. So all the functions **MUST** be accepting the inputs described for each function to receive full marks. You MAY NOT reference global variables inside the function.

## Task A - DrawSimpleTree (10%)

The DrawSimpleTree function is provided for you in the start code. It draws a trunk and a circle to represent the leaves.

Task A is simply to get the code working according to the instructions below and to read about how the first function works.

On the last pages is the exact code needed to start the program.  Copy that code into the file and get it running.
Read through the code carefully to see how it is structured.  Pay close attention to the `drawSimpleTree()` function as you will need to base the others on that function.

## Task B - DrawPineTree ( 50%)

Create a new function called `drawPineTree` that is set up similar to the `drawSimpleTree` function.

This function has the same first 4 parameters as `drawSimpleTree`:
- An x and y value for specifying where to draw the tree (same as `drawSimpleTree`)
- A width and a height specifying how wide and tall the tree should be (same as  `drawSimpleTree`)
As pine trees are always green, no color parameter should be passed in 

Within the function, draw the tree using the image to the right as a model.
- A pine tree consists of a rectangular trunk and a single triangle for the leaves.
- The trunk can be drawn exactly the same as was done in `drawSimpleTree`. The trunk is always brown. 
- The triangle is always green but feel free to randomize the shade of green.
- You will need to do a bit of math to figure out the corners of the triangle.  
  - Reminder: `triangle(x1,y1, x2, y2, x3,y3)`. The order of the three points does not matter. 

Calling the `drawPineTree` function:
- Call the function using the B key and pass the mouseX and mouseY in as the coordinates (exactly as was done for you for the first type of tree).

## Task C - DrawLeafyTree (20%)

Create a new function called `drawLeafyTree` that is similar in setup to the `drawSimpleTree` function.  

This function has the same 5 parameters as `drawSimpleTree` plus one new one:
  - An x and y value for specifying where to draw the tree (same as `drawSimpleTree`)
  - A width and a height specifying how wide and tall the tree should be (same as  `drawSimpleTree`)
  - A colour for what colour the leaves should be (same as  `drawSimpleTree`)
  - A number of leaves to put on the tree (This is what is new.)

Within the function, draw the tree using the image to the above as a model:
  - The brown trunk can be drawn exactly the same as was done in `drawSimpleTree`.
  - The trunk is always brown. 
  - Draw a bunch of random-sized round leaves that appear anywhere in the upper two-thirds of the tree’s bounding rectangle.  
  - Tip: Use a FOR loop based on the number of leaves passed in with some randomization for the X and Y coordinates of each leaf-circle.

Calling the Leafy Tree function:
- You will call the function in two ways:
  1. Firstly, in SETUP(), you should draw three leafy trees on your screen similar to how the first `drawSimpleTree` is called in setup():
    - A RED tree with only 80 leaves that is 30 pixels wide and 80 pixels tall at the position (130,300) on the screen.
    - An ORANGE tree with 150 leaves that is 30 pixels wide and only 60 pixels tall at the position (330, 300) on the screen.
    - A YELLOW tree with 300 leaves that is 50 pixels wide and 90 pixels tall at the position (50,200) on the screen.
  2. Secondly, call the function using the C key as follows:
    - Pass the mouseX and mouseY in as the coordinates (exactly as was done for you for the first type of tree with the B key).
    - Add a randomized number of leaves that you pass into the function.

## Task D - Adding FancyMode to DrawPineTree (20%)

Firstly, make sure the current version of `drawPineTree` is working consistently.

Do not create a new function.  Instead, add an extra parameter into the existing `drawPineTree` function.  That parameter will take in TRUE or FALSE (or it may be easier to use ZERO or ONE because you can more easily generate a random number later if needed).  That parameter will tell the function if it should draw a plain or fancy tree.

If the parameter is False or Zero, it is in Plain Mode. That means it should draw the pine tree exactly as before.

However, if the parameter passed in is true, it is in Fancy Mode and should draw a fancy tree:
- A FANCY pine tree consists of a rectangular trunk and THREE triangles for the leaves.  

Below is one way to do the math but you can alter these percentages as you wish to make it look better:
- The green triangles take up 85% of the height of the tree. 
- The first triangle is ⅓ the height of the green tall and 1/2 the width of the tree wide
- The first triangle is ⅔  the height of the green tall and 3/4  the width of the tree wide
- The third triangle is the full height of the green and the full width of the tree.

Draw Your Pine Trees:
- Alter the B keyPress call so that it passes in false or Zero to match the updated function.
- Add the D keyPress so that it calls `drawPineTree` but passes in true or ONE.
- Plus, in SETUP, you should draw four  pine trees on your screen:
  - A PLAIN tree that is 40 pixels wide and 100 pixels tall at the position (200,150).
  - A PLAIN tree that is 30 pixels wide and 50 pixels tall at the position (230, 200).
  - A FANCY tree that is 50 pixels wide and 80 pixels tall at the position (400,400).
  - A FANCY tree that is 30 pixels wide and 80 pixels tall at the position (400,200).

## Starter Code 
```javascript
let leafColours = ["green", "red", "orange", "yellow"]
function setup() {
  let sketch = createCanvas(500, 500);
    sketch.parent("mycanvas")
  clearTown();
  drawSimpleTree(200,300, 50,70, "Yellow") 
}//end setup
function draw() {
//empty draw function needed to keep the program looping
}//end draw


function keyPressed(){
    let treeWidth = random(20,60);
    let treeHeight = random(1.5,2)*treeWidth;
    let col = random(leafColours);  //this randomly selects one item out of an array
	
