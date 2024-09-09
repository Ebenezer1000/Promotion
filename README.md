# Promotion
## Daily Rebate Promotion
- Duration 

Start Time - Long Term
- Conditions to qualify for this bet
  1. Account needs to be binded (phone number/Google authenticator etc) to qualify for this promotion.
  2. Account balances below 1,000$ are not eligible for this promotion. That is equal and greater 1000$ only qualifies
  3. Daily Rebate (Interest) Settlement - The interest you receive depends on your VIP level and your current account balance. The calculation only applies if your account balance is above or equal to 1,000$.
  4. Every day at 1:00 a.m., the system calculates your daily rebate (interest)
  5. You need to bet on certain games (of our choosing) that the average bet amount will be based on.
  6. Your VIP level is based on the amount of betting you’ve done. The system checks and updates your VIP level every 10 days, specifically on the 1st, 11th, and 21st of each month.
  7. The account change/transaction history in both the frontend and back office needs to record this change in account balance of the user.
     
 ![image](https://github.com/user-attachments/assets/3f738695-5ab2-463e-a537-f6b6d371802c)

 # 1. Backend Development:
The backend team will be responsible for implementing the core logic of the promotion, including calculating interest, updating VIP levels, and managing user accounts.

## Core Backend Logic:
- Daily Rebate Calculation:

Implement a scheduled job (e.g., cron job) to run daily at 1:00 a.m. to calculate the interest for users.
Ensure the interest is calculated based on the VIP level and account balance, with only accounts over 1,000$ qualifying for the promotion.
Interest Formula:
Interest = Account Balance × Daily Interest Rate

Example: A VIP3 user with an account balance of 20,000$ will earn interest as follows:
20,000$ × 0.001 = 20$

- VIP Level Tracking:

Set up logic to calculate the VIP level based on the average daily bet amount. This can be done by tracking the user's betting history, summing the qualifying bets over 10 days, and then updating the VIP level accordingly.

Implement a VIP level update job that runs every 1st, 11th, and 21st of each month to assess and update the user's VIP status.

- Bet Tracking:

Create a function to track bets placed on specific games that are eligible for the promotion. The average bet amount should be calculated over 10-day periods to determine VIP status.
# Security Checks:
Ensure that only accounts with valid security information (bound by phone number or Google Authenticator) are eligible. The backend should check this condition before applying interest.

# Database and Transaction History:
- Account Balance Management:
Ensure the database is updated to reflect the interest earned. For transparency, each transaction (interest, balance changes, etc.) should be logged in the transaction history.

- Transaction Logs:
Implement detailed transaction logging that captures the interest calculation, VIP level updates, and other relevant changes, which should be accessible to both the frontend and back office.
Game Eligibility:

- Create a backend service that filters bets based on the eligible games for the promotion

# 2. Frontend Development:

The frontend will handle user interaction, displaying VIP levels, account balance changes, and transaction history.

## User Interface (UI) for Promotion Information:
- VIP Level Display:
Show the user's current VIP level and the required daily bet amount to reach the next level. Display this in the user’s profile or a dashboard area.
- Interest Tracking:
Display the interest earned at 1:00 a.m. each day. Include an "Interest History" section where users can view the daily rebates they’ve received.

![image](https://github.com/user-attachments/assets/7b9d24fc-16b8-429e-9d9a-71c3de7ef2ad)


## Transaction History:
- Transaction Logs:
Create a clear section in the user’s account that shows all transactions, including the daily interest updates, VIP level changes, and betting activity. This should match the backend's data.

## Security Information Status:
- Eligibility Check:
Add a feature that checks and displays whether the user has bound their account with security measures (phone number or  Google Authenticator). If not, prompt them to complete this step to qualify for the promotion.

## Bet Tracking and Game Eligibility:
- Bet Status:
Show users which games are eligible for the promotion and highlight their bet history for the eligible games.
Include a section to track the average daily bet amount, so users know how much they need to bet to reach higher VIP levels.

## Visual Feedback:
- Balance Updates:
Use real-time updates to show when a user's account balance changes due to the interest rebate.
- Progress Bars:
Implement progress bars that show how close the user is to the next VIP level based on their betting history.
- Bonus Notification:
Once the user meets the conditions and the backend calculates the bonus, display a notification or popup informing them that they’ve earned the bonus.
