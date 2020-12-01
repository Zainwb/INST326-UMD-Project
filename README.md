# INST326-UMD-Project
quiz generator software 
from tkinter import *
from tkinter import messagebox as mb


'''We have not created question file yet onece we create the questions we use the file in open file 
'''
root = Tk()
root.size("800x500")
root.title("Quiz")
with open('quiz.txt') as f:
   
qes = (obj['ques'])
options = (obj['options'])
a = (obj['ans'])

class Quiz:
    def __init__(self):
        self.qn = 0
        self.ques = self.question(self.qn)
        self.opt_selected = IntVar()
        self.opts = self.radiobtns()
        self.display_options(self.qn)
        self.buttons()
        self.correct = 0

    def question(self, qn):
        t = Label(root, text="Quiz in Python Programming", width=50, bg="red", fg="green", font=("times", 20, "bold"))
        t.place(x=0, y=2)
        qn = Label(root, text=q[qn], width=60, font=("times", 16, "bold"), anchor="w")
        qn.place(x=70, y=100)
        return qn

    def radiobtns(self):
        val = 0
        b = []
        yp = 150
        while val < 4:
            btun = Radiobutton(root, text=" ", variable=self.opt_selected, value=val + 1, font=("times", 14))
            b.append(btn)
            btun.place(x=100, y=yp)
            val += 1
            yp += 40
        return b

    def display_options(self, qn):
        val = 0
        self.opt_selected.set(0)
        self.ques['text'] = q[qn]
        for op in options[qn]:
              self.opts[val]['text'] = op
              val += 1

    def buttons(self):
        nbutton = Button(root, text="Next",command=self.nextbtn, width=10,bg="green",fg="white",font=("times",16,"bold"))
        nbutton.place(x=200,y=380)
        quitbutton = Button(root, text="Quit", command=root.destroy,width=10,bg="red",fg="white", font=("times",16,"bold"))
        quitbutton.place(x=380,y=380)

    def check_answer(self, qn):
        if self.opt_selected.get() == a[qn]:
             return True

    def next_butten(self):
        if self.check_answer(self.qn):
            self.correct += 1
        self.qn += 1
        if self.qn == len(q):
            self.display_result()
        else:
            self.display_options(self.qn)       


    def display_result(self):
        score = int(self.correct / len(q) * 100)
        result = "Score: " + str(score) + "%"
        wc = len(q) - self.correct
        correct = "No. of correct answers: " + str(self.correct)
        wrong = "No. of wrong answers: " + str(wc)
        mb.showinfo("Result", "\n".join([result, correct, wrong]))



quiz=Quiz()
root.mainloop()



"""Importing random library to select random question from the available questions"""

import random

"""Creating a class to hold the questions along with the correct answer"""

class Ques:
    
    def __init__(self, ask, ans): #initialise function to assign values to its data members
        self.ask=ask
        self.ans=ans

"""A list that holds all the questions"""

questionbank= [
"Question 1:\na) 1\nb) 2\nb) 3\nc) d\n",
"Question 3:\na) 1\nb) 2\nb) 3\nc) d\n",
"Question 4:\na) 1\nb) 2\nb) 3\nc) d\n",

"""Create multiple Ques objects that holds a question and its correct answer.
We keep these class objects in a list
"""

Ques =[
Ques(questionbank[0],"a"),
Ques(questionbank[1],"b"),
Ques(questionbank[2],"c"),
Ques(questionbank[3],"d")
]

"""Define a fuction that keeps track of the marks of the user and picks questions at random from the available questions"""

def quiz(ques):
marks = 0
for item in random.sample(ques,k=3):
userAns = input(item.ask)
if userAns == item.ans:
marks = marks +1
print("Score: "+str(marks)+"/3")

quiz(ques)




