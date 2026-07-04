# IT_medium

- **Target:** `1Q78hDeaHXQbuCSQxG1uPAc4V3jsuVUG9r` (0.002 BTC)
- **Edition:** Italian
- **Family:** mnemonic (compressed P2PKH)
- **Swept:** [914a8251](https://mempool.space/tx/914a825138f943fc357b5a026b607b3c62bf67d5997043761711aaeabf5cab49), 2026-07-01

## The clue

The Italian edition prints its own 12-word example phrase in the same entropy passage where
the English edition prints the EN_hard_1 phrase. Same location in the book, different content.
That is the signal: the Italian edition planted its own puzzle in the slot occupied by the
English one. The same footnote about the last word carrying a checksum is served to the
Italian reader.

## The insight

The twelve printed words are English words, but they do not form a valid BIP39-English
mnemonic. The Italian text also quietly drops the word "English" from the description of the
2048-word list that the English edition includes. BIP39 has an official Italian wordlist.
Translating each printed English word to its Italian BIP39 equivalent produces a valid
BIP39-Italian mnemonic. This is the localization pattern the Italian edition uses throughout:
the puzzle language itself is translated.

## Disambiguation

Most of the twelve words have a single natural Italian BIP39 translation. Four are ambiguous,
with two plausible candidates each (for example watch to orologio or guardare). That is 64
combinations. Exactly four are checksum-valid, and exactly one of those derives the target
address, so the checksum and the address together pin down a unique answer. No deliberate flaw
or repair is needed here, unlike EN_hard_1: the checksum is clean.

## The transform

```
twelve printed English words
  -> translate each to its official BIP39-Italian word
  -> valid BIP39-Italian mnemonic (empty passphrase)
  -> BIP44 m/44'/0'/0'/0/0
  -> compressed P2PKH
```

## Key material (spent)

- private key (hex): `578df2fef081d6c5430a5a815515412930ee5d6cf6b0f92aab04a4a121067ecd`
- WIF (compressed): `Kz9uTuc4bo9FczbmcuAeuXqeV9AHQnpV8U56dKeepoKxnqccDboF`
- derived address: `1Q78hDeaHXQbuCSQxG1uPAc4V3jsuVUG9r`, exact match to target

## Verification

The BIP39-Italian wordlist was pinned by hash and cross-checked identical between the
bitcoin/bips repo and trezor/python-mnemonic. From the winning mnemonic, a full derivation and
a WIF round-trip both reproduce the target address. This is the localized twin of EN_hard_1:
same artifact, translated language, same BIP44 and compressed template.
