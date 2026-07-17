# Prime Bank – Console Bank Management System

A simple console-based banking system written in C. Built as a first-semester CSE project at UITS.

## Features

- **Account Setup** – Enter name, set a 4-digit login PIN and a 4-digit master PIN (used for recovery).
- **Login System** – 3 attempts to enter the correct PIN. Account locks after 3 wrong attempts.
- **Account Recovery** – If locked, use the master PIN to unlock and set a new login PIN.
- **Main Menu**
  1. Check Balance
  2. Deposit Money
  3. Withdraw Money
  4. Transaction History
  5. Change PIN
  6. Exit

## How It Works

- Starting balance is fixed at **1000 BDT**.
- Every deposit/withdrawal is logged with a label and amount, stored in parallel arrays (`history[]`, `historyAmount[]`).
- Up to **20 transactions** can be recorded per session (buffer overflow guard included).
- PIN and Master PIN can never be the same, and a new PIN must differ from both the master PIN and the current PIN.

## Build & Run

```bash
gcc prime_bank.c -o prime_bank
./prime_bank
```

## Sample Flow

```
WELCOME TO Prime Bank
Enter Your Full Name: Fahim
Set 4-Digit Login PIN: 1234
Set 4-Digit Master PIN (for account recovery): 5678

Enter PIN to Login: 1234
Login Successful!

MAIN MENU
1. Check Balance
2. Deposit Money
3. Withdraw Money
4. Transaction History
5. Change PIN
6. Exit
Enter Choice:
```

## Notes / Design Decisions

- Login logic uses a `loggedIn` flag with `while` loops instead of `goto`, to avoid uncontrolled jumps and duplicate account-opening entries.
- Input validation is done for PIN length (4 digits), amount (must be positive), and balance (can't withdraw more than available).
- This is a learning project — no file storage, so all data resets when the program exits.

## Possible Future Improvements

- Save/load account data to a file so balance persists between runs.
- Support multiple accounts instead of a single hardcoded user.
- Encrypt PIN storage instead of keeping it as plain `int`.
