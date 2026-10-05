# Budget_Tracker_Project-1
This tracks incomes and expenses and displays a summary

**Course:** ITP 100 Software Design and Logic  
**Author:** Raheem Reid  
**Deliverable:** Algorithm Design (IPO and Pseudocode)  

## 1. Problem Description and Scope  
* **Problem:** Imagine you're a freelance designer juggling multiple income sources and expenses each month. Between client payments, software subscriptions, and coffee-fueled brainstorming sessions, keeping track of your finances has become a challenge. You want a simple tool to log your earnings and spending, categorize them, and get a clear picture of where your money goes.
* **Scope:**  
  * Features a continuous main loop with 2 hierarchical submenus (Income and Expense).  
  * Validates menu bounds (rejects values outside menu options) and income and expense inputs (rejects negative numbers).  
  * Aggregates total income and expenses in memory during execution and outputs a summary on demand.  
  * Terminates cleanly when the user selects the Exit option.
## 2. IPO Chart (Input - Process - Output)

| Input | Processing | Output |
| :--- | :--- | :--- |
| • `main_choice` (Integer: 1–4)<br>• `sub_choice` (Integer: 1–3)<br>• `income_amount` (Real / Integer: ≥ 0)<br>• `expense_amount` (Real / Integer: ≥ 0) | 1. Initialize `total_income = 0` and `total_expense = 0`.<br>2. Loop main menu display until user enters `4`.<br>3. Validate that `main_choice` is between 1 and 4.<br>4. If `1` (Income):<br>&emsp;a. Display the income submenu.<br>&emsp;b. Validate `sub_choice` is between 1 and 3.<br>&emsp;c. Map the selected choice to an income category.<br>&emsp;d. Prompt for the income amount.<br>&emsp;e. Validate that `income_amount >= 0`.<br>&emsp;f. Add `income_amount` to `total_income`.<br>5. If `2` (Expense):<br>&emsp;a. Display the expense submenu.<br>&emsp;b. Validate `sub_choice` is between 1 and 3.<br>&emsp;c. Map the selected choice to an expense category.<br>&emsp;d. Prompt for the expense amount.<br>&emsp;e. Validate that `expense_amount >= 0`.<br>&emsp;f. Add `expense_amount` to `total_expense`.<br>6. If `3` (Financial Summary):<br>&emsp;a. Calculate `balance = total_income - total_expense`.<br>&emsp;b. Determine whether the balance represents a profit, loss, or break-even.<br>&emsp;c. Display a formatted financial summary.<br>7. If `4` (Exit): Display an exit farewell and terminate. | • Invalid input warning messages<br>• Confirmation of logged income and category<br>• Confirmation of logged expense and category<br>• Formatted Financial Summary:<br>&emsp;- Total Income<br>&emsp;- Total Expenses<br>&emsp;- Remaining Balance<br>&emsp;- Profit, Loss, or Break-Even Status<br>• Exit farewell message |


## 3. Pseudocode  
```
Module Main ()
    DECLARE Real total_income = 0.0
    DECLARE Real total_expense = 0.0
    DECLARE Real balance = 0.0
    DECLARE Integer main_choice = 0
    DECLARE Integer sub_choice = 0
    DECLARE Real income_amount = 0.0
    DECLARE Real expense_amount = 0.0
    DECLARE String category_name = ""

    DISPLAY "============================"
    DISPLAY "  PERSONAL BUDGET TRACKER   "
    DISPLAY "============================"

WHILE True
    // STEP 1: Main Menu & Input Validation
    DISPLAY "--- MAIN MENU ---"
    DISPLAY "1. Log Income"
    DISPLAY "2. Log Expense"
    DISPLAY "3. View Financial Summary"
    DISPLAY "4. Exit"
    DISPLAY "Enter your choice (1-4):"
    INPUT main_choice


    WHILE main_choice != 1 AND main_choice != 2 AND main_choice != 3 AND main_choice != 4
            DISPLAY "Invalid. Choice must be 1, 2, 3, or 4. Try Again:"
            INPUT main_choice
    END WHILE

    // STEP 2: Route Submenus and Actions
    IF main_choice == 1 THEN
    DISPLAY "--- INCOME MENU ---"
    DSIPLAY "1. Design"
    DISLPAY"2. Coding"
    DISPLAY "3. User Documentation"
    DISPLAY "Enter income category (1-3):"
    INPUT sub_choice

        WHILE sub_choice != 1 AND sub_choice != 2 AND sub_choice !=3
            DISPLAY "Invalid. Please enter 1, 2, or 3. Try Again!"
            INPUT sub_choice
        END WHILE


        IF sub_choice == 1 THEN
            category_name = "Design"
        ELSE IF sub_choice == 2 THEN
            category_name = "Coding"
        ELSE
            category_name = "User Documentation"
        END IF

        DISPLAY "Enter income amount:"
        INPUT income_amount
        WHILE income_amount < 0
            DISPLAY "Invalid. Please enter amount >= 0:"
            INPUT income_amount
        END WHILE


        total_income = total_income + income_amount
        DISPLAY "Successfully added $" , amount, "of income for", category_name, "."


        ELSE IF main_choice == 2 THEN
            DISPLAY "--- EXPENSE MENU ---"
            DISPLAY "1. Software"
            DISPLAY "2. Equipment"
            DISPLAY "3. Workspace"
            DISLPAY "Enter expense category (1-3):"

            WHILE sub_choice != 1 AND sub_choice != 2 AND sub_choice !=3
               DISPLAY "Invalid. Please enter 1, 2, or 3. Try Again!"
               INPUT sub_choice
            END WHILE


            IF sub_choice == 1 THEN
               catergory_name = "Software"
            ELSE IF sub_choice == 2 THEN
               catergory_name = "Equipment"
            ELSE
               category_name = "Workspace"
            END IF


        DISPLAY "Enter Expense Amount:"
        INPUT expense_amount
          WHILE expense_amount < 0
            DISPLAY "Invalid. Please enter expense >= 0:"
            INPUT expense_amount
          END WHILE


         total_expense = total_expense + expense_amount
        DISPLAY "Successfully added $" , amount, "of expenses for", category_name, "."

    ELSE IF main_choice == 3 THEN
        balance = total_income - total_expense"
        DISPLAY "=========================================="
        DISPLAY "           FINANCIAL SUMMARY               "         
        DISPLAY "=========================================="
        DISPLAY "Total Income:", total_income
        DISPLAY "Total Expenses:", total_expense
        DSIPLAY "Net Balance:", balance

        IF balance > 0 THEN
            DISPLAY "Status: Good job! You were profitable this month! :)"
        ELSE IF balance < 0 THEN
            DISPLAY "Status: You spent more than you earned this month. :("
        ELSE
            DISPLAY "Status: You broke even this month."
      END IF
        DISPLAY "=========================================="
    ELSE IF main_choice == 4 THEN
        DISLPAY "Thank you for using Personal Budget Tracker. Goodbye!"
        BREAK
    END IF
  END WHILE
END MODULE
