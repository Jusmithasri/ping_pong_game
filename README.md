Ping-Pong Game Project

Description: This project is a two-player Ping-Pong game developed using Python and the Turtle graphics library. The game simulates a classic ping-pong match, with each player controlling a paddle to hit the ball back and forth.

Features:

Two-player support: Player 1 uses the 'Up' and 'Down' arrow keys to move their paddle, while Player 2 uses the 'u' and 'j' keys.

Graphics and Animation: The game features smooth animations and graphics created using the Turtle module.

Score Tracking: The game keeps track of each player's score, displaying the current scores at the top of the screen.

Winning Condition: The first player to reach the target score of 20 points wins the game, which is then announced on the screen.

Instructions:

Move Paddles:

Player 1: Use the 'Up' and 'Down' arrow keys to move the right paddle.

Player 2: Use the 'u' key to move the left paddle up and the 'j' key to move it down.

Start the Game: Run the game script to start the match.

Gameplay: Hit the ball with your paddle to send it back to your opponent. Each time your opponent misses the ball, you score a point.

Winning: The game continues until one player reaches the target score of 20 points. The winner is then announced, and the game ends.

How to Run:

Ensure you have Python installed on your computer.

Install the Turtle graphics library if not already installed.

Run the script in a Python environment to start the game.
Code:

python
#ping_pong game 
#two players can play this game player
#one can use up and down arrows to move the paddles and 2nd plyer can use 'u' and 'j' letters to move the paddles up and down respectively


import turtle as t #for all the graphics or objects to create the game
import time 

#players score 
player_a_score = 0
player_b_score = 0
target_score = 20  #set the minimum target score to 20

win = t.Screen()   
win.title("Ping-Pong Game") 
win.bgcolor('black')    
win.setup(width=800,height=600) 
win.tracer(0)   

#creating left paddle for the game
paddle_left = t.Turtle()
paddle_left.speed(0)
paddle_left.shape('square')
paddle_left.color('red')
paddle_left.shapesize(stretch_wid=5,stretch_len=1)
paddle_left.penup()
paddle_left.goto(-350,0)

#creating a right paddle for the game
paddle_right = t.Turtle()
paddle_right.speed(0)
paddle_right.shape('square')
paddle_right.shapesize(stretch_wid=5,stretch_len=1)
paddle_right.color('red')
paddle_right.penup()
paddle_right.goto(350,0)

#creating a pong ball for the game
ball = t.Turtle()
ball.speed(0)
ball.shape('circle')
ball.color('yellow')
ball.penup()
ball.goto(0,0)
ball_dx = 1.5   #setting up the pixels for the ball movement.
ball_dy = 1.5

#creating a pen for updating the Score
pen = t.Turtle()
pen.speed(0)
pen.color('skyblue')
pen.penup()
pen.hideturtle()
pen.goto(0,260)
pen.write("Player A: 0                Player B: 0 ",align="center",font=('Monaco',24,"normal"))

#moving the left Paddle using the keyboard
def paddle_left_up():
    y = paddle_left.ycor()
    y = y + 15
    paddle_left.sety(y)

#moving the left paddle down
def paddle_left_down():
    y = paddle_left.ycor()
    y = y - 15
    paddle_left.sety(y)

#Moving the right paddle up
def paddle_right_up():
    y = paddle_right.ycor()
    y = y + 15
    paddle_right.sety(y)

#Moving right paddle down
def paddle_right_down():
    y = paddle_right.ycor()
    y = y - 15
    paddle_right.sety(y)

#Keyboard binding
win.listen()
win.onkeypress(paddle_left_up,"u")
win.onkeypress(paddle_left_down,"j")
win.onkeypress(paddle_right_up,"Up")
win.onkeypress(paddle_right_down,"Down")
while True:
    win.update() 
    #check if either player has reached the target score
    if player_a_score == target_score or player_b_score == target_score:
        pen.goto(0, 0)
        winner = "Player A" if player_a_score == target_score else "Player B"
        pen.clear()
        pen.write("{} wins!".format(winner), align="center", font=('Monaco', 36, "normal"))
        time.sleep(5)  
        break

  #moving the ball
  ball.setx(ball.xcor() + ball_dx)
  ball.sety(ball.ycor() + ball_dy)

  # Setting up the border
  if ball.ycor() > 290:   
       ball.sety(290)
       ball_dy = ball_dy * -1
        
  if ball.ycor() < -290:  
       ball.sety(-290)
       ball_dy = ball_dy * -1

   if ball.xcor() > 390:   
        ball.goto(0,0)
        ball_dx = ball_dx * -1
        player_a_score += 1
        pen.clear()
        pen.write("Player A: {}                  Player B: {} ".format(player_a_score,player_b_score), align="center", font=('Monaco',24,"normal"))

   if ball.xcor() < -390:  
        ball.goto(0,0)
        ball_dx = ball_dx * -1
        player_b_score += 1
        pen.clear()
        pen.write("Player A: {}                  Player B: {} ".format(player_a_score,player_b_score), align="center", font=('Monaco',24,"normal"))

   #Handling the collisions with paddles
    if ball.xcor() > 340 and ball.xcor() < 350 and ball.ycor() < paddle_right.ycor() + 40 and ball.ycor() > paddle_right.ycor() - 40:
        ball.setx(340)
        ball_dx = ball_dx * -1

  if ball.xcor() < -340 and ball.xcor() > -350 and ball.ycor() < paddle_left.ycor() + 40 and ball.ycor() > paddle_left.ycor() - 40:
        ball.setx(-340)
        ball_dx = ball_dx * -1



Conclusion: This Ping-Pong game project is a fun and interactive way to practice Python programming, specifically using the Turtle graphics library for animations and game development. It provides a hands-on experience in creating game mechanics, handling user input, and implementing a scoring system.
