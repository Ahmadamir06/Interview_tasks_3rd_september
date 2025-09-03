# Task B2: Bank Account System

## Problem

Design a class `BankAccount` that represents a bank account with basic functionalities. Create a robust system that handles deposits, withdrawals, and account information management.

---

## Objective

Write a **Python** class that implements core banking operations with proper validation and error handling.

---

## Requirements

### Class: `BankAccount`

#### Attributes
- **`account_number`**: A unique identifier for the account (integer)
- **`account_holder_name`**: Name of the account holder (string)
- **`balance`**: The current balance in the account (float)

#### Methods

##### Constructor
```python
__init__(account_number, account_holder_name, initial_balance=0.0)
```
Initialize the account with required details and optional initial balance.

##### Core Operations
- **`deposit(amount)`**: Add a specified amount to the balance
- **`withdraw(amount)`**: Subtract a specified amount from the balance (if sufficient funds are available)
- **`get_balance()`**: Return the current balance of the account
- **`get_account_info()`**: Return a string summarizing the account details

---

## Functional Requirements

### Validation Rules
- ✅ **Withdrawal validation**: Only allow withdrawal if balance is sufficient
- ✅ **Amount validation**: Ensure deposit/withdrawal amounts are positive
- ✅ **Account initialization**: Require valid account number and holder name
- ✅ **Balance protection**: Prevent negative balances

### Error Handling
- Handle insufficient funds gracefully
- Validate input parameters
- Provide meaningful error messages

---

## Expected Implementation

### Class Structure
```python
class BankAccount:
    def __init__(self, account_number, account_holder_name, initial_balance=0.0):
        # Initialize account attributes
        pass
    
    def deposit(self, amount):
        # Add amount to balance with validation
        pass
    
    def withdraw(self, amount):
        # Subtract amount from balance if sufficient funds
        pass
    
    def get_balance(self):
        # Return current balance
        pass
    
    def get_account_info(self):
        # Return formatted account information
        pass
```

---

## Example Usage & Output

### Sample Scenario
```python
# Create account
account = BankAccount(123456, "John Doe", 1000.50)

# Display initial info
print(account.get_account_info())

# Perform deposit
account.deposit(200.00)
print(f"After Deposit: 200.00")
print(f"New Balance: {account.get_balance()}")

# Perform withdrawal
account.withdraw(500.00)
print(f"After Withdrawal: 500.00")
print(f"New Balance: {account.get_balance()}")
```

### Expected Output
```
Account Holder: John Doe
Account Number: 123456
Balance: 1000.50

After Deposit: 200.00
New Balance: 1200.50

After Withdrawal: 500.00
New Balance: 700.50
```

---

## Additional Considerations

### Edge Cases to Handle
- **Insufficient funds**: Withdrawal amount exceeds balance
- **Invalid amounts**: Negative or zero deposit/withdrawal amounts
- **Account creation**: Invalid account numbers or empty names

### Optional Enhancements
- Transaction history tracking
- Account type (savings, checking)
- Interest calculation
- Account freezing/unfreezing functionality

---

## Acceptance Criteria

- [ ] **Constructor** properly initializes all attributes
- [ ] **Deposit method** increases balance correctly
- [ ] **Withdraw method** validates sufficient funds before withdrawal
- [ ] **Balance method** returns accurate current balance
- [ ] **Account info method** returns properly formatted information
- [ ] **Error handling** for invalid operations
- [ ] **Input validation** for all methods
- [ ] **Clean, readable code** with appropriate comments

---

## Deliverables

1. **`BankAccount.py`** - Complete class implementation
2. **`demo.py`** - Demonstration script showing all functionality
3. **Brief documentation** explaining design decisions

---

## Evaluation Focus

- **Object-oriented design principles**
- **Input validation and error handling**
- **Code readability and documentation**
- **Proper encapsulation of data and methods**
- **Handling of edge cases and exceptions**
