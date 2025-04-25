# DSA210 Term Project - Analysis of my Chess Games

This is the term project of **Ekin Gülhan** for the **DSA210** course offered by **Sabancı University**. In this project, I aim to apply **data science techniques** to analyze my own data of **online chess games** and test my hypotheses.


## Project Overview 🔗

This project focuses on exctracting and analyzing online chess game data from **chess.com** and **lichess.org**. Using **Python** and various data science techniques, I will evaluate my own gameplay patterns, identify the correlations between different parameters, and validate spesific hypotheses about my performance trends.

---

## Motivation and Objectives ♟️

The motivation behind this project is to apply **data science techniques** to analyze **my own chess games** and gain insights into my games. While collecting and examining my data, I will be developing **data science skills** and learning the subject better with **hands-on experience**. 

I aim to **collect the necessary data**, **visualize it** and **conduct exploratory data analysis methods** through my project. Then I will be applying **hypothesis tests**, and lastly **machine learning methods and techniques** on my data.

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
  - **Raw Game Data:** The record of the moves made. The notation is encoded according to the globally accepted encoding. E.g. *1. Nf3 d5, encodes that in the 1st move, white played knight (N) to f3 square, then black played pawn to d5 in response*.
- **FEN:** A notation that represents the position of all pieces on the board at a spesific moment during the game. Unlike PGN it does not contain the full game.
- **Time Control:** The time limit given to each player for the entire game to complete all their moves.su
- **Time Class:** Specifies the time control format, *bullet* (1-3 min for each player), *blitz* (3-5 min for each player), or *rapid* (10-60 min for each player).
- **Rating:** Shows the strength of a player's understanding of the game of chess.
- **Result:** The outcome of the game. Not only win, loss, or draw but also the reason of the outcome will be included. E.g. *timeout, resigned, insufficient material, stalemate, checkmate*, etc.
- **ECO:** ECO (Encyclopedia of Chess Openings) encodes the opening (generally a theoretical sequence of moves which are played in the beginning of the game, nearly all of the sequences are studied and named previously) of a chess game. E.g. *French Defense, Two Knights Variation*.

Below is an example table of chess.com's raw data:
                               
| Parameter        | Game 1                                                       | Game 2                                                       |
|------------------|--------------------------------------------------------------|--------------------------------------------------------------|
| **PGN**          | `[Event "Live Chess"]\n[Site "Chess.com"]\n[Date "2024.01.08"]\n[Time "15:20:30"]\n[White "Player X"]\n[Black "Player Y"]\n[Result "1-0"]\n1. e4 {[%clk 0:01:00]} 1... e5 {[%clk 0:00:59.5]} 2. d4 {[%clk 0:00:59.4]} 2... exd4 {[%clk 0:00:58.6]} 3. c3 {[%clk 0:00:58.5]} 3... dxc3 {[%clk 0:00:57.7]} ...` | `[Event "Live Chess"]\n[Site "Chess.com"]\n[Date "2024.01.08"]\n[Time "15:35:10"]\n[White "Player X"]\n[Black "Player Y"]\n[Result "0-1"]\n1. d4 {[%clk 0:01:00]} 1... e6 {[%clk 0:00:59.7]} 2. e3 {[%clk 0:00:59.9]} 2... d5 {[%clk 0:00:59]} 3. c4 {[%clk 0:00:59.8]} 3... c5 {[%clk 0:00:57.6]} 4. Qb3 {[%clk 0:00:59.4]} 4... Nc6 {[%clk 0:00:56.6]} ...` |
| **FEN**          | `rnbqkbnr/pppp1ppp/8/3P4/8/8/PPP2PPP/R1BQKBNR w KQkq - 0 4`   | `rnbqkbnr/ppp1pppp/8/3P4/3N4/8/PPP1PPPP/R1BQKBNR w KQkq - 0 4`   |
| **Time Control** | 60 secs                                                           | 60 secs                                                           |
| **Time Class**   | Bullet                                                       | Bullet                                                       |
| **Player X**     | Rating: 1311                                                  | Rating: 1307                                                  |
| **Player Y**     | Rating: 1333                                                  | Rating: 1303                                                  |
| **ECO**          | [Danish Gambit](https://www.chess.com/openings/Danish-Gambit-3...dxc3) | [Queen's Gambit Declined](https://www.chess.com/openings/Queens-Gambit-Declined-3.e3) |
| **Result**  | Player X won by checkmate                                    | Player Y won on time                                         |




The enriched data with the analysis of **Stockfish** will include:

- **Accuracy:** A measure of how closely the moves match the optimal moves suggested by the chess engine.
- **Blunder Count:** The number of significant game-changing mistakes made by a player during the game.
- **Correct Moves:** The number of moves played by the player that are considered the best or near-optimal (generally moves that does not worsen the position) by the chess engine.
- **Average Centipawn Loss:** A measure of the average loss in position strength, in centipawns (a *pawn* in a chess game is considered to have a value of *100 centipawns*, the position at a certain time of a chess game is evaluated with the *centipawn loss*, e.g. *white +200* means white has *200 centipawns of adventage*, in other words, white is *200 centipawns* better at this position), for each move compared to the best move.

---

## Data Visualization 🎨

To understand the behaviour of my data, uncover trends and correlations; I will use **data visualization techniques**. The visualization methods will include; **histograms**,  **boxplots**, **scatter plots**, **heatmaps**, **time-series graphs**, and more. 

With the visualization, I will be able to explore the data, determine how to proceed and decide what to do next. **Data visualization** will also be the key process to present and explain my analysis in an organized fashion.

---

## Exploratory Data Analysis (EDA) 🧩

Before diving into statistical testing, I will conduct **exploratory data analysis (EDA)** to better understand my chess data. This process will involve:

- **Summarizing the dataset,** understanding **distributions**, **correlations**, **relations** between the paramaters of the data.
- **Handling missing values** and **data cleaning** to ensure the reliability of my analysis.
- **Identifying outliers and anomalies** that may indicate unusual performance trends, and therefore damage the hypothesis testing process by potentially driving the analyze into wrong conclusions.

## Findings from the EDA 🧮

There exists differences in compared graphs of Win and Loss games regarding the average time spent each game. As an initial thought, this may suggest that I could observe results in favor of the Alternative Hypothesis, of course further checks must be done.

![image](https://github.com/user-attachments/assets/c1b13e67-7c5e-4ccb-827d-91d989aec179)

I observed that a uniform-like ditribution occurs in the following plot, regardless of the outcome of the game. Below is the plot of the data points in winning games. Please check the `main.ipynb` for other categories' plots. The x-axis represent the move numbers, while the y-axis represents the time spent on completing that particular move.

![image](https://github.com/user-attachments/assets/d40be7ee-bb95-4d6e-915d-ef060d635047)

Both of the graphs follow a right skewed uniform-like distribution, indicating there exists a pattern of time spent per move in particular moves. Note that histograms may be hard to read because of the high frequencies in the first few moves, that is why I use over-plotting transparent scatter plots to better understand the nature of the data in this case.

*Please head to the `main.ipynb` file for detailed EDA and findings.*

---

## Hypothesis 💡

The analyzed data will be used to support or deny hypotheses like:

### Signature Time Pattern of the Winning Games

***Null Hypothesis (H₀):*** There is **no distinct, unique pattern** in the time I spend on each move in the games I won when the moves of the whole game are divided into equal phases. The time distribution pattern in winning games **does not differ** significantly from the time distribution pattern observed in games I lost. Any observed difference between winning and losing games is **due to random variation** rather than consistent patterns.

***Alternative Hypothesis (H₁):*** The time I spend on each move in the games I won follows **a unique, distinct pattern** when the moves of the whole game are divided into equal phases, and this pattern differs significantly from the time distribution pattern observed in games I lost. 

- This **signature pattern**, if confirmed, can serve as a predictive indicator of my game outcome during play, giving me a powerful tool to assess my **winning probability** based on how closesly my current time usage matches my established **winning pattern**.
- Does this **pattern** change with different **time controls** or not?

---

## Hypothesis Testing Results 🧪

After preparing the data, I conducted hypothesis tests for each **time class** category. For each category, each move is tested separately using two sample t-tests to determine if the difference between the Win and Loss games are significant. The significance level was accepted as constant *0.05*.

### All Games

Firstly, I conducted hypothesis tests for all of the Blitz, Bullet, and Rapid games together.
Out of 73 successful t-tests (meaning 74th move did not contain enough data), only 15 p-values observed were under the significance level. This implies that there is no strong pattern difference in Win and Loss games category-wise. We **fail to reject** the **Null Hypothesis** based on this result.

### Blitz Games

The data of **Blitz Games** yielded a result with more significant p-values. Out of 72 successful t-tests, 23 p-values were found to be falling under the significance level. Although at the first glance, this result appears to be leading us to **fail to reject** the **Null Hypothesis**, which is the case in actuality; it is better that we observe a plot of the p-value distribution among the moves. This is because 23 p-values, even though not enough to imply a proof to reject the Null Hypothesis, are still a considerable amount.

![image](https://github.com/user-attachments/assets/59be7742-1a6a-41e3-aa12-f1b72fcc3ea1)

Once the p-value plot is observed, it would appear that there are spesific intervals that for which I could assess the rejection of the Null Hypothesis just on those move intervals. We can see from the graph that roughly between moves 1 and 25 there is a high concentration of significant p-values. This is also the case with the interval of 50th-60th moves.

### Bullet Games

The **Bullet Games** data yielded a similar result with the Blitz Games data. Out of 64 successful t-tests, 23 p-values were found to be falling under the significane level. Again, we **fail to reject** the **Null Hypothesis**. But very similar to our previous analysis, the **Bullet Games** also yields a plot of spesific p-value concentrated intervals, that suggests the Null Hypothesis may be rejectable for that intervals.

### Rapid Games

The data of **Rapid Games** however, yielded a surprising result. I observed that out of 65 successful t-tests, only 2 p-values were significant. This observation immediately led me to directly **fail to reject** the **Null Hypothesis**, without even checking spesific intervals, unlike the previous **time class** categories' tests.

*Please head to the `main.ipynb` file for detailed results and insights.*

---

## Machine Learning Applications and Future Work 🤖

After collecting data, conducting EDA, and applying hypothesis tests; I will be using **machine learning** applications to investigate potential predictive models based on the data, and the results of the hypotheses.


---
*This project utilizes data from chess.com and lichess.org, analysis powered by Stockfish, assistance from ClaudeAI and ChatGPT*

