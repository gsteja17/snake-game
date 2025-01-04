from turtle import Turtle,Screen
from snake import Snake
from food import Food
from scoreboard import Score
import time
screen=Screen()
screen.bgcolor("black")
screen.setup(width=600,height=600)
screen.title("Snake Game")
screen.tracer(0)

snake=Snake()
food=Food()
screen.listen()
score=Score()

screen.onkey(key="Up",fun=snake.up)
screen.onkey(key="Left",fun=snake.left)
screen.onkey(key="Down",fun=snake.down)
screen.onkey(key="Right",fun=snake.right)
game_on=True
while game_on:
    screen.update()
    time.sleep(0.1)
    snake.move()

    if snake.head.distance(food)<15:
        food.refresh()
        snake.extend()
        score.increase()

    if snake.head.xcor() > 290 or snake.head.xcor()<-290 or snake.head.ycor()>290 or snake.head.ycor()<-290:
        score.update_high()
        snake.snake_reset()


    for segments in snake.segments[1:]:
        if snake.head.distance(segments)<10:

            score.update_high()
            snake.snake_reset()


screen.exitonclick()