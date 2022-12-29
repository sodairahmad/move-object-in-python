# move-object-in-python
how to move object in python

code

from tkinter import *

def moveup(event):
    label.place(x=label.winfo_x(),y=label.winfo_y()-10)
def movedown(event):
    label.place(x=label.winfo_x(),y=label.winfo_y()+10)
def moveleft(event):
    label.place(x=label.winfo_x()-10,y=label.winfo_y())
def moveright(event):
    label.place(x=label.winfo_x()+10,y=label.winfo_y())

window= Tk()
window.title("move object game")
window.bind("<w>",moveup)
window.bind("<s>",movedown)
window.bind("<a>",moveleft)
window.bind("<d>",moveright)
window.bind("<Up>",moveup)
window.bind("<Down>",movedown)
window.bind("<Left>",moveleft)
window.bind("<Right>",moveright)

window.geometry("800x600")
car=PhotoImage(file='car.png')
label=Label(window,image=car,bg='red',text='move game',compound=LEFT)
label.place(x=0,y=0)


window.mainloop()


END()..........................................................


TITLE(HOW TO MOVE CANVAS IMAGES IN PYTHON)
CODE

from tkinter import *

def moveup(event):
    canvas.move(image,0,-10)
def movedown(event):
    canvas.move(image, 0, 10)
def moveleft(event):
    canvas.move(image,-10,0)
def moveright(event):
    canvas.move(image, 10, 0)
window= Tk()

window.title("move object game")
window.bind("<w>",moveup)
window.bind("<s>",movedown)
window.bind("<a>",moveleft)
window.bind("<d>",moveright)
window.bind("<Up>",moveup)
window.bind("<Down>",movedown)
window.bind("<Left>",moveleft)
window.bind("<Right>",moveright)

canvas=Canvas(window,height=500,width=700)
canvas.pack()


photo= PhotoImage(file='moveimage.png')
image=canvas.create_image(0,0, image=photo,anchor=NW)


window.mainloop()


END().................................................................

TITLE (HOW TO MOVE OBJECT CONTINUOUSLY IN PYTHON)
CODE

from tkinter import *
import time

HEIGHT=500
WIDTH=500
xvelocity=30
yvelocity=24

window= Tk()
cannvas=Canvas(window,height=HEIGHT,width=WIDTH)
cannvas.pack()

baground_image=PhotoImage(file='image3.png')
baground=cannvas.create_image(0,0,image=baground_image,anchor=NW)

images=PhotoImage(file='moveimage.png')
myimage=cannvas.create_image(0,0,image=images,anchor=NW)

images_width=images.width()
images_height=images.height()

while True:
    coordinates=cannvas.coords(myimage)
    #print(coordinates)
    if coordinates[0]>=(WIDTH-images_width) or coordinates[0]<0:
        xvelocity= -xvelocity
    if coordinates[1]>=(HEIGHT-images_height) or coordinates[1]<0:
        yvelocity= -yvelocity
    cannvas.move(myimage,xvelocity,yvelocity)
    window.update()
    time.sleep(0.1)


window.mainloop()

END().................................................................


TITLE (HOW TO ANIMAT MULTIPLE OBJECTS IN PYTHON)

CODE
MANI BODY CODE
from tkinter import *
import time

from Ball import *

window= Tk()

WIDTH=500
HEIGHT=500

canvas=Canvas(window,width=WIDTH,height=HEIGHT)
canvas.pack()
volly_ball= Ball(canvas,0,0,100,8,4,'red')
tennis_ball= Ball(canvas,0,0,50,10,12,'black')
foot_ball= Ball(canvas,0,0,130,5,7,'blue')

while True:
    volly_ball.move()
    tennis_ball.move()
    foot_ball.move()
    window.update()
    time.sleep(0.01)
window.mainloop()

(IMPORT CLASS CODE)

class Ball:

    def __init__(self,canvas,x,y,diameter,xvelocity,yvelocity,color):
        self.canvas = canvas
        self.image = canvas.create_oval(x,y, diameter, diameter, fill=color)
        self.xvelocity = xvelocity
        self.yvelocity = yvelocity
    def move(self):
        coordinates=self.canvas.coords(self.image)
        print(coordinates)
        if coordinates[2]>=self.canvas.winfo_width() or coordinates[0]<0:
            self.xvelocity= -self.xvelocity
        if coordinates[3] >= self.canvas.winfo_width() or coordinates[1] < 0:
            self.yvelocity = -self.yvelocity
        self.canvas.move(self.image,self.xvelocity,self.yvelocity)



END().................................................................



