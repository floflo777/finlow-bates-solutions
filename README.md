# Finlow-Bates book puzzles: solutions

Kary Finlow-Bates hid Bitcoin private keys inside his book *Move Over Brokers Here Comes The
Blockchain*. Each key was funded with **0.002 BTC** (200,000 sat) and claimable by whoever
read the book closely enough to reconstruct it. There is no public solver writeup for any of
them, and they had sat unsolved for roughly 4 years.

This repo documents **4 I solved and swept**, across both the English and Italian editions,
for **0.008 BTC** in total. The amounts are small on purpose. The point is the mechanism
behind each one.

Out of respect for the book's copyright, nothing here reproduces its pages, figures or text.
Each writeup describes the reasoning and the derivation only. If you want to verify a solve,
you need your own copy of the book.

| Puzzle | Edition | Mechanism | Target | Sweep |
|---|---|---|---|---|
| [EN_hard_1](./solutions/EN_hard_1.md) | English | Planted BIP39 mnemonic, one altered word | `181rPpfdUGFg4fVEdhDZEfDbBSqgigtoZR` | [b6e064aa](https://mempool.space/tx/b6e064aa8fde1153c342e2f7d98bce09e004bef5ac8db8f0138601289ceae69a) |
| [EN_hard_2](./solutions/EN_hard_2.md) | English | XOR of seven printed hashes | `161YgNX2NrCzGunWvoV1hN3DuzWeuovBK3` | [c46c70fb](https://mempool.space/tx/c46c70fb04a2faeebde24057b22a547da7b309fd33b74b3d77181943a02b45d0) |
| [IT_medium](./solutions/IT_medium.md) | Italian | English to Italian BIP39 wordlist translation | `1Q78hDeaHXQbuCSQxG1uPAc4V3jsuVUG9r` | [914a8251](https://mempool.space/tx/914a825138f943fc357b5a026b607b3c62bf67d5997043761711aaeabf5cab49) |
| [IT_hard](./solutions/IT_hard.md) | Italian | Four cities from the Italian-only acknowledgements, triple SHA-256 | `1QExGvuieS9MvuKC3R1qjp6jGTVcqisTDj` | swept |

## What makes these hard

There is no single algorithm. Each puzzle is a two-step problem.

First, the lateral answer: a phrase, a figure, or a detail you only get by reading the book
the way the author thinks. This is the part that resists brute force. The answer is meant to
feel obvious after you see it and impossible before.

Second, the answer to key transform: a simple, human-doable operation the book hints at,
such as repairing a checksum, hashing three times, XOR-ing a table, or translating a
wordlist. Once you have the right answer, the transform is short.

The recurring trap is to attack the second step with a machine, spraying `sha256^n` over
every n-gram in the book. That fails even on the puzzles I later solved by hand. The book is
a reading problem, not a compute problem.

## The two families

- **Mnemonic family** (EN_hard_1, IT_medium): the answer is a 12-word BIP39 phrase the book
  prints or implies. Derive via BIP44 `m/44'/0'/0'/0/0`, compressed P2PKH.
- **Figure and deduced family** (EN_hard_2, IT_hard): the answer produces a raw 32-byte key
  directly, by XOR-ing a table or triple-SHA256 of a phrase. Uncompressed P2PKH.

Knowing which family a puzzle belongs to, and that the Italian edition localizes its puzzles
rather than copying them, is most of the battle. Each writeup gives the full reconstruction:
the clue, the insight, the transform, the derived key, and the sweep.

Solved and documented by [@0xFlorent_](https://twitter.com/0xFlorent_). All four rewards were
swept to a single personal wallet, so the keys shown in the writeups are spent.
