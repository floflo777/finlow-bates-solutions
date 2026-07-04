# EN_hard_2

- **Target:** `161YgNX2NrCzGunWvoV1hN3DuzWeuovBK3` (0.002 BTC)
- **Edition:** English
- **Family:** figure and deduced (uncompressed P2PKH)
- **Swept:** [c46c70fb](https://mempool.space/tx/c46c70fb04a2faeebde24057b22a547da7b309fd33b74b3d77181943a02b45d0), 2026-06-25

## The clue

A figure in the hash-functions chapter shows a one-time-password pad: seven printed 256-bit
hashes, presented as a chain built from an altered pangram. The phrase in the figure is a
deliberate red herring (it is visibly not the canonical pangram), which is the tell that the
figure, not the phrase, is the payload.

## The insight

The key is not a hash of any text. It is the seven printed hashes themselves, combined.
XOR-ing the seven 256-bit rows together produces a single 32-byte value, and that value is
the private key. This is a different transform class from the mnemonic puzzles: a printed
table of numbers combined directly into a raw key.

## The transform

```
seven printed 256-bit hashes
  -> XOR all seven together
  -> 32-byte private key
  -> uncompressed P2PKH
```

## Key material (spent)

- private key (hex): `9dd0f77d3cc6746cdfe779de61499a88ba4a7fc6a53f90dc276a0c2826679be8`
- WIF (uncompressed): `5K1nnZxtT1kDxbzjkwK6GUYBWApcUMDpLVpKNgSvpGxLYhruRTB`
- derived address: `161YgNX2NrCzGunWvoV1hN3DuzWeuovBK3`, exact match to target

## Verification

The seven rows read off the figure, XOR-ed in printed order, give the private key above,
whose uncompressed P2PKH address is the target. Reading the exact hash digits off the page is
the one place a clean digital copy of the figure helps, since a single wrong nibble breaks the
result.

## Lesson carried forward

Not every clue lives in the chapter its puzzle is named for, and not every answer is a
brainwallet. "Combine the printed numbers in a figure" became a transform class to test
against every table and grid of numbers in the book.
