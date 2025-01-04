from turtle import Turtle
class Score(Turtle):
    def __init__(self):
        super().__init__()
        self.score=0
        with open("data.txt") as a:
            self.highscore=int(a.read())
        self.color("white")
        self.penup()
        self.goto(0,270)
        self.hideturtle()
        self.havescore()



    def havescore(self):
        self.clear()
        self.write(arg=f"Score : {self.score} High score : {self.highscore}", align="center", font=('Arial', 20, 'normal'))

    def update_high(self):
        if self.score>self.highscore:
            self.highscore=self.score
            with open("data.txt",mode="w") as a:
                a.write(f"{self.highscore}")

        self.score=0
        self.havescore()




    def increase(self):
        self.score+=1
        self.havescore()



