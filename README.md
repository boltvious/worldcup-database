# 🏆 World Cup Database

A relational database built with **PostgreSQL** to store and analyze data from the final three rounds of the FIFA World Cup tournaments (2014 and 2018). This project demonstrates database schema design, data normalization, Bash scripting for automated data ingestion, and advanced SQL querying for data analysis.

## 🛠️ Technologies Used
*   **PostgreSQL**: For database creation, table relationships, and data querying.
*   **Bash Scripting**: For automating the CSV data ingestion process (`insert_data.sh`) and generating analytical reports (`queries.sh`).
*   **Git**: For version control.

## 📂 Project Structure
*   `worldcup.sql`: The database dump file (schema and data).
*   `insert_data.sh`: A Bash script that reads `games.csv`, populates the `teams` table with unique teams, and inserts all match records into the `games` table using foreign keys.
*   `queries.sh`: A Bash script that executes a series of SQL queries to answer specific statistical questions about the World Cup data.
*   `games.csv`: The raw dataset containing World Cup match data.

## 🗄️ Database Schema

The database consists of two tables with a one-to-many relationship:

**1. `teams` Table**
*   `team_id` (SERIAL PRIMARY KEY)
*   `name` (VARCHAR UNIQUE NOT NULL)

**2. `games` Table**
*   `game_id` (SERIAL PRIMARY KEY)
*   `year` (INT NOT NULL)
*   `round` (VARCHAR NOT NULL)
*   `winner_id` (INT FOREIGN KEY referencing `teams`)
*   `opponent_id` (INT FOREIGN KEY referencing `teams`)
*   `winner_goals` (INT NOT NULL)
*   `opponent_goals` (INT NOT NULL)

## 🚀 How to Run

1.  **Recreate the Database:**
    Create a PostgreSQL database and run the dump file:
    ```bash
    createdb worldcup
    psql -d worldcup -f worldcup.sql
    ```

2.  **Run the Data Ingestion Script:**
    (Make sure the script has executable permissions: `chmod +x insert_data.sh`)
    ```bash
    ./insert_data.sh
    ```

3.  **Generate the Analytical Report:**
    ```bash
    ./queries.sh
    ```

## 📊 Sample Insights from `queries.sh`
The script runs several complex SQL queries (using `JOIN`, `GROUP BY`, `AVG`, `ROUND`, etc.). Here are some of the questions it answers:
*   Total number of goals in all games from winning teams.
*   Average number of goals in all games rounded to two decimal places.
*   The winner of the 2018 tournament.
*   List of unique winning team names in the whole dataset.
*   List of teams that start with 'Co'.

## ✅ Testing
This project passed all rigorous unit tests provided by freeCodeCamp for the Relational Databases certification. The scripts were tested for correct output formatting, database constraints, and execution permissions.
