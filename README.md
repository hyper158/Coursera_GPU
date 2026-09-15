# Coursera_GPU
Project Overview

This project is a CUDA-based Tic-Tac-Toe game where two GPU-based competitors play against each other.

The game uses CUDA to evaluate multiple board positions in parallel and select suitable moves. Player X follows an offensive strategy, while Player O follows a defensive strategy that can block the opponent and identify winning moves.

Since the development environment provides one physical GPU, the two competitors are implemented as separate host threads that take synchronized turns using the GPU.

Technologies Used
C++
CUDA
NVIDIA GPU
CUDA Runtime API
Multithreading
Mutex and Condition Variable
How the Game Works

The game uses a standard 3×3 Tic-Tac-Toe board.

GPU Player X: Uses an offensive strategy.
GPU Player O: Uses a defensive strategy.
CUDA Threads: Evaluate the nine board positions.
Move Scoring: Each available position receives a score based on the strategy.
Synchronization: The two competitor threads take turns using a shared game board.
Game Result: The game ends when a player wins or the board becomes full.
GPU-Based Move Evaluation

For every turn, a CUDA kernel is launched with multiple threads. Each thread evaluates one board position.

Player X gives higher priority to:

Immediate winning moves
Center position
Corner positions
Other available positions

Player O gives higher priority to:

Immediate winning moves
Blocking Player X
Center position
Corner positions
Other available positions

The position with the highest score is selected as the next move.

Synchronization

The two GPU competitor threads use a shared game board. A mutex and condition variable are used to control the turn order.

This prevents both competitors from modifying the board at the same time and ensures that X and O play in the correct sequence.

Output

The program displays:

Detected CUDA GPU
CUDA capability
Current player
Player strategy
CUDA kernel execution
Selected board position
Move score
Updated Tic-Tac-Toe board
Final winner or draw
Example Environment

The project was tested using an NVIDIA Tesla T4 GPU with CUDA support in Google Colab.

The implementation also follows the single-GPU approach allowed by the assignment, where two GPU-based competitors take synchronized turns.

Project Demonstration

The demonstration video shows the complete game execution, including CUDA kernel execution, synchronized turns, board updates, move selection, and the final game result.

Files
gpu_tictactoe/
└── gpu_tictactoe.cu
Compilation
nvcc -std=c++17 gpu_tictactoe/gpu_tictactoe.cu -o gpu_tictactoe_app
Execution
./gpu_tictactoe_app
Project Objective

The main objective of this project is to demonstrate how GPU computing and parallel execution can be applied to a simple game. It also demonstrates CUDA kernels, parallel board evaluation, multithreading, synchronization, and GPU-based decision making.
