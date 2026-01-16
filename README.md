expenses = []

print("Select Expense Type")
print("1 Weekly")
print("2 Monthly")
print("3 Yearly")

period_choice = input("Enter choice : ")

if period_choice == "1":
    period = "Weekly"
elif period_choice == "2":
    period = "Monthly"
elif period_choice == "3":
    period = "Yearly"
else:
    print("Invalid choice")
    exit()

total_money = float(input("Enter total money you have : "))

while True:
    print("\n1 Add Expense")
    print("2 View Expenses")
    print("3 Category Wise Total")
    print("4 Total Expense & Balance")
    print("5 Delete Last Expense")
    print("6 Exit")

    choice = input("Enter your choice : ")

    if choice == "1":
        print("\nSelect Category")
        print("1 Food")
        print("2 Travel")
        print("3 Entertainment")
        print("4 Shopping")
        print("5 Other")

        cat_choice = input("Enter category number : ")

        if cat_choice == "1":
            category = "Food"
        elif cat_choice == "2":
            category = "Travel"
        elif cat_choice == "3":
            category = "Entertainment"
        elif cat_choice == "4":
            category = "Shopping"
        elif cat_choice == "5":
            category = input("Enter custom category : ")
        else:
            print("Invalid category")
            continue

        amount = float(input("Enter amount : "))
        expense_date = input("Enter date (DD-MM-YYYY) : ")

        expense = {
            "amount": amount,
            "category": category,
            "date": expense_date
        }

        expenses.append(expense)
        print("Expense added successfully")

    elif choice == "2":
        if expenses == []:
            print("No expenses found")
        else:
            for e in expenses:
                print("Date:", e["date"], "Amount:", e["amount"], "Category:", e["category"])

    elif choice == "3":
        food = 0
        travel = 0
        entertainment = 0
        shopping = 0
        other = 0

        for e in expenses:
            if e["category"] == "Food":
                food = food + e["amount"]
            elif e["category"] == "Travel":
                travel = travel + e["amount"]
            elif e["category"] == "Entertainment":
                entertainment = entertainment + e["amount"]
            elif e["category"] == "Shopping":
                shopping = shopping + e["amount"]
            else:
                other = other + e["amount"]

        print("Food Total:", food)
        print("Travel Total:", travel)
        print("Entertainment Total:", entertainment)
        print("Shopping Total:", shopping)
        print("Other Total:", other)

    elif choice == "4":
        total = 0
        for e in expenses:
            total = total + e["amount"]

        balance = total_money - total

        print(period, "Expense Total:", total)
        print("Remaining Balance:", balance)

    elif choice == "5":
        if expenses == []:
            print("No expense to delete")
        else:
            expenses.pop()
            print("Last expense deleted")

    elif choice == "6":
        print("Thank you")
        break

    else:
        print("Invalid choice") 
