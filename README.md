# Promotion
## DAILY REBATE PROMOTION
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


# MULTI-BET BONUS PROMOTION
- Duration 

Start Time - End Time
- Conditions to qualify for this bet
 1. Account needs to be binded (phone number/Google authenticator etc) to qualify for this promotion.
 2. A user must place at least 100 bets on different games (3 or more lottery games qualifies as different games) within a 30-day period.
 3. Each bet should have a bet amount not less than 10$ and a cummulative threshold amount of 1000$ in the 30-day period.
 4. Once the conditions are met, calculate the bonus. For instance, if the cumulative bet amount reaches the threshold, apply a 10% bonus on the total wagered amount.

- Example:

A user places different bets:
Bet 1: 10$ on Game A
Bet 2: 30$ on Game B
Bet 3: 20$ on Game C
Bet 4: 100$ on Game D
Bet 5: 50$ on Game E
etc
If the conditions are met (bets on different games, each bet less equal and greater than 10$ and threshold total amount of 1000$), the backend should calculate the total wagered amount and apply the bonus (e.g., 10% of total wagered amount = bonus).


 # 1. Backend Development:
The backend needs to track user's bets across multiple games, calculate bonuses, and applying rewards when conditions are met.

- Bet Tracking:
Create a mechanism to track individual bets that meet the criteria for this promotion. Each bet should be associated with:
User ID
Game ID (to ensure bets are on different games).
Bet amount
Date (to ensure it falls within the qualifying period).

- Bonus Application:
Once the bonus is calculated, update the user’s account balance with the bonus amount.
Log the bonus in the transaction history for transparency.

- Period Tracking:
The backend should track the date range during which the promotion is valid and only apply the bonus if bets are placed within this period.

- Database Schema:
Create tables or collections to store:
Bets (with relevant fields like User ID, Game ID, Bet Amount, Date).
Bonuses (with User ID, Bonus Amount, Date Awarded).
Promotion Rules (to allow flexibility in updating conditions).

# 2. Frontend Development:
The frontend needs to display the user’s progress toward meeting the conditions for the bonus and showing the bonus when earned.

## User Interface (UI) for Bet Progress:
- Bet Tracking Display:

Create a progress bar or visual indicator that tracks the user's progress toward qualifying for the bonus.
For example, display how many qualifying bets the user has placed and how many more are needed to meet the condition (e.g., "You’ve placed 42/100 qualifying bets").

- Real-Time Updates:
As users place new bets, update the progress display in real time. This requires the frontend to communicate with the backend via API to fetch updated progress information after each bet.

## Bonus Display:
- Bonus Notification:
Once the user meets the conditions and the backend calculates the bonus, display a notification or popup informing them that they’ve earned the bonus.
Example: “Congratulations! You’ve earned a 10% bonus of 30$ for placing X qualifying bets and bet amount!”

## Transaction History:
- Add a section where users can view the bonus and related information in their transaction history (bonus amount, qualifying period, etc.).

## Promotional Banner:
- Display a promotional banner on the user dashboard to encourage them to participate in the multi-bet promotion, showing their current progress and potential reward.


# 3. WELCOME BONUS FOR NEW PLAYERS:
- Duration 

Start Time - Long Term
- Conditions to qualify for this bet
1. New User Registration:
The user must create a new account on the platform. This means they have never had an account before, and the system should detect them as a new user.
2. First Deposit Requirement:
The user must make their first-ever deposit into their account. This is a critical condition, as the welcome bonus will only be applied after the first deposit is made.
3. Minimum Deposit Amount:
There will be a minimum deposit amount required to qualify for the welcome bonus. For example, the user might need to deposit at least $10 to qualify.
The system should check that the deposit meets or exceeds the threshold before applying the bonus.
4. Eligibility for Only One Bonus:
Each user is eligible for only one welcome bonus. Once the bonus is awarded after the first deposit, the system should mark the bonus awarded as true to prevent users from claiming multiple welcome bonuses.
5. Security Verification:
The user needs to verify/bind their account (e.g., through email or phone verification) before qualifying for the bonus.
- Example of Conditions:
- Condition 1: User must create a new account.
- Condition 2: User must make their first deposit of at least $10.
- Condition 3: The welcome bonus can only be awarded once per user.
- Condition 4 (Optional): User must verify their account via email or phone before receiving the bonus.

# 1. Backend Development:
The backend will be responsible for detecting new users, processing their first deposit, and applying the welcome bonus.

## User Sign-Up and Initial Setup:

Create the logic to track new user registrations. Once a user signs up, ensure they are flagged as eligible for the welcome bonus.

Add a “first-deposit” flag in the database that tracks whether the user has made their first deposit. This will be critical in ensuring that the bonus is applied only after the first deposit.

Database Schema Update: Ensure the user table or collection contains fields such as:

is_new_user: true
first_deposit: false
bonus_awarded: false
First Deposit Detection:

Implement logic to detect when a user makes their first deposit. The system should check if the first_deposit flag is false and then switch it to true once the deposit is made.




