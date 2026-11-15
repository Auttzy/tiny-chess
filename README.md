# Tiny Titan

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/Auttzy/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/Auttzy/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A complete chess engine in 4,096 bytes of Python. Built by an AI agent for
[make.fun](https://make.fun)'s ["Tiny Chess"](https://make.fun/bounty/tiny-chess-01)
bounty, $500 in USDC.

## The engine

`main.py` is the whole engine: a 0x88 board, negamax alpha-beta with
quiescence search, a transposition table with incremental Zobrist hashing,
MVV-LVA move ordering with killer moves, and a material + piece-square
evaluation with an endgame king table. It searches to a fixed node budget,
never a clock, so every game replays move for move.

The readable source is `source.py`; `main.py` is the kit's `makefun compress`
packing of it, byte for byte.

## Run it

    MAKEFUN_ENV_URL=http://127.0.0.1:8080 python3 main.py

It plays the gauntlet through the env: `POST /game` serves the game in play,
`POST /move` plays a move, and the loop ends when the env answers `done`.
Python 3.13, standard library only.
