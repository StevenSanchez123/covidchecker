# covidchecker
midterm project

from tkinter import *
import tkinter as tk


class Win1:
    def __init__(self, master):
        self.master = master
        self.master.geometry("400x400")
        self.frame = tk.Frame(self.master)
        self.master.title("Covid Checker")
        self.master.label = Label(root, text="Sign Up", fg='magenta4', bg='gray5', font=("Copperplate Gothic Bold",
                                                                                         26, 'bold'))
        self.master.label.pack(side=TOP)
        self.master.config(background='gray5')
        self.butnew("Most Common symptoms", "2", Win2)
        self.butnew("Less Common Symptoms", "3", Win3)
        self.butnew("Serious Symptoms", "4", Win4)
        self.frame.pack()

    def butnew(self, text, number, _class):
        tk.Button(self.frame, text=text, command=lambda: self.new_window(number, _class)).pack()

    def new_window(self, number, _class):
        self.new = tk.Toplevel(self.master)
        _class(self.new, number)


class Win2:
    def __init__(self, master, number):
        self.master = master
        self.master.geometry("400x400+200+200")
        self.frame = tk.Frame(self.master)
        self.quit = tk.Button(self.frame, text=f"Exit", command=self.close_window)
        self.quit.pack()
        self.frame.pack()

    def close_window(self):
        self.master.destroy()


class Win3:
    def __init__(self, master, number):
        self.master = master
        self.master.geometry("400x400+200+200")
        self.frame = tk.Frame(self.master)
        self.quit = tk.Button(self.frame, text=f"Exit", command=self.close_window)
        self.quit.pack()
        self.label = tk.Label(self.frame, text="fever""dry cough""tiredness")
        self.label.pack()
        self.frame.pack()

    def close_window(self):
        self.master.destroy()

class Win4:
    def __init__(self, master, number):
        self.master = master
        self.master.geometry("400x400+200+200")
        self.frame = tk.Frame(self.master)
        self.quit = tk.Button(self.frame, text=f"Exit", command=self.close_window)
        self.quit.pack()
        self.label = tk.Label(self.frame, text="THIS IS ONLY IN THE THIRD WINDOW")
        self.label.pack()
        self.frame.pack()

    def close_window(self):
        self.master.destroy()





root = tk.Tk()
app = Win1(root)
root.mainloop()
