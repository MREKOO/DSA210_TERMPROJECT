# DSA210 Term Project

## Table of Contents
* [Project Overview](#project-overview)
* [Collection of Data](#collection-of-data)
* [Description of the Data Set](#description-of-the-data-set)

---

## Project Overview

This is the term project of me, Ekin Gülhan, for the DSA210 course offered by Sabancı University. In this project I aim to apply data science techniques to analyze my own data of online chess games played and test my hypothesis.

---

## Collection of Data

The data of my online chess games will be extracted from the webserver of chess.com, the most used online chess platform. Chess.com provides an API for its users to reach many parameters about the games played by its users. Through the API of chess.com, I will extract the game data stored in a JSON file, either manually or using python. Once I pull this data, using lichess.org's (again a famous non-profit online chess platform) API and through python, I will request a analysis of each game from the chess engine Stockfish embeded inside lichess web app. Stockfish provides analyzes of chess games; marking out the accuracy (the rate of move correctness according to the chess engine, in other words how similarly the player has made their moves to the chess engine) of the players, showing the blunders (a significantly mistaken move made by a player during a game of chess, that often worsens the position for the respective player), and providing the correct, or brilliant moves (oftenly reffered to a move that is the only move that could be made to keep the positional advantage unchanged).

---

## Description of the Tools

All the libraries and tools will be use in accordance with Python and their APIs.

- **Pandas:** This library will be used to manipulate the data.
- **Matplotlib:** This library will be used to visualize the data.
- **chess.com:** The online chess data will be collected with the API.
- **lichess.org:** The collected data will be sent to be evaluated with the help of the API to further enrich the data.
- **Stockfish:** The data sent to lichess.org will be analyzed by the powerfull chess engine, that is embeded inside the lichess.org website.
- **JSON:** Python JSON library may be used to process data into the code.  


---

## Description of the Data Set

The JSON file imported from chess.com includes the relevant data:

- **PGN:** PGN (Portable Game Notation) is a text format used globally to record chess games, including moves with the time remaining, and some other metadata.
  - **Date and Time:** From the PGN of each game, the date and time (GMT) the respective game took place will be extracted.
  - **Clock at Each Move:** The remaining time for each player at every move is included in the PGN. Can be used to determine average time taken to make the moves, time pressure rate, etc.
  - Raw Game Data: The record of the moves made. The notation is encoded according to globally accepted encoding. E.g: *1. Nf3 d5, encodes that in the 1st move, white played knight (N) to f3 square, then black played pawn to d5 in response*.
- **FEN:** A notation that represents the position of all pieces on the board at a spesific moment during the game. Unlike PGN it does not contain the full game.
- **time_control:** The time limit given to each player for the entire game to complete all their moves.
- **time_class:** Specifies the time control format, *bullet* (1-3 min for each player), *blitz* (3-5 min for each player), or *rapid* (10-60min min for each player).
- **result:** The outcome of the game. Not only win, loss, or draw but also the reason of the outcome will be included. E.g. *timeout, resigned, insufficient material, stalemate, checkmate*, etc.
- **eco:** ECO (Encyclopedia of Chess Openings) encodes the opening (generally a theoretical sequence of moves which are played in the beginning of the game, nearly all of the sequences are studied and named previously) of a chess game. E.g. *French Defense, Two Knights Variation*.

The enriched data with the analysis of Stockfish will include:

- **Accuracy:** A measure of how closely the moves match the optimal moves suggested by the chess engine.
- **Blunder Count:** The number of significant game-changing mistakes made by a player during the game.
- **Correct Moves:** The number of moves played by the player that are considered the best or near-optimal (generally moves that does not worsen the position) by the chess engine.
- **Average Centipawn Loss:** A measure of the average loss in position strength, in centipawns (a *pawn* in a chess game is considered to have a value of *100 centipawns*, the position at a certain time of a chess game is evaluated with the *centipawn loss*, e.g. *white +200* means white has *200 centipawns of adventage*, in other words, white is *200 centipawns* better at this position), for each move compared to the best move.

---
