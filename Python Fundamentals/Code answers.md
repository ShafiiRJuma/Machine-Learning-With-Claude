### Scenario 1

```
student_name = "Juma Mwakisu"
student_age = 21
gpa = 3.6
is_registered = True

print(f'Registration Confirmed: {student_name}\nAge: {student_age} | GPA: {gpa:.2f} | Status: {is_registered}')
```

### Scenario 2

```
amount_inserted = 1500
min_amount = 500
max_amount = 50000

status_message = 'Valid' if (amount_inserted >= min_amount and amount_inserted <= max_amount) else 'Invalid'
print(f"Amount: {amount_inserted} TZS\nStatus: {status_message}")
```

### Scenario 3

```
fares = [400, 400, 600, 400, 1000, 400, 600, 400]

total = 0
for fare in fares:
    total = total + fare

highest_fare = max(fares)

count = 0
for fare in fares:
    if fare == highest_fare:
        count = count + 1

print(f"Total Collected: {total} TZS\nHighest Fare: {highest_fare} TZS\nPassengers at Highest Fare: {count}")
```

### Scenario 4

```
def check_account_number(account_number):
    if len(account_number) == 10 and account_number.isdigit():
        return True
    else:
        return False

def check_customer_record(customer):
    issues = []

    if len(customer["name"]) == 0:
        issues.append("customer name is empty")

    if customer["balance"] <= 0:
        issues.append("balance is not positive")

    if not check_account_number(customer["account_number"]):
        issues.append("account number is invalid")

    valid = len(issues) == 0
    return {"valid": valid, "issues": issues}

customer = {
    "name": "Fatuma Ally",
    "account_number": "0123456789",
    "balance": 250000,
    "email": "fatuma.ally@crdbmail.co.tz"
}

result = check_customer_record(customer)
print(result)
```
