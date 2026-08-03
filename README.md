# Game of Life refactoring kata in C++

[![CI](https://github.com/Coding-Cuddles/game-of-life-refactoring-cpp-kata/actions/workflows/main.yml/badge.svg)](https://github.com/Coding-Cuddles/game-of-life-refactoring-cpp-kata/actions/workflows/main.yml)
[![C++17](https://img.shields.io/badge/C%2B%2B-17-blue.svg)](https://en.cppreference.com/w/cpp/17)
[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

Refactor Conway's Game of Life toward the Liskov Substitution Principle
without changing its behavior. Setup is complete when all five starter tests
pass.

## Overview

This kata complements [Clean Code: SOLID, Ep. 11 - Liskov Substitution Principle](https://cleancoders.com/episode/clean-code-episode-11-p1).

This repository contains two exercises designed to improve your skills in
code refactoring, with a focus on the Liskov Substitution Principle (LSP).

## Instructions

### Exercise 1

The Game of Life is a cellular automaton devised by the British mathematician
John Horton Conway in 1970. The game is a zero-player game, meaning that its
evolution is determined by its initial state, requiring no further input.

You have a code base that simulates the Game of Life, but it does not adhere to
the LSP. Your task is to refactor the code to align with the LSP. This means,
among other things, that you should be able to replace any instance of a parent
class with an instance of one of its child classes without altering the
correctness of the program.

**Instructions:**

1. Review the current code base and identify parts that violate the LSP.
2. Refactor the violating code to align with the LSP.
3. Make sure all the tests still pass after your refactoring.

Be sure to run the tests before and after your refactoring to make sure you
haven't changed the game's behavior.

### Exercise 2

For those who complete the refactoring in the first part of the class, a second
exercise is available. Your task is to extend the original code with new types
of cells.

Here are the new cell types to implement:

1. **Immortal Cell**: This cell type never dies. Once born, it stays alive
   through all the subsequent generations.
2. **Reproductive Cell**: This cell type reproduces faster than a normal cell.
   It can make a new cell in the neighborhood with 2-3 neighbors instead of
   three.
3. **Lazy Cell**: This cell type requires more neighbors to survive. It stays
   alive only if it has exactly three neighbors.

## Prerequisites

Required:

- [Git](https://git-scm.com/downloads)
- A compiler with C++17 support. Choose one:
  - [GCC](https://gcc.gnu.org/) 10+ on Linux
  - [LLVM Clang](https://llvm.org/) 14+ on Linux
  - [Apple Clang](https://developer.apple.com/xcode/) 17+ on macOS
  - [MSVC](https://visualstudio.microsoft.com/) 2022 on Windows
- [CMake 3.24 or later](https://cmake.org)

Optional:

- [GNU Make](https://www.gnu.org/software/make/), for shorter commands. Every
  required task also has direct CMake and CTest commands. Make may be
  unavailable on Windows.

You do not need to install GoogleTest separately. CMake finds an installed
copy or downloads the pinned release when needed.

## Set up the kata

1. Clone the repository:

   ```console
   git clone https://github.com/Coding-Cuddles/game-of-life-refactoring-cpp-kata.git
   ```

2. Enter the repository directory:

   ```console
   cd game-of-life-refactoring-cpp-kata
   ```

3. Run the starter tests. Use Make when it is installed:

   ```console
   make test
   ```

   Otherwise, use CMake and CTest directly:

   ```console
   cmake -S . -B build -DCMAKE_BUILD_TYPE=Debug
   cmake --build build --config Debug
   ctest --test-dir build --build-config Debug --output-on-failure
   ```

The first run may download and build GoogleTest. CTest should report
`100% tests passed`.

If a command reports a missing compiler or CMake, install that prerequisite
and run the setup commands again.

Setup is complete when CTest reports `100% tests passed`.

## Work on the kata

1. Refactor `game.h` while preserving the behavior covered by
   `test_game.cpp`.

2. Run the tests after each change. Use Make when it is installed:

   ```console
   make test
   ```

   Otherwise, use CMake and CTest directly:

   ```console
   cmake --build build --config Debug
   ctest --test-dir build --build-config Debug --output-on-failure
   ```

   Continue when CTest reports `100% tests passed`.

## Make command reference

Make is optional. Run `make` or `make help` to list these commands in the
terminal.

| Command             | Result                                    |
| ------------------- | ----------------------------------------- |
| `make all`          | Build and run the test suite              |
| `make help`         | Show the Make command reference           |
| `make build`        | Configure and build without running tests |
| `make test`         | Build and run the test suite              |
| `make format`       | Format tracked C++ and header files       |
| `make format-check` | Check formatting without changing files   |
| `make clean`        | Remove generated build artifacts          |
