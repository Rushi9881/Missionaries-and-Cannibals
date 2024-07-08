# Missionaries and Cannibals Game

This project is a simple console-based implementation of the classic Missionaries and Cannibals problem using Python. The goal of the game is to get all missionaries and cannibals across the river without ever leaving a group of missionaries in one place outnumbered by cannibals, as the cannibals would eat them.

## Table of Contents

- [Project Description](#project-description)
- [Game Rules](#game-rules)
- [Prerequisites](#prerequisites)
- [How to Play](#how-to-play)
- [Example Run](#example-run)
- [Contributing](#contributing)

## Project Description

The Missionaries and Cannibals game is a problem in which the player needs to move three missionaries and three cannibals across a river using a boat. The boat can carry at most two people at a time, and at no point can the number of cannibals on either side of the river outnumber the missionaries.

## Game Rules

1. The boat can carry one or two people.
2. At no point should the number of cannibals be greater than the number of missionaries on either side of the river.
3. The game ends when all missionaries and cannibals are safely on the left side of the river.
4. If the player makes a move that results in the missionaries being outnumbered by cannibals on either side, they lose the game.

## Prerequisites

- Python 3.x

## How to Play

1. Run the Python script.
2. Enter the number of missionaries and cannibals you want to move across the river.
3. Follow the prompts to continue moving until all are safely across or until an invalid move is made.

## Example Run

```python
boat_side = 'Right'
missionaries_on_right = 3
cannibals_on_right = 3 
missionaries_on_left = 0
cannibals_on_left = 0 
M = '\U0001f482'
C = '\U0001f479'
W = '\U0001f30a'
B ='\U0001f6A2'

print('M=',missionaries_on_left * M, 'C=',cannibals_on_left  * C, "|", W,W,W,W,B ,"| ", 'M=',missionaries_on_right * M,'C=',cannibals_on_right * C )

while True:

    missionaries = int(input('No of missionaries or enter 10 to quit : '))
    if missionaries == 10:
        print('You Quit. Game Over!')
        break
    cannibals = int(input('No of cannibals : '))

    if (missionaries + cannibals) != 1 and (missionaries + cannibals) != 2:
        print('Invalid Move')
        continue


    if boat_side == 'Right':
        if missionaries_on_right < missionaries or cannibals_on_right < cannibals :
            print('Invalid Move')

        missionaries_on_right = missionaries_on_right - missionaries
        cannibals_on_right = cannibals_on_right - cannibals

        missionaries_on_left += missionaries
        cannibals_on_left += cannibals
        
        print('M=',missionaries_on_left * M, 'C=',cannibals_on_left * C, '|',B,W,W,W,W,'|','M=',missionaries_on_right * M ,'C=',cannibals_on_right * C)
        
        boat_side = 'Left'

    else:
        if missionaries_on_left < missionaries or cannibals_on_left < cannibals:
            print('Invalid Move')
            
            
        missionaries_on_left = missionaries_on_left - missionaries
        cannibals_on_left = cannibals_on_left - cannibals

        missionaries_on_right += missionaries
        cannibals_on_right += cannibals
        
        print('M=',missionaries_on_left * M, 'C=',cannibals_on_left  * C, "|", W,W,W,W,B ,"| ", 'M=',missionaries_on_right * M,'C=',cannibals_on_right * C )

        boat_side = 'Right'

    if (missionaries_on_right < cannibals_on_right and missionaries_on_right > 0) or (missionaries_on_left < cannibals_on_left and missionaries_on_left > 0):
        print('You Loose')
        break

    if(missionaries_on_left == 3 and cannibals_on_left == 3):
        print('You win')
        break
