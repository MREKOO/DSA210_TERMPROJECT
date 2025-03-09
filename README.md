# DSA210 Term Project

This is the term project of **Ekin Gülhan** for the **DSA210** course offered by **Sabancı University**. In this project, I aim to apply **data science techniques** to analyze my own data of **online chess game data** and test my hypotheses.


## Project Overview 🔗

This project focuses on exctracting and analyzing online chess game data from **chess.com** and **lichess.org**. Using **Python** and various data science techniques, I will evaluate my own gameplay patterns, identify the correlations between different parameters, and validate spesific hypotheses about my performance trends.


---

## Collection of Data 🔎

The data of my online chess games will be extracted from the webserver of **chess.com**, the most widely used online chess platform. Chess.com provides an **API** that allows users to pull out detailed game data. Through this **API**, I will extract the game data stored in a **JSON file**, either manually or using **Python scripts**. 

After retrieving the raw game data, using **lichess.org's (a widely used non-profit online chess platform) API** of **Python**, I will request an analysis of each game. This analysis will be made by a powerful and well-known chess engine **Stockfish**. This chess engine **Stockfish** is embedded inside **lichess.org** and can be reached by the **lichess.org API**. The requested analysis for each game will contain:
- **Move Accuracy**: The rate of move correctness according to the chess engine, in other words how closely the player's moves match the suggested engine moves.
- **Blunders**: Identifying significantly mistaken moves made by the player, often worsening the player's position and changing the course of the game.
- **Correct Moves**: Highlighting good moves that maintain the player's advantage.
- **Average Centipawn Loss**: A measure for evaluating a position that occurs anytime during the game. Also helpful to detect correct and blunderous moves.

---

## Description of the Tools 🪛

All the libraries and tools will be used in accordance with **Python** and their **API**s.

- **Pandas:** This library will be used to manipulate the data.
- **Matplotlib:** This library will be used to visualize the data.
- **chess.com:** The online chess data will be collected with the API.
- **lichess.org:** The collected data will be sent to be evaluated with the help of the API to further enrich the data.
- **Stockfish:** The data sent to lichess.org will be analyzed by the powerfull chess engine, that is embeded inside the lichess.org website.
- **JSON:** Python JSON library may be used to process data into the code.  


---

## Description of the Data Set 📝

The **JSON file** imported from **chess.com** includes the relevant data:

- **PGN:** PGN (Portable Game Notation) is a text format used globally to record chess games, including moves with the time remaining, and some other metadata.
  - **Date and Time:** From the PGN of each game, the date and time (GMT) the respective game took place will be extracted.
  - **Clock at Each Move:** The remaining time for each player at every move is included in the PGN. Can be used to determine average time taken to make the moves, time pressure rate, etc.
  - Raw Game Data: The record of the moves made. The notation is encoded according to globally accepted encoding. E.g. *1. Nf3 d5, encodes that in the 1st move, white played knight (N) to f3 square, then black played pawn to d5 in response*.
- **FEN:** A notation that represents the position of all pieces on the board at a spesific moment during the game. Unlike PGN it does not contain the full game.
- **Time Control:** The time limit given to each player for the entire game to complete all their moves.
- **Time Class:** Specifies the time control format, *bullet* (1-3 min for each player), *blitz* (3-5 min for each player), or *rapid* (10-60min min for each player).
- **Result:** The outcome of the game. Not only win, loss, or draw but also the reason of the outcome will be included. E.g. *timeout, resigned, insufficient material, stalemate, checkmate*, etc.
- **ECO:** ECO (Encyclopedia of Chess Openings) encodes the opening (generally a theoretical sequence of moves which are played in the beginning of the game, nearly all of the sequences are studied and named previously) of a chess game. E.g. *French Defense, Two Knights Variation*.

The enriched data with the analysis of **Stockfish** will include:

- **Accuracy:** A measure of how closely the moves match the optimal moves suggested by the chess engine.
- **Blunder Count:** The number of significant game-changing mistakes made by a player during the game.
- **Correct Moves:** The number of moves played by the player that are considered the best or near-optimal (generally moves that does not worsen the position) by the chess engine.
- **Average Centipawn Loss:** A measure of the average loss in position strength, in centipawns (a *pawn* in a chess game is considered to have a value of *100 centipawns*, the position at a certain time of a chess game is evaluated with the *centipawn loss*, e.g. *white +200* means white has *200 centipawns of adventage*, in other words, white is *200 centipawns* better at this position), for each move compared to the best move.

---

## Hypotheses

The analyzed data will be used to support or deny the following statements:


---
*This project utilizes data from chess.com and lichess.org, analysis powered by Stockfish.*

