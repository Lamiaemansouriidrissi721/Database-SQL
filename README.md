The provided SQL script outlines the creation and management of a database table named league_database, designed to store user performance metrics for a gaming application. Here's a breakdown of the script:

1. Table Creation:

The script begins by creating a table named league_database with the following columns:

    id: An integer that serves as the primary key, automatically incremented for each new record.
    user_Tag: A text field to store the user's in-game tag or username.
    Game_Rank: A text field indicating the user's rank in the game (e.g., 'Challenger', 'Diamond').
    performance: An integer representing the user's performance score.

2. Inserting Data:

The script inserts sample data into the league_database table:

INSERT INTO league_database (user_Tag, Game_Rank, performance)
VALUES ('sweetshadow', 'Challenger', 90),
       ('player1', 'Diamond', 75),
       ('gamer123', 'Gold', 60),
       ('proPlayer', 'Master', 85),
       ('casualGamer', 'Silver', 40);

3. Viewing Data:

To view all records in the league_database table:

SELECT * FROM league_database;

4. Adding New User:

The script adds a new user, 'AkiraBiers18', with a 'Silver' rank and a performance score of 50:

INSERT INTO league_database (user_Tag, Game_Rank, performance)
VALUES ('AkiraBiers18', 'Silver', 50);

5. Modifying Table Structure:

To accommodate additional data, the script adds three new columns:

    wins: An integer to store the number of wins.
    total_games: An integer to store the total number of games played.
    win_rate: A real number to store the win rate percentage.

ALTER TABLE league_database
ADD COLUMN wins INTEGER,
ADD COLUMN total_games INTEGER,
ADD COLUMN win_rate REAL;

6. Updating New Columns:

The script updates the new columns with sample data for each user:

UPDATE league_database
SET wins = 50, total_games = 100
WHERE user_Tag = 'sweetshadow';

UPDATE league_database
SET wins = 30, total_games = 60
WHERE user_Tag = 'player1';

UPDATE league_database
SET wins = 30, total_games = 500
WHERE user_Tag = 'gamer123';

UPDATE league_database
SET wins = 30, total_games = 90
WHERE user_Tag = 'AkiraBiers18';

UPDATE league_database
SET wins = 30, total_games = 200
WHERE user_Tag = 'proPlayer';

UPDATE league_database
SET wins = 30, total_games = 70
WHERE user_Tag = 'casualGamer';

7. Calculating Win Rates:

The script calculates and updates the win_rate for each user:

UPDATE league_database
SET win_rate = (wins * 100.0 / total_games);

8. Viewing Users by Win Rate:

To view users ordered by their win rate in descending order:

SELECT user_Tag, win_rate
FROM league_database
ORDER BY win_rate DESC;

9. Deleting Users:

The script deletes records for users 'gamer123' and 'proPlayer':

DELETE FROM league_database
WHERE user_Tag IN ('gamer123', 'proPlayer');

10. Final Verification:

To verify the deletion, the script selects all records from the league_database table:

SELECT * FROM league_database;

This script effectively manages user performance data, allowing for the addition of new users, modification of user statistics, and removal of users as needed.

For more detailed information on database schema design and best practices, you can refer to this resource:
CockroachDB
