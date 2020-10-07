# covidchecker
# midterm project

"""The program should ask the user its name, age, location, social security number, contact phone number
and referring number. The program should then save those information to a textfile(research) and bring up
a new window with  symptoms: cough, runny nose, sore throat, fever, diarrhea, fatigue, shortness or
breath, joint pain and other. The program should accept the person's weight, height, calculate BMI,
temperature, hypertension, pulse and saturation rates. Based on those values and jf three or more
symptom is present schedule them for a pcr test."""

from tkinter import *
import tkinter as tk

# ======================================================================================================================

class Win1:
    def __init__(self, master):
        self.master = master
        self.master.geometry("500x400")
        self.frame = tk.Frame(self.master)
        self.master.title("Covid Checker")
        self.master.label = Label(root, text="Sign Up", fg='magenta4', bg='gray5', font=("Copperplate Gothic Bold",
                                                                                         26, 'bold'))
        self.master.label.pack()
        self.master.config(background='gray5')

# ======================================================================================================================

        self.master.label = Label(root, text="Firstname", fg='magenta4', bg='gray5', font=("Copperplate Gothic Bold",
                                                                                              14, 'bold'))
        self.master.label.place(x=20, y=60)
        self.master.label = Label(root, text="Lastname", fg='magenta4', bg='gray5', font=("Copperplate Gothic Bold",
                                                                                14, 'bold'))
        self.master.label.place(x=20, y=100)
        self.master.label = Label(root, text="Age", fg='magenta4', bg='gray5', font=("Copperplate Gothic Bold",
                                                                                           14, 'bold'))
        self.master.label.place(x=20, y=140)
        self.master.label = Label(root, text="Location", fg='magenta4', bg='gray5', font=("Copperplate Gothic Bold",
                                                                                           14, 'bold'))
        self.master.label.place(x=20, y=180)
        self.master.label = Label(root, text="Social Security Number", fg='magenta4', bg='gray5', font=("Copperplate Gothic Bold",
                                                                                           14, 'bold'))
        self.master.label.place(x=20, y=220)
        self.master.label = Label(root, text="Contact Phone Number", fg='magenta4', bg='gray5', font=("Copperplate Gothic Bold",
                                                                                           14, 'bold'))
        self.master.label.place(x=20, y=260)
        self.master.label = Label(root, text="Referring Number", fg='magenta4', bg='gray5', font=("Copperplate Gothic Bold",
                                                                                           14, 'bold'))
        self.master.label.place(x=20, y=300)

# ======================================================================================================================
# these are all the entry buttons
        self.master.firstname_entry = Entry(textvariable="firstname")
        self.master.firstname = StringVar()
        self.master.firstname_entry.place(x=160, y=65)
        self.master.lastname_entry = Entry(textvariable="lastname")
        self.master.lastname = StringVar()
        self.master.lastname_entry.place(x=160, y=105)
        self.master.age_entry = Entry(textvariable="age")
        self.master.age = IntVar()
        self.master.age_entry.place(x=85, y=145)
        self.master.location_entry = Entry(textvariable="location")
        self.master.location = StringVar()
        self.master.location_entry.place(x=155, y=185)
        self.master.ssn_entry = Entry(textvariable="ssn")
        self.master.ssn = IntVar()
        self.master.ssn_entry.place(x=320, y=225)
        self.master.cpn_entry = Entry(textvariable="cpn")
        self.master.cpn = IntVar()
        self.master.cpn_entry.place(x=320, y=265)
        self.master.rn_entry = Entry(textvariable="rn")
        self.master.rn = IntVar()
        self.master.rn_entry.place(x=250, y=305)
# this is the submit button that calls the save_info fucntion in order for the information to be entered into a file
        self.master.submit = Button(text="Submit", fg='black', bg='red', font=("Copperplate Gothic Bold",14, 'bold'),
                                    width="7", height="1", command="save_info")
        self.master.submit.place(x=20, y=330)

# ======================================================================================================================
# the function that saves all the entries into a file
    def save_info(self):
        self.master.firstname_info = firstname.get()
        self.master.lastname_info = lastname.get()
        self.master.age_info = age.get()
        self.master.age_info = str(age_info) # this converts the integer into a string in order for it to be written into the file
        self.master.location_info = location.get()
        self.master.ssn_info = ssn.get()
        self.master.ssn_info = str(ssn_info)
        self.master.cpn_info = cpn.get()
        self.master.cpn_info = str(cpn_info)
        self.master.rn_info = rn.get()
        self.master.rn_info = str(rn_info)
        print(firstname_info, lastname_info, age_info, location_info, ssn_info, cpn_info, rn_info)

        self.master.file = open("info.txt", "w")
        self.master.file.write(firstname_info)
        self.master.file.write(firstname_info)
        self.master.file.write(age_info)
        self.master.file.write(location_info)
        self.master.file.write(ssn_info)
        self.master.file.write(cpn_info)
        self.master.file.write(rn_info)
        self.master.file.close()

# ======================================================================================================================

    def butnew(self, text, number, _class):
            tk.Button(self.frame, text=text, command=lambda: self.new_window(number, _class)).pack()

    def new_window(self, number, _class):
            self.new = tk.Toplevel(self.master)
            _class(self.new, number)

# ======================================================================================================================

root = tk.Tk()
app = Win1(root)
root.mainloop()
