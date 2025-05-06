int sqStartTopLeft = 60; // fixed top left
int sqStartBottRight = 655; // the bottom right side

// dice
int diceButtonRectX = 315;
int diceButtonRectY = 507;
int diceButtonRectW = 170;
int diceButtonRectH = 63;

int currentDiceNum = 0;

// booleans
boolean gamePiece = false;
boolean gamePieceOn = false;

boolean diceOver = false;

boolean greenAdvancedMessage = false;
boolean redBackwardsMessage = false;
boolean endingMessage = false;
boolean winMessage = false;
boolean gameFinished = false;

int gamePieceArraySpot = 0;
int[] xArray = {105, 190, 275, 360, 445, 530, 615, 700, 700, 700, 700, 700, 700, 700, 700, 615, 530, 445, 360, 275, 190, 105, 105, 105, 105, 105, 105, 105, 105};
int[] yArray = {105, 105, 105, 105, 105, 105, 105, 105, 190, 275, 360, 445, 530, 615, 700, 700, 700, 700, 700, 700, 700, 700, 615, 530, 445, 360, 275, 190, 105};

void setup() {
  size(800,800);
}

void keyPressed() {
  if (keyCode == ENTER) {
  saveFrame("####.tif");
  }
}


void draw() {
  update(mouseX,mouseY);
  
  background(129, 172, 236);
  stroke(0);
  
  // board
  fill(255);
  square(50,50,700);
  
  fill(50);
  square(60,60,680);

  // board squares
  fill(106, 106, 104);
  int sqFill = 0;
  int sqX = 60;
  int sqY = 60;
  while (sqFill <= 7) {
    square(sqX,sqStartTopLeft,85);
    square(sqStartTopLeft,sqY,85);
    
    square(sqStartBottRight,sqY,85);
    square(sqX,sqStartBottRight,85);
    
    sqX += 85;
    sqY += 85;
    sqFill++;
  }
  
  drawGreenSq();
  drawRedSq();
  
  
  // inner square
  fill(130,45,45);
  square(145,145,510);
  
  // arrow
  fill(245,203,31);
  noStroke();
  square(85,90,20);
  triangle(105,80,124,100,105,120);
  
  // game piece
  if (!gamePieceOn) {
    fill(0);
    textSize(14);
    text("Click the arrow to start!",60,35);
  } else if (gamePieceOn) {
    fill(50);
    noStroke();
    if (greenAdvancedMessage) {
      fill(0);
      textSize(14);
      text("You landed on a green, and advanced past the nearest red!",145,35);
    } else if (redBackwardsMessage) {
      fill(0);
      textSize(14);
      text("You landed on a red, and advanced back to its closest grey square!",145,35);
    } else if (endingMessage) {
      fill(0);
      textSize(14);
      text("Close! You need to roll the exact number to get to the end and win.", 145,35);
    } else if (winMessage) {
      fill(0);
      textSize(14);
      text("You made it to the end!", 145, 35);
    }
    drawGamePiece(gamePieceArraySpot);
    

  }
  
  // dice button
  stroke(0);
  fill(255);
  rect(diceButtonRectX,diceButtonRectY,diceButtonRectW,diceButtonRectH);
  
  fill(0);
  textSize(20);
  text("Roll Dice", 365, 545);

  // dice
  stroke (0);
  fill(255);
  rect(291,235,215,215);
  
  if (currentDiceNum > 0) {
      fill (0);
      if (currentDiceNum == 1) {
        circle(397,336,25);
      } else if (currentDiceNum == 2) {
        circle(339,288,25);
        circle(459,401,25);
      } else if (currentDiceNum == 3) {
        circle(339,288,25);
        circle(399,342,25);
        circle(459,401,25);
      } else if (currentDiceNum == 4) {
        circle(339,288,25);
        circle(459,288,25);
        circle(339,401,25);
        circle(459,401,25);
      } else if (currentDiceNum == 5) {
        circle(339,288,25);
        circle(459,288,25);
        circle(339,401,25);
        circle(459,401,25);
        circle(399,342,25);
      } else {
        circle(339,288,25);
        circle(459,288,25);
        circle(339,401,25);
        circle(459,401,25);
        circle(459,344,25);
        circle(339,344,25);
      }
  }
  
}

void mouseClicked() {
  if (gameFinished) {
    return;
  }

  if (diceOver && gamePieceOn) {
    currentDiceNum = rollDice();

    greenAdvancedMessage = false;
    redBackwardsMessage = false;
    endingMessage = false;
    winMessage = false;
    
    gamePieceArraySpot += currentDiceNum;
    
    if (gamePieceArraySpot == 1) {
      gamePieceArraySpot += 4;
    } else if (gamePieceArraySpot == 3 || gamePieceArraySpot == 20 ) {
      gamePieceArraySpot += 2;
      greenAdvancedMessage = true;
    } else if (gamePieceArraySpot == 7) {
      gamePieceArraySpot += 9;
      greenAdvancedMessage = true;
    } else if (gamePieceArraySpot == 9) {
      gamePieceArraySpot += 7;
      greenAdvancedMessage = true;
    } else if (gamePieceArraySpot == 12 || gamePieceArraySpot == 18 || gamePieceArraySpot == 24) {
      gamePieceArraySpot += 4;
      greenAdvancedMessage = true;
    } else if (gamePieceArraySpot == 4 || gamePieceArraySpot == 15 || gamePieceArraySpot == 19) {
      gamePieceArraySpot -= 2;
      redBackwardsMessage = true;
    } else if (gamePieceArraySpot == 11 || gamePieceArraySpot == 14) {
      gamePieceArraySpot -= 1;
      redBackwardsMessage = true;
    } else if (gamePieceArraySpot == 21 || gamePieceArraySpot == 25 || gamePieceArraySpot == 27) {
      gamePieceArraySpot -= 4;
      redBackwardsMessage = true;
    } else if (gamePieceArraySpot == 26) {
      gamePieceArraySpot -= 3;
      redBackwardsMessage = true;
    }  else if (gamePieceArraySpot > 28 || gamePieceArraySpot == 25 && currentDiceNum > 3 || gamePieceArraySpot == 26 && currentDiceNum > 2 || gamePieceArraySpot == 27 && currentDiceNum > 1) {
      gamePieceArraySpot = 27;
      endingMessage = true;
    } else if (gamePieceArraySpot == 28) {
      winMessage = true;
      gameFinished = true;
    }
    
  } else if (gamePiece) {
    gamePieceOn = true;
  }
}

void update(int x, int y) {
  if ( checkDice(x,y) ) {
    diceOver = true;
  } else if ( checkGamePiece(x,y) ) {
    gamePiece = true;
  } else {
    gamePiece = false;
    diceOver = false;
  }
}

void drawGreenSq() {
  fill(131,187,94);
  square(145,60,85);
  square(315,60,85);
  square(655,60,85);
  
  square(655,230,85);
  square(655,485,85);
  square(655,655,85);
  
  square(315,655,85);
  square(145,655,85);
  
  square(60,400,85);
}

void drawRedSq() {
  fill(217,72,72);
  square(400,60,85);
  
  square(655,400,85);
  
  square(655,655,85);
  
  square(570,655,85);
  square(230,655,85);
  square(60,655,85);
  
  square(60,315,85);
  square(60,230,85);
  square(60,145,85);
}

boolean checkGamePiece(int x, int y) {
  if (x > 85 && x < 124 && y > 80 && y < 120) {
    return true;
  } else {
    return false;
  }
}

boolean checkDice(int x, int y) {
  if (x > diceButtonRectX && y > diceButtonRectY && 
      x < (diceButtonRectX + diceButtonRectW)
      && y < (diceButtonRectY+diceButtonRectH)) {
    return true;
  } else {
    return false;
  }
}

void drawGamePiece (int spot) {
  circle(xArray[spot], yArray[spot], 50);
}

int rollDice() {
  float result = random(1,6);
  int roll =  round(result);
  
  return roll;
 }
