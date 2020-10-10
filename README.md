# covidchecker
# midterm project

"""The program should ask the user its name, age, location, social security number, contact phone number
and referring number. The program should then save those information to a textfile(research) and bring up
a new window with  symptoms: cough, runny nose, sore throat, fever, diarrhea, fatigue, shortness or
breath, joint pain and other. The program should accept the person's weight, height, calculate BMI,
temperature, hypertension, pulse and saturation rates. Based on those values and jf three or more
symptom is present schedule them for a pcr test."""

from tkinter import *
# from tkinter import messagebox

# ======================================================================================================================


def save_info():
    firstname_info = firstname.get()
    lastname_info = lastname.get()
    age_info = age.get()
    age_info = str(age_info)
    location_info = location.get()
    ssn_info = ssn.get()
    ssn_info = str(ssn_info)
    connum_info = connum.get()
    connum_info = str(connum_info)
    rn_info = rn.get()
    rn_info = str(rn_info)
    print(firstname_info, lastname_info, age_info, location_info, ssn_info, connum_info, rn_info)

    file = open("user.txt", "w")
    file.write(firstname_info)
    file.write(lastname_info)
    file.write(age_info)
    file.write(location_info)
    file.write(ssn_info)
    file.write(connum_info)
    file.write(rn_info)
    file.close()
    print(" User ", firstname_info, " has been registered successfully")

    firstname_entry.delete(0, END)
    lastname_entry.delete(0, END)
    age_entry.delete(0, END)
    location_entry.delete(0, END)
    ssn_entry.delete(0, END)
    connum_entry.delete(0, END)
    rn_entry.delete(0, END)


# ======================================================================================================================


screen = Tk()
screen.geometry("500x500")
screen.title("Covid Checker")
label = Label(text="Registration Form", fg='magenta4', width="500", height="3", font=("Copperplate Gothic", 12, 'bold'))
label.pack()


# ======================================================================================================================

C = Canvas( height=300, width=100)
filename = PhotoImage(file="C:\\Users\\Dee\\Desktop\\Steven\\midtermpython\\virus.png")
background_label = Label( image=filename)
background_label.place(x=0, y=0, relwidth=1, relheight=1)


# ======================================================================================================================



firstname_text = Label(text="Firstname * ", )
lastname_text = Label(text="Lastname * ", )
age_text = Label(text="Age * ", )
location_text = Label(text="location * ", )
ssn_text = Label(text="Social Security Number * ", )
connum_text = Label(text="Contact Phone Number * ", )
rn_text = Label(text="Referring Number * ", )
firstname_text.place(x=15, y=70)
lastname_text.place(x=15, y=120)
age_text.place(x=15, y=170)
location_text.place(x=15, y=220)
ssn_text.place(x=15, y=270)
connum_text.place(x=15, y=320)
rn_text.place(x=15, y=370)


# ======================================================================================================================



firstname = StringVar()
lastname = StringVar()
age = IntVar()
location = StringVar()
ssn = IntVar()
connum = IntVar()
rn = IntVar()


# ======================================================================================================================


firstname_entry = Entry(textvariable=firstname, width="30")
lastname_entry = Entry(textvariable=lastname, width="30")
age_entry = Entry(textvariable=age, width="30")
location_entry = Entry(textvariable=location, width="30")
ssn_entry = Entry(textvariable=ssn, width="30")
connum_entry = Entry(textvariable=connum, width="30")
rn_entry = Entry(textvariable=rn, width="30")


# ======================================================================================================================



firstname_entry.place(x=15, y=90)
lastname_entry.place(x=15, y=140)
age_entry.place(x=15, y=190)
location_entry.place(x=15, y=240)
ssn_entry.place(x=15, y=290)
connum_entry.place(x=15, y=340)
rn_entry.place(x=15, y=390)


# ======================================================================================================================



register = Button(screen, text="Register", width="20", height="2", command=save_info, bg="grey")
register.place(x=15, y=420)


C.pack()
mainloop()
