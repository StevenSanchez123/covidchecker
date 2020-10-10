# covidchecker
# midterm project

# Lance Craig & Steven Sanchez
# Midterm project
"""The program should ask the user its name, age, location, social security number, contact phone number
and referring number. The program should then save those information to a text file(research) and bring up
a new window with  symptoms: cough, runny nose, sore throat, fever, diarrhea, fatigue, shortness or
breath, joint pain and other. The program should accept the person's weight, height, calculate BMI,
temperature, hypertension, pulse and saturation rates. Based on those values and jf three or more
symptom is present schedule them for a pcr test."""

from tkinter import *

# from tkinter import messagebox


# ======================================================================================================================


"""This is the function that creates the text files saving all the data inputted by the user to it"""


def save_info():
    firstname_info = firstname.get()
    lastname_info = lastname.get()
    age_info = age.get()
    # age_info = str(age_info) (This allows the INTVAR to be converted into a string)
    location_info = location.get()
    ssn_info = ssn.get()
    # ssn_info = str(ssn_info) (This allows the INTVAR to be converted into a string)
    connum_info = connum.get()
    # connum_info = str(connum_info) (This allows the INTVAR to be converted into a string)
    rn_info = rn.get()
    # rn_info = str(rn_info) (This allows the INTVAR to be converted into a string)
    print(firstname_info, lastname_info, age_info, location_info, ssn_info, connum_info, rn_info)

    """This allows the data to be written to the file"""

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

# the window size along with the title for the window
screen = Tk()
screen.geometry("500x500")
screen.title("Covid Checker")

"""The heading doesn't want to show for some reason so i just removed it, placing it back will alter the program
shifting the labels and entry bars all over the place"""
# heading = Label(text="Registration Form", fg='magenta4', width="200", height="1", font=("Copperplate Gothic", 12,
# 'bold'))
# heading = Label(text = "Python Form", bg = "grey", fg = "black", width = "500", height = "3")
# heading.pack()


# ======================================================================================================================


"""This places an image as the window background"""
C = Canvas(height=500, width=500)
filename = PhotoImage(file="C:\\Users\\Dee\\Desktop\\Steven\\midtermpython\\virus.png")
background_label = Label(image=filename)
background_label.place(x=0, y=0, relwidth=1, relheight=1)

# ======================================================================================================================


"""This creates the labels for each of the data entries that will follow"""
firstname_text = Label(text=" Firstname ", )
lastname_text = Label(text=" Lastname ", )
age_text = Label(text=" Age ", )
check_text = Label(text=" Check Your Symptoms ", fg='red', bg='gray5', font=("Copperplate Gothic Bold", 12, 'bold'))
calc_text = Label(text=" Check Health Status ", fg='red', bg='gray5', font=("Copperplate Gothic Bold", 12, 'bold'))
location_text = Label(text=" Location ", )
ssn_text = Label(text=" Social Security Number ", )
connum_text = Label(text=" Contact Phone Number ", )
rn_text = Label(text=" Referring Number ", )
firstname_text.place(x=25, y=30)
lastname_text.place(x=25, y=90)
age_text.place(x=25, y=150)
check_text.place(x=250, y=150)
calc_text.place(x=250, y=240)
location_text.place(x=25, y=210)
ssn_text.place(x=25, y=270)
connum_text.place(x=25, y=330)
rn_text.place(x=25, y=390)

# ======================================================================================================================


"""Creating the in put variables for the entry data in order for them to be saved"""
firstname = StringVar()
lastname = StringVar()
age = StringVar()
location = StringVar()
ssn = StringVar()
connum = StringVar()
rn = StringVar()

# ======================================================================================================================


"""Creating the entry bars for the data to be input by the user"""
firstname_entry = Entry(textvariable=firstname, width="30")
lastname_entry = Entry(textvariable=lastname, width="30")
age_entry = Entry(textvariable=age, width="30")
location_entry = Entry(textvariable=location, width="30")
ssn_entry = Entry(textvariable=ssn, width="30")
connum_entry = Entry(textvariable=connum, width="30")
rn_entry = Entry(textvariable=rn, width="30")

# ======================================================================================================================


"""The entry placing"""
firstname_entry.place(x=25, y=60)
lastname_entry.place(x=25, y=120)
age_entry.place(x=25, y=180)
location_entry.place(x=25, y=240)
ssn_entry.place(x=25, y=300)
connum_entry.place(x=25, y=360)
rn_entry.place(x=25, y=420)

# ======================================================================================================================


"""The register button that inputs the data entered into a text file while erasing the data on the window"""
register = Button(screen, text="Register", width="10", height="1", command=save_info, bg="grey")
register.place(x=25, y=450)


# ======================================================================================================================


def win1():
    window = Toplevel()
    window.config(background='gray5')
    # label = Label(window, text="Symptoms")
    # label.pack()
    # print("fever: %d,\ncough: %d, \n%dheadaches: %d,\nrashes: %d,\nbreathing difficulties: %d,\nchest pains: %d,\nloss "
    # "of movement/speech: %d" % (var1.get(), var2.get(), var3.get(), var4.get(), var5.get(), var6.get(), var7.get()))

    Label(window, fg='magenta4', bg='gray5', font=("Arial", 8, 'bold'), text="List of covid symptoms. Select the ones "
                                                                             "you have:").grid(row=0, sticky=W)
    var1 = IntVar()
    Checkbutton(window, fg='magenta4', bg='gray5', text="Fever", variable=var1).grid(row=1, sticky=W)
    var2 = IntVar()
    Checkbutton(window, fg='magenta4', bg='gray5', text="Cough", variable=var2).grid(row=2, sticky=W)
    var3 = IntVar()
    Checkbutton(window, fg='magenta4', bg='gray5', text="Headaches", variable=var3).grid(row=3, sticky=W)
    var4 = IntVar()
    Checkbutton(window, fg='magenta4', bg='gray5', text="Rashes", variable=var4).grid(row=4, sticky=W)
    var5 = IntVar()
    Checkbutton(window, fg='magenta4', bg='gray5', text="Breathing difficulties", variable=var5).grid(row=5, sticky=W)
    var6 = IntVar()
    Checkbutton(window, fg='magenta4', bg='gray5', text="Chest pains", variable=var6).grid(row=6, sticky=W)
    var7 = IntVar()
    Checkbutton(window, fg='magenta4', bg='gray5', text="Loss of movement/speech", variable=var7).grid(row=7, sticky=W)
    # Button(text='Quit', command=quit).grid(row=8, sticky=W, pady=4)
    Button(window, text='Show', command=win1).grid(row=9, ipadx=20, sticky=W, pady=4)


# ======================================================================================================================


def win2():
    window = Toplevel()
    window.config(background='gray73')
    label = Label(window, fg='firebrick1', bg='gray5', text="Health Calculator", font=("Arial", 10, 'bold'))
    label.pack()



# ======================================================================================================================


win_butt = Button(text="Symptoms", width="10", height="1", command=win1, fg="red", bg="gray5")
win_butt.place(x=330, y=180)
calc_butt = Button(text="Health Calculator", width="20", height="1", command=win2, fg="red", bg="gray5")
calc_butt.place(x=300, y=270)

C.pack()
mainloop()

