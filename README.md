# Java Brick Breaker Game
Java Brick Breaker Game is a game application that involves hand-eye coordination and quick thinking from the user. The goal of the game is to break all of the “bricks” that appear at the top of the game window using a “ball” and a “paddle” without letting the ball reach the bottom of the window. Once the user presses a start button, a circular entity representing the ball will start moving down the screen. The user can control the racket by moving it either left or right using the two arrow-key buttons on the keyboard. If timed correctly, the racket can reverse the ball’s direction if it touches it, making it go towards the bricks. If the ball manages to touch a brick, the brick will either fully disappear or crack (indicating another hit needed to clear the brick). Some bricks are made of "steel" and will never break, others have star and indicated that the brick will drop an item if cleared. An item drop will either alter the size of the paddle, create an additional ball, or give the user an additional life. At the top of the window, there is also a score value that increments as a brick is obliterated. If the ball slips past the racket, or if the player successfully hits all bricks, the score will be shown on the middle of the screen and displaying either a win or lose. The game will become progressively difficult as for every 5 bricks cleared the speed of the ball increases.
This project is built off of an open-source project located in this GitHub Repository by Git-user janbodnar: https://github.com/janbodnar/Java-Breakout-Game

![image](https://user-images.githubusercontent.com/89605166/163895961-e73f825f-a7ba-4d85-86c3-989a5faa957c.png)

# Project Board
https://trello.com/b/43fRtdGo/project-board





# How to run
- Download the latest binary from the Release section on the right on GitHub.  
- On the command line uncompress using
```
tar -xzf Java-Brick-Breaker-Game-<version>.tar.gz
```
- On the command, go to file location inside of uncompressed folder
```
cd Java-Brick-Breaker-Game-<version>/out/production/concept-AlexHarvey63
```
- Run by typing command:
```
java BrickBreaker
```
- After running, a window should open up and display the different sprites. Once a change is added that needs to be tested, run the program and see the results of the changes and act on them accordingly. Changes and modifications should be added to other classes by using a text editor or IDE when necessary.

### How to build
- Use this github repository
- Use main branch for the most stable release
- Use latest version of Intellij or other Java compatible IDE
- Requires JPanel, JFrame, and ImageIO packages
- Run the file with the main method, this can be found in BrickBreaker.java
- In terminal:
  - Change current directory to location of code by typing: `cd /<name of cloned repository>/src/main/java`
  - To compile: `javac BrickBreaker.java`
  - To run: `java BrickBreaker`

- After running the app, a window should pop-up and display the paddle, ball, and brick sprites along with additional details.

# UML
![image](https://user-images.githubusercontent.com/89605166/160741478-9e21a3fe-639c-41a0-b2f4-9af7b0143d39.png)
![image](https://user-images.githubusercontent.com/89605166/160741483-c92232b9-dfb7-4899-91d0-a8b93b060bb6.png)
![image](https://user-images.githubusercontent.com/77736858/161879611-bf3b140a-a044-4f81-899d-d73e025acd6f.png)


figure 3 updated on April 5, 22

### Brief UML Overview
The sprite class includes the get and set methods that are used to help generate the visual, moving elements of the game such as the racket, ball and bricks. Naturally, the racket, ball, and brick classes extend sprite, allowing them to initialize their respective positions in the game and generate their visuals. The racket class implements the basicallity functionality of the racket such as move and responding to pressed keys by the user. The ball class behaves similarly, initializing its position while also creating its unique, private move function to define its behavior. Finally, Brick acts in a similar manner, but includes a boolean variable tracking whether or not it has been touched by the ball. If it touched by the ball, its status is update to destroyed.  
The GameBoard, HighScoreBoard, and MenuScreen classes all extend JPanel, a container class. HighScoreBoard and MenuScreen both initialize the visualize components of their respective features. They both use nested private classes, such as returnHandler and startHandler to implement different features of the game such as start and return. GameBoard implements instances of the racket, bricks and ball. It is responsible for printing messages to the user such as “game over”. GameBoard also implements user functionality features like pause and resume by also using nested private classes to handle the functions. Similarly, it contains a nested class to track each time the user pushes and releases a game key. The program package also includes the configuartions interface. This interface includes only attributes relating to the dimensions of each of the game pieces. Lastly, the BrickBreaker class extends the JFrame class and houses the only main() function for the entire program and is responsible for launching the game.

# Sequence Diagrams

![seq1 drawio](https://user-images.githubusercontent.com/97983404/162009722-d3b2809f-7fa0-459a-9095-13e876c1f409.png)

### Sequence 1: Building the GameBoard
When you first run BrickBreaker, main will try to create a BrickBreaker game. Once created, the first thing it does is create a new JPanel MainScreen menu. The MainScreen holds 2 buttons; one to create a HighScore menu, and one to start the game. Clicking the High Score button will create a new JPanel HighScoreBoard which will display all the high scores. Clicking the Start Game button will start the game by creating a new JPanel GameBoard. The GameBoard will then create all the objects we need to play the game. This includes the ball, bricks, and the racket. After creating all the objects, the GameBoard will start the game by starting a timer and invoking the GameCycle method.

![seq2 drawio](https://user-images.githubusercontent.com/97983404/162009837-3a32244d-d9ab-4d63-a51f-de1e4836b523.png)

### Sequence 2: Sample GameCycle
Once the GameCycle method has been invoked, the game will continue to run a doGameCycle loop until the game is over. If the player presses either the left or right arrow key at any point, the GameBoard will update the position of the racket first. During a game cycle, several things will happen in order. First, the position of the racket is  updated based on user input. Then, the position of the ball is updated. Finally, the GameBoard will call checkCollision on itself. This method will check if the ball hit the racket, and if the ball hit any bricks. If the ball hits the racket, the x and y position of the ball will be updated. If the ball hit nany bricks, those bricks will be destroyed. If any of the conditions for ending the game are met, such as destroying all of the bricks or losing all of your lives, the game will end. The  GameBoard also holds two buttons, one to pause the game and one to restart the game.
