accounts = {}

def create_account():
    acc_no = input("Enter account number: ")

    if acc_no in accounts:
        print("Account already exists!")
        return

    name = input("Enter account holder name: ")
    balance = float(input("Enter initial deposit: ₹"))

    accounts[acc_no] = {
        "name": name,
        "balance": balance
    }

    print("✅ Account created successfully!")


def deposit():
    acc_no = input("Enter account number: ")

    if acc_no not in accounts:
        print("❌ Account not found!")
        return

    amount = float(input("Enter deposit amount: ₹"))

    if amount <= 0:
        print("❌ Invalid amount!")
        return

    accounts[acc_no]["balance"] += amount
    print("✅ Amount deposited successfully!")


def withdraw():
    acc_no = input("Enter account number: ")

    if acc_no not in accounts:
        print("❌ Account not found!")
        return

    amount = float(input("Enter withdrawal amount: ₹"))

    if amount <= 0:
        print("❌ Invalid amount!")
    elif amount > accounts[acc_no]["balance"]:
        print("❌ Insufficient balance!")
    else:
        accounts[acc_no]["balance"] -= amount
        print("✅ Withdrawal successful!")


def check_balance():
    acc_no = input("Enter account number: ")

    if acc_no not in accounts:
        print("❌ Account not found!")
        return

    print("Account Holder:", accounts[acc_no]["name"])
    print("Balance: ₹", accounts[acc_no]["balance"])


def account_details():
    acc_no = input("Enter account number: ")

    if acc_no not in accounts:
        print("❌ Account not found!")
        return

    print("\n--- Account Details ---")
    print("Account Number:", acc_no)
    print("Account Holder:", accounts[acc_no]["name"])
    print("Balance: ₹", accounts[acc_no]["balance"])


while True:
    print("\n========== BANK SYSTEM ==========")
    print("1. Create Account")
    print("2. Deposit Money")
    print("3. Withdraw Money")
    print("4. Check Balance")
    print("5. Account Details")
    print("6. Exit")

    choice = input("Enter your choice: ")

    if choice == "1":
        create_account()
    elif choice == "2":
        deposit()
    elif choice == "3":
        withdraw()
    elif choice == "4":
        check_balance()
    elif choice == "5":
        account_details()
    elif choice == "6":
        print("Thank you for using the Bank System! 👋")
        break
    else:
        print("❌ Invalid choice!")
