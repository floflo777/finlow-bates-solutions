# EN_hard_1

- **Target:** `181rPpfdUGFg4fVEdhDZEfDbBSqgigtoZR` (0.002 BTC)
- **Edition:** English
- **Family:** mnemonic (compressed P2PKH)
- **Swept:** [b6e064aa](https://mempool.space/tx/b6e064aa8fde1153c342e2f7d98bce09e004bef5ac8db8f0138601289ceae69a), 2026-06-18

## The clue

The chapter on entropy and private keys prints a 12-word phrase as an example mnemonic. It
looks like an incidental illustration, but a footnote a few pages later points out that the
last word of a BIP39 phrase carries a checksum. That footnote is the signpost: the printed
phrase is the puzzle, and its last word is where to look.

## The insight

Taken verbatim, the printed phrase fails its BIP39 checksum. The last word is a deliberate
red herring, altered by one word from the correct one. Correcting it to the nearest
checksum-valid neighbour (a single-word edit) yields a valid mnemonic. No spraying required:
the checksum itself tells you when the repair is right, and only one nearby word satisfies it.

## The transform

```
repaired 12-word BIP39 phrase
  -> BIP39 seed (empty passphrase)
  -> BIP44 m/44'/0'/0'/0/0
  -> compressed P2PKH
```

## Key material (spent)

- private key (hex): `bb7431f0773cdef6bce0483556b4ad90ec85e4ea4a7d2aad0529b0d571b8bffb`
- WIF (compressed): `L3W6ZhE2uqHg4e1yrj6vUZTvykYaiMSg1VNyD8CfVTy1zkfVKzcj`
- derived address: `181rPpfdUGFg4fVEdhDZEfDbBSqgigtoZR`, exact match to target

## Verification

Two independent paths agreed: WIF to compressed P2PKH, and a full `bip_utils` re-derivation
from the repaired mnemonic. Both produced the target address exactly.

## Why it is the keystone

This is the only puzzle where the mechanism was legible from the start, and it defines the
mnemonic family: a printed phrase, one deliberate flaw, a nearby fix-hint, standard BIP44,
compressed. IT_medium turned out to be the Italian-localized twin of this exact artifact.
