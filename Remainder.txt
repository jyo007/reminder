import datetime
import time

def dvalidation(inputDate):
    day, month, year = inputDate.split('/')
    isValidDate = True
    try:
        datetime.datetime(int(year), int(month), int(day))
    except ValueError:
        isValidDate = False
    if (isValidDate):
        return 1;
    else:
        return 0;

Dict = {}  # We have declared a dictionary to store birthday.
# Run loop till the user wants.
while True:
    i = 1;
    up=[]
    print("_____Remainder_____\n")
    print("1.Update reminder")
    print("2.Add Remainder")
    print("3.Delete Remainder")
    print("4.Show all reminders")
    print("5-Check todays remainder")
    print("6.Exit")
    choice = int(input("Enter the choice\n"))

    if choice == 1:
        if len(Dict) == 0:  # If no data in dictionary
            print("Nothing to Update")
        else:
            print("reminder List")

            for x, y in Dict.items():
                print(i, "-", x, y)
                up.append(x)
                i = i + 1;
            r = int(input("Which reminder do you need to update?(choose Sl no)\n"))
            Dict.pop(up[r-1])
            name = str(input('What is the updated  message?'))
            date = input("Enter the date in format 'dd/mm/yyyy' : ")
            v = dvalidation(date)
            if (v == 1):
                Dict[name] = date
                print("Remainder Added")
            else:
                print("Input date is not valid..")
            print("Remainder Updated")

    elif choice == 2:
        name = str(input('What you need to remainded?'))

        date = input("Enter the date in format 'dd/mm/yyyy' : ")
        v=dvalidation(date)
        if (v==1):
            Dict[name] = date
            print("Remainder Added")
        else:
            print("Input date is not valid..")

    elif choice == 3:
        if len(Dict) == 0:  # If no data in dictionary
            print("Nothing to Update")
        else:
            print("reminder List")

            for x, y in Dict.items():
                print(i, "-", x, y)
                up.append(x)
                i = i + 1;
            r = int(input("Which reminder do you need to Delete?(choose Sl no)\n"))
            Dict.pop(up[r-1])
            print("Reminder Deleted Successfully")
    elif choice == 4:
        if len(Dict) == 0:  # If no data in dictionary
            print("Nothing to show")
        else:
            print("reminder List")
            for x, y in Dict.items():
             print(i, "-", x, y)
             i = i +1
    elif choice == 5:
        crdate = time.strftime("%d/%m/%Y")
        print(crdate)
        for x,y in Dict.items():
            if y==crdate:
                print("*****reminder****\n")
                print(x)
            else:
               print("No reminders today")



    elif choice == 6:  # close program
        print("======Exiting program========")
        break
    else:  # if he has chosen none of above input plese ask him to chose valid option
        print("Choose a valid option")


