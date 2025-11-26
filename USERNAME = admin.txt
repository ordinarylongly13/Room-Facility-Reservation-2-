USERNAME = "admin"
PASSWORD = "1234"

labs = {
    1: {"status": "AVAILABLE", "faculty": "", "date": ""},
    2: {"status": "AVAILABLE", "faculty": "", "date": ""},
    3: {"status": "AVAILABLE", "faculty": "", "date": ""}
}

print("=================================")
print("   COMPUTER LAB LOG-IN SYSTEM")
print("=================================")

while True:
    user = input("Username: ")
    pw = input("Password: ")

    if user == USERNAME and pw == PASSWORD:
        print("\nLogin Successful!\n")
        break
    else:
        print("Invalid Username or Password! Try again.\n")

while True:
    print("\n================================")
    print("  COMPUTER LABORATORY RESERVATION")
    print("==================================")
    print("AVAILABLE COMLAB:")
    print("COMLAB 1")
    print("COMLAB 2")
    print("COMLAB 3")
    print("\n1. RESERVE LAB")
    print("2. VIEW RESERVATION")
    print("3. CANCEL RESERVATION")
    print("4. EXIT")
    
    choice = input("\nSelect option (1-4): ")

    if choice == "1":
        print("\n----- RESERVE LAB -----")
        faculty = input("Faculty Name: ")
        lab_num = int(input("LAB (1-3): "))
        date = input("Date (MM/DD/YYYY): ")

        if labs[lab_num]["status"] == "AVAILABLE":
            labs[lab_num].update({"status": "RESERVED", "faculty": faculty, "date": date})
            print(f"\nYou successfully reserved COMLAB {lab_num} on {date}.")
        else:
            print("\nSORRY! This Lab is already RESERVED.")

        input("\nPress ENTER to return to dashboard...")

    elif choice == "2":
        print("\n----- LAB STATUS -----")
        print("LAB | STATUS     | DATE")
        print("---------------------------")
        for lab_num, info in labs.items():
            print(f"{lab_num}   | {info['status']}  | {info['date']}")
        input("\nPress ENTER to return...")

    elif choice == "3":
        print("\n----- CANCEL RESERVATION -----")
        lab_num = int(input("Enter LAB (1-3): "))

        if labs[lab_num]["status"] == "RESERVED":
            labs[lab_num] = {"status": "AVAILABLE", "faculty": "", "date": ""}
            print(f"\nYou successfully cancelled COMLAB {lab_num}.")
        else:
            print("\nCANNOT CANCEL! No reservation found in this lab.")

        input("\nPress ENTER to return...")

    elif choice == "4":
        print("\nThank you for using the system! Goodbye!")
        break

    else:
        print("\nInvalid choice! Please try again.")