# Lance Craig & Steven Sanchez
# Midterm project
"""The program should ask the user its name, age, location, social security number, contact phone number
and referring number. The program should then save those information to a text file(research) and bring up
a new window with  symptoms: cough, runny nose, sore throat, fever, diarrhea, fatigue, shortness or
breath, joint pain and other. The program should accept the person's weight, height, calculate BMI,
temperature, hypertension, pulse and saturation rates. Based on those values and jf three or more
symptom is present schedule them for a pcr test."""

from tkinter import *
import tkinter.messagebox as tsmg
import math


# ======================================================================================================================


"""This is the function that creates the text files saving all the data inputted by the user to it"""


def save_info():
    firstname_info = firstname.get()
    lastname_info = lastname.get()
    age_info = age.get()
    location_info = location.get()
    ssn_info = ssn.get()
    connum_info = connum.get()
    rn_info = rn.get()
    print("First Name: ", firstname_info, "\nLast Name: ", lastname_info, "\nAge: ", age_info,
          "\nLocation: ", location_info, "\nSocial Security Number: ", ssn_info, "\nContact Number: ", connum_info,
          "\nReferring Number: ", rn_info)

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
    print("User ", firstname_info, " has been registered successfully.")

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
    Button(window, text='Show', command=win2).grid(row=9, ipadx=20, sticky=W, pady=4)


# ======================================================================================================================


def win2():
    def calculate():

        weight = float(lbs.get())
        feets = float(feet.get())
        inchess = float(inches.get())
        height = (feets * 12) + inchess

        bmi = float((weight * 703) / (height ** 2))
        res.set(round(bmi, 2))

        if (bmi < 16):
            tsmg.showinfo("Health Status", "Severely Underweight")

        elif (bmi >= 16 and bmi < 18.5):
            tsmg.showinfo("Health Status", "You Are Underweight")

        elif (bmi >= 18.5 and bmi < 25):
            tsmg.showinfo("Health Status", "You Are Healthy")

        elif (bmi >= 25 and bmi < 30):
            tsmg.showinfo("Health Status", "You Are Overweight")

        elif (bmi > 30):
            tsmg.showinfo("Health Status", "Severely Overweight")

    window = Toplevel()
    window.geometry('500x600')
    window.config(background='gray73')
    label = Label(window, fg='firebrick1', bg='gray5', text="Health Calculator", font=("Arial", 10, 'bold'))
    label.pack(side=TOP)
    label2 = Label(window, fg='gray5', bg='plum3', text="Calculate your BMI", font=("Arial", 10, 'bold'))
    label2.place(x=12, y=40)

    feet = StringVar()
    inches = StringVar()
    lbs = StringVar()
    res = StringVar()

    height_text = Label(window, text='Your \n Height: ', fg='gray5', bg='gray73')
    height_text.place(x=12, y=70)
    cms_text = Label(window, text=' ft', fg='gray5', bg='gray73')
    cms_text.place(x=134, y=85)
    dash_text = Label(window, text=' / ', fg='gray5', bg='gray73')
    dash_text.place(x=155, y=85)
    ins_text = Label(window, text=' ins', fg='gray5', bg='gray73')
    ins_text.place(x=240, y=85)
    weight_text = Label(window, fg='gray5', bg='gray73', text="Your \n Weight: ")
    weight_text.place(x=12, y=120)
    lbs_text = Label(window, text=' lbs', fg='gray5', bg='gray73')
    lbs_text.place(x=134, y=135)
    compute = Label(window, fg='gray5', bg='gray73', text="Compute BMI: ")
    compute.place(x=12, y=165)

    foot_text = Entry(window, textvariable=feet, width="10")
    foot_text.place(x=70, y=85)
    inches_text = Entry(window, textvariable=inches, width="10")
    inches_text.place(x=175, y=85)
    weight_text = Entry(window, textvariable=lbs, width="10")
    weight_text.place(x=70, y=135)
    result = Entry(window, textvariable=res, width="20")
    result.place(x=100, y=165)
    calc_butn = Button(window, text="Calculate", width="8", command=calculate)
    calc_butn.place(x=235, y=160)


# ======================================================================================================================


    p = StringVar()

    line_text = Label(window, text='===========================================================', fg='gray5',
                      bg='gray73')
    line_text.place(x=12, y=190)
    pulse_text = Label(window, text='Your Pulse: ', fg='gray5', bg='gray73')
    pulse_text.place(x=12, y=220)
    pls_text = Entry(window, textvariable=p, width="10")
    pls_text.place(x=80, y=220)
    check_butn = Button(window, text="Check ", width="5", command='calcpulse')
    check_butn.place(x=155, y=220)


# ======================================================================================================================


    def tempcalc():

        temp = float(t.get())

        ctemp = float(temp)

        if (ctemp < 36):
            tsmg.showinfo("Temperature Status", "Your body temperature is below normal. "
                                                "\n Please get checked for Hypothermia!")

        elif (ctemp >= 36 and ctemp < 37.5):
            tsmg.showinfo("Temperature Status", "Your body temperature is normal.")

        elif (ctemp > 38):
            tsmg.showinfo("Temperature Status", "Your body temperature is above normal. \n You have a fever!")

    t = StringVar()

    temperature_text = Label(window, text='Your Temperature: ', fg='gray5', bg='gray73')
    temperature_text.place(x=12, y=260)
    temp_text = Entry(window, textvariable=t, width="10")
    temp_text.place(x=120, y=260)
    c_text = Label(window, text='°c ', fg='gray5', bg='gray73')
    c_text.place(x=185, y=260)
    check_butn = Button(window, text="Check ", width="5", command=tempcalc)
    check_butn.place(x=210, y=260)


# ======================================================================================================================


    def hypcalc():
        syst = float(lic.get())
        diast = float(dia.get())

        hysys = float(syst)
        hydia = float(diast)

        if (hysys < 120 and hydia < 80):
            tsmg.showinfo("Hypertension Status", "Systolic and Diastolic levels are normal.")

        elif (hysys >= 120 and hysys <= 139 and hydia >= 80 and hydia <= 89):
            tsmg.showinfo("Hypertension Status", "You have prehypertension and are at risk of"
                                                 "\n getting stage 1 hypertension!")

        elif (hysys >= 140 and hysys <= 159 and hydia >= 90 and hydia <= 99):
            tsmg.showinfo("Hypertension Status", "You have stage 1 hypertension!"
                                                 "\n Please seek medical assistance")

        elif (hysys >= 160 and hydia >= 100):
            tsmg.showinfo("Hypertension Status", "You have stage 2 hypertension!"
                                                 "\n Please seek medical assistance")

    lic = StringVar()
    dia = StringVar()

    hypertension_text = Label(window, text='Your Hypertension Level: ', fg='gray5', bg='gray73')
    hypertension_text.place(x=12, y=300)

    hyten_text = Label(window, text='Systolic: ', fg='gray5', bg='gray73')
    hyten_text.place(x=12, y=320)
    hyp_text = Entry(window, textvariable=lic, width="10")
    hyp_text.place(x=65, y=320)
    sys_text = Label(window, text='mm Hg: ', fg='gray5', bg='gray73')
    sys_text.place(x=135, y=320)

    dias_text = Label(window, text='Diastolic: ', fg='gray5', bg='gray73')
    dias_text.place(x=200, y=320)
    dia_text = Entry(window, textvariable=dia, width="10")
    dia_text.place(x=260, y=320)
    di_text = Label(window, text='mm Hg: ', fg='gray5', bg='gray73')
    di_text.place(x=330, y=320)
    check_butn2 = Button(window, text="Check ", width="5", command=hypcalc)
    check_butn2.place(x=390, y=320)


# ======================================================================================================================


    line2_text = Label(window, text='===========================================================', fg='gray5',
                      bg='gray73')
    line2_text.place(x=12, y=350)

    def spoonlvl():
        spoon = float(spo.get())

        sppon = float(spoon)

        if (sppon < 95):
            tsmg.showinfo("Saturation Rates", "Your oxygen levels are below normal(Hypoxemia)!"
                          "\n The lower the oxygen level, the more severe the hypoxemia."
                          "\n This can lead to complications in body tissue and organs."
                          "\n Please seek medical assistance! Unless Your Oxygen Level is norma due"
                          " to chronic lung conditions.")

        elif (sppon >= 95 and sppon <= 100):
            tsmg.showinfo("Saturation Rates", "Your oxygen levels are normal."
                          "\n Unless lung conditions cause your normal oxygen level to be lower.")

        elif (sppon >100):
            tsmg.showinfo("Saturation Rates", "Your oxygen levels are too high."
                          "\n You may be in danger, please seek immediate attention!")

    def hilvl():
        hi = float(pao.get())

        hibb = float(hi)

        if (hibb < 80):
            tsmg.showinfo("Saturation Rates", "Your oxygen levels are below normal(Hypoxemia)!"
                          "\n The lower the oxygen level, the more severe the hypoxemia."
                          "\n This can lead to complications in body tissue and organs."
                          "\n Please seek medical assistance! Unless Your Oxygen Level is norma due"
                          " to chronic lung conditions.")

        elif (hibb >= 80 and hibb <= 100):
            tsmg.showinfo("Saturation Rates", "Your oxygen levels are normal."
                          "\n Unless lung conditions cause your normal oxygen level to be lower.")

        elif (hibb >100):
            tsmg.showinfo("Saturation Rates", "Your oxygen levels are too high."
                          "\n You may be in danger, please seek immediate attention!")




    spo = StringVar()
    pao = StringVar()

    label3 = Label(window, fg='gray5', bg='plum3', text="Saturation Rates: ", font=("Arial", 10, 'bold'))
    label3.place(x=12, y=380)

    sp02_text = Label(window, text='SpO2 Level: ', fg='gray5', bg='gray73')
    sp02_text.place(x=12, y=410)
    sp022_text = Entry(window, textvariable=spo, width="10")
    sp022_text.place(x=85, y=410)
    sp023_text = Label(window, text='% ', fg='gray5', bg='gray73')
    sp023_text.place(x=155, y=410)
    check_butn3 = Button(window, text="Check ", width="5", command=spoonlvl)
    check_butn3.place(x=180, y=410)

    or_text = Label(window, text='or ', fg='gray5', bg='gray73')
    or_text.place(x=12, y=440)

    pa02_text = Label(window, text='PaO2 Level: ', fg='gray5', bg='gray73')
    pa02_text.place(x=12, y=470)
    pa022_text = Entry(window, textvariable=pao, width="10")
    pa022_text.place(x=85, y=470)
    pa023_text = Label(window, text='mm Hg ', fg='gray5', bg='gray73')
    pa023_text.place(x=155, y=470)
    check_butn4 = Button(window, text="Check ", width="5", command=hilvl)
    check_butn4.place(x=210, y=470)


# ======================================================================================================================


    label4 = Label(window, fg='gray5', bg='plum3', text="Book An Appointment: ", font=("Arial", 10, 'bold'))
    label4.place(x=12, y=500)

    book_text = Label(window, text='Would You like to book a Doctor appointment?', fg='gray5', bg='gray73')
    book_text.place(x=12, y=530)
    bookbtn = Button(window, text="Book ", width="5", command=win3)
    bookbtn.place(x=270, y=530)

    quitu_text = Label(window, text='Would You like to quit this window?', fg='gray5', bg='gray73')
    quitu_text.place(x=12, y=560)
    quitman_btn = Button(window, text="Quit ", width="5", command=quit)
    quitman_btn.place(x=210, y=560)


def win3():

    def book_info():
        hospital_info = hosp.get()
        district_info = dist.get()
        time_info = tie.get()
        month_info = mon.get()
        day_info = day.get()
        year_info = yr.get()
        print("Appointment Info: ", "\nHospital: ", hospital_info, "\nDistrict: ", district_info, "\nTime: ", time_info,
              "\nMonth: ", month_info, "\nDay: ", day_info, "\nYear: ", year_info)

        """This allows the data to be written to the file"""

        file = open("appointment.txt", "w")
        file.write(hospital_info)
        file.write(district_info)
        file.write(time_info)
        file.write(month_info)
        file.write(day_info)
        file.write(year_info)
        file.close()
        print(" Appointment ", " has been registered successfully")

        hos_text.delete(0, END)
        dis_text.delete(0, END)
        tim_text.delete(0, END)
        mon_text.delete(0, END)
        day_text.delete(0, END)
        year_text.delete(0, END)


    window = Toplevel()
    window.geometry('300x350')
    window.config(background='gray73')

    label5 = Label(window, fg='gray5', bg='plum3', text="Please Fill Out The Following: ", font=("Arial", 10, 'bold'))
    label5.place(x=12, y=20)

    dist = StringVar()
    hosp = StringVar()
    tie = StringVar()
    day = StringVar()
    mon = StringVar()
    yr = StringVar()

    hospital_text = Label(window, text="Hospital: ", fg='gray5', bg='gray73')
    hospital_text.place(x=12, y=70)
    hos_text = Entry(window, textvariable=hosp, width="20")
    hos_text.place(x=68, y=70)
    district_text = Label(window, text="District: ", fg='gray5', bg='gray73')
    district_text.place(x=12, y=110)
    dis_text = Entry(window, textvariable=dist, width="20")
    dis_text.place(x=60, y=110)
    time_text = Label(window, text="Time: ", fg='gray5', bg='gray73')
    time_text.place(x=12, y=150)
    tim_text = Entry(window, textvariable=tie, width="20")
    tim_text.place(x=50, y=150)
    date_text = Label(window, text="Date: ", fg='gray5', bg='gray73')
    date_text.place(x=12, y=190)
    mon_text = Entry(window, textvariable=mon, width="3")
    mon_text.place(x=48, y=190)
    mo_text = Label(window, text="Mo ", fg='gray5', bg='gray73')
    mo_text.place(x=72, y=190)
    day_text = Entry(window, textvariable=day, width="3")
    day_text.place(x=100, y=190)
    day2_text = Label(window, text="Ds ", fg='gray5', bg='gray73')
    day2_text.place(x=125, y=190)
    year_text = Entry(window, textvariable=yr, width="5")
    year_text.place(x=150, y=190)
    yr_text = Label(window, text="Yr ", fg='gray5', bg='gray73')
    yr_text.place(x=187, y=190)

    buk_butn = Button(window, text="Book Appointment ", width="20", command=book_info)
    buk_butn.place(x=12, y=230)

    label5 = Label(window, fg='gray5', bg='plum3', text="Exit Appointment Scheduler? ", font=("Arial", 10, 'bold'))
    label5.place(x=12, y=275)

    exit_btn = Button(window, text="Exit ", width="10", command=window.quit)
    exit_btn.place(x=12, y=310)


# ======================================================================================================================


win_butt = Button(text="Symptoms", width="10", height="1", command=win1, fg="red", bg="gray5")
win_butt.place(x=330, y=180)
calc_butt = Button(text="Health Calculator", width="20", height="1", command=win2, fg="red", bg="gray5")
calc_butt.place(x=300, y=270)

C.pack()
mainloop()
