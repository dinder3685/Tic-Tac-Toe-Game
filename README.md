Tic-Tac-Toe Game State Checker

Overview

This project implements a simple Tic-Tac-Toe game state checker in C. It determines whether the game has been won by 'X' or 'O', is still ongoing, or has ended in a draw.

Features

Checks rows, columns, and diagonals for a winner.

Detects unfinished games if empty squares exist.

Returns correct game state (X_WON, O_WON, DRAW, or NOT_FINISHED).

Code Implementation

#include <stdio.h>

// Enum for game state
enum game_state { NOT_FINISHED = -1, DRAW = 0, X_WON = 1, O_WON = 2 };
// Enum for board squares
enum square { EMPTY = 0, X = 1, O = 2 };

// Function to check game state
enum game_state check_game_state(const enum square board[3][3]) {
    // Check rows & columns
    for(int i = 0; i < 3; i++) {
        if(board[i][0] == board[i][1] && board[i][0] == board[i][2] && board[i][0] != EMPTY) return board[i][0];  // Row win
        if(board[0][i] == board[1][i] && board[0][i] == board[2][i] && board[0][i] != EMPTY) return board[0][i];  // Column win
    }
    // Check diagonals
    if(board[0][0] == board[1][1] && board[0][0] == board[2][2] && board[0][0] != EMPTY) return board[0][0];
    if(board[0][2] == board[1][1] && board[0][2] == board[2][0] && board[0][2] != EMPTY) return board[0][2];
    
    // Check for unfinished game
    for(int i = 0; i < 3; i++)
        for(int j = 0; j < 3; j++)
            if(board[i][j] == EMPTY) return NOT_FINISHED;
    
    return DRAW;
}

Example Usage

int main() {
    enum square board[3][3] = {
        {X, O, X},
        {O, X, O},
        {O, X, X}
    };
    
    enum game_state result = check_game_state(board);
    
    if (result == X_WON) printf("X won!\n");
    else if (result == O_WON) printf("O won!\n");
    else if (result == DRAW) printf("Game is a draw.\n");
    else printf("Game is not finished.\n");
    
    return 0;
}

Future Improvements

Implement a full Tic-Tac-Toe game with player moves.

Add AI opponent using minimax algorithm.

Convert to GUI version with a simple interface.

Contributing

Feel free to fork this repository and improve the code! Pull requests are welcome. 🚀
