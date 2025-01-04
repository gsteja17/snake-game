from turtle import Turtle,Screen
STARTING_POSITIONS=[(0,0),(-20,0),(-40,0)]
UP=90
DOWN=270
LEFT=180
RIGHT=0
class Snake:
    def __init__(self):
        self.segments = []
        self.create()
        self.head=self.segments[0]


    def create(self):
        for i in STARTING_POSITIONS:
            self.addsegment(i)

    def addsegment(self,position):
        new_segment = Turtle(shape="square")
        new_segment.penup()
        new_segment.goto(position)
        new_segment.color("white")
        self.segments.append(new_segment)


    def extend(self):
        self.addsegment(self.segments[-1].position())
    def move(self):
        for seg in range(len(self.segments)-1, 0, -1):
            self.segments[seg].goto(x=self.segments[seg - 1].xcor(), y=self.segments[seg - 1].ycor())
        self.head.forward(20)
    def snake_reset(self):
        for seg in self.segments:
            seg.goto(1000,1000)
        self.segments.clear()
        self.create()
        self.head=self.segments[0]
    def up(self):
        if self.head.heading()!=DOWN:
            self.head.setheading(UP)
    def down(self):
        if self.head.heading()!=UP:
            self.head.setheading(DOWN)

    def right(self):
        if self.head.heading()!=LEFT:
            self.head.setheading(RIGHT)
    def left(self):
        if self.head.heading()!=RIGHT:
            self.head.setheading(LEFT)