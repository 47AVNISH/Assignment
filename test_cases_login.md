# Question 2: Test Case Design — Login System

Application under test: Login System (Username, Password, Login button)

Functional requirements covered:
- R1: Username must not be empty
- R2: Password must be at least 6 characters long
- R3: Valid username and password allow a successful login
- R4: Invalid credentials display a specific error message
- R5: After 3 consecutive failed login attempts, the account is locked

| Test Case ID | Test Scenario | Input Data | Expected Output |
|--------------|---------------|------------|-----------------|
| TC_01 | Valid login with a registered username and a password of exactly 6 characters (edge: minimum allowed length) | Username = user1, Password = pass12 | "Login successful" and the user is redirected to the dashboard/home page |
| TC_02 | Valid login with correct credentials and a password longer than 6 characters | Username = user1, Password = pass1234 | "Login successful" and the user is redirected to the dashboard/home page |
| TC_03 | Invalid login with an empty username field (edge: empty username) | Username = (empty), Password = pass123 | Error message "Username is required" displayed; login is not performed |
| TC_04 | Invalid login with a username containing only whitespace characters | Username = "   ", Password = pass123 | Error message "Username is required" displayed; login is not performed |
| TC_05 | Invalid login with an empty password field (edge: empty password) | Username = user1, Password = (empty) | Error message "Password is required" displayed; login is not performed |
| TC_06 | Invalid login with a password shorter than 6 characters (edge: 5 characters, below minimum) | Username = user1, Password = pass1 (5 chars) | Error message "Password must be at least 6 characters long" displayed; login is not performed |
| TC_07 | Invalid login with a registered username but a wrong password | Username = user1, Password = wrongpass | Error message "Invalid username or password" displayed; login is not performed; failed-attempt counter increases to 1 |
| TC_08 | Invalid login with an unregistered username | Username = ghostuser, Password = pass123 | Error message "Invalid username or password" displayed; login is not performed |
| TC_09 | Account locking after 3 consecutive failed login attempts with the same username | Attempt 1: Username = user1, Password = wrongpass1; Attempt 2: Username = user1, Password = wrongpass2; Attempt 3: Username = user1, Password = wrongpass3 | After the 3rd failed attempt, error message "Account is locked due to 3 failed login attempts. Please contact support." is displayed and the account is locked |
| TC_10 | Login attempt on an already locked account (4th consecutive attempt) | Username = user1, Password = correctpass1 | Error message "Account is locked due to 3 failed login attempts. Please contact support." is displayed even though the password is correct; login is not performed |

## Requirement coverage matrix

| Requirement | Covered by |
|-------------|-----------|
| R1 – Username must not be empty | TC_03, TC_04 |
| R2 – Password must be at least 6 characters | TC_05, TC_06, TC_01 (exactly 6), TC_02 (more than 6) |
| R3 – Valid credentials allow successful login | TC_01, TC_02 |
| R4 – Invalid credentials display a specific error message | TC_06, TC_07, TC_08 |
| R5 – Account locked after 3 consecutive failed attempts | TC_09, TC_10 |

## Edge cases covered

- Empty username (TC_03)
- Username with only whitespace (TC_04)
- Empty password (TC_05)
- Password length less than 6 characters — 5 characters (TC_06)
- Password length equal to 6 characters (TC_01)
- Password length greater than 6 characters (TC_02)
- Account lock boundary — exactly 3 failures (TC_09) and the attempt after lock (TC_10)
