import turtle
import random

screen = turtle.Screen()
screen.setup(800, 600)
screen.bgcolor("#050520")
t = turtle.Turtle()
t.speed(0)
t.hideturtle()


def draw_stars(count):
    '''
    Draws stars
    '''
    for _ in range(count):
        x = random.randint(-400, 400)
        y = random.randint(-100, 300)
        t.penup()
        t.goto(x, y)
        t.pendown()
        t.dot(random.randint(1, 3), "white")

def draw_windows(start_x, start_y, width, height):
    '''
    Draws window
    '''
    window_size = 10
    padding = 15
    
    for x in range(start_x + padding, start_x + width - padding, 25):
        for y in range(start_y + padding, start_y + height - padding, 30):
            if random.random() > 0.4:
                t.penup()
                t.goto(x, y)
                t.pendown()
                t.fillcolor(random.choice(["#FFD700", "#FFFACD", "#F0E68C"]))
                t.begin_fill()
                for _ in range(4):
                    t.forward(window_size)
                    t.left(90)
                t.end_fill()

def draw_building(x, y, width, height, color="#1A1A1A"):
    '''
    Draws building
    '''
    t.penup()
    t.goto(x, y)
    t.pendown()
    t.fillcolor(color)
    t.begin_fill()
    for _ in range(2):
        t.forward(width)
        t.left(90)
        t.forward(height)
        t.left(90)
    t.end_fill()
    
    draw_windows(x, y, width, height)

def create_cityscape():
    '''
    Creates cityscapes
    '''
    draw_stars(80)
    
    current_x = -400
    while current_x < 400:
        b_width = random.randint(60, 120)
        b_height = random.randint(150, 450)
        draw_building(current_x, -300, b_width, b_height)
        current_x += b_width + 5


create_cityscape()
screen.mainloop()
