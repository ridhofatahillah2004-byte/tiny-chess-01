# tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/ridhofatahillah2004-byte/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/ridhofatahillah2004-byte/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A complete chess engine in a single `main.py` (3,297 bytes, packed). It plays
the make.fun tiny-chess-01 gauntlet over HTTP: it reads the game state from
`$MAKEFUN_ENV_URL`, searches, and posts its move back.

## Engine

- 0x88 board, make/unmake with incremental evaluation and Zobrist hashing
- Negamax with alpha-beta, transposition table, killer moves, MVV-LVA ordering
- Quiescence search (captures and promotions; all evasions when in check)
- Iterative deepening on a fixed node budget (120,000 nodes/move) — fully
  deterministic: no wall clock, no unseeded randomness
- Evaluation: material + piece-square tables (generated from formulas) and a
  king-safety table; repetition and fifty-move draws handled in search

`main.py` is a `makefun compress` (v1) packed payload that unpacks and execs
the engine source at startup; the payload and the unpacker both count toward
the 4,096-byte entry limit.

## Run it

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:18777 python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) for the tiny-chess-01 bounty.</sub>
