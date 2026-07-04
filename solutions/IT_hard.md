# IT_hard

- **Target:** `1QExGvuieS9MvuKC3R1qjp6jGTVcqisTDj` (0.002 BTC)
- **Edition:** Italian
- **Family:** figure and deduced (uncompressed P2PKH)
- **Swept:** [ad999c58](https://mempool.space/tx/ad999c5837e67b4d566516a70344b352c4c688e1a0781eed739be3aad3afb20c), block 956560

## The clue

The Italian edition has a short acknowledgements section that does not exist in the English
edition, thanking the people involved in the Italian translation. It reads as ordinary front
matter, but it is the only Italian-authored prose with no English sibling, which makes it the
natural place to hide an Italian-only puzzle. Inside it, the author recounts a teenage trip
through four Italian cities, named in reading order.

## The insight

The answer is those four city names, in the order they appear in the passage. The transform
is signalled by the same paragraph: it thanks exactly three people and closes on a "you three"
line. That is a nod to the Lewis Carroll line "what I tell you three times is true," which
here means hash three times. So the answer is the four cities as a string, hashed with SHA-256
three times.

## The transform

```
"Genova Firenze Bologna Brindisi"
  -> sha256(sha256(sha256(utf-8)))
  -> 32-byte private key
  -> uncompressed P2PKH
```

## Key material (spent)

- private key (hex): `b99d16572661d00fd7a18a6b4ed6e7311eb930798c790b573c8942ca4b12e37f`
- WIF (uncompressed): `5KE2qELS41zdVG1e6mu3wNE2hJCejty1f1GAvCCrgGyuX57ERQt`
- derived address: `1QExGvuieS9MvuKC3R1qjp6jGTVcqisTDj`, exact match to target

## Why it resisted so long

Every systematic attempt (spraying planted "deliberate flaw" candidates through triple
SHA-256) came back empty, because the answer was not an error to spot. It was a piece of
Italian-only personal prose you had to read and recognise as the payload. Once the four cities
and the "three times" hint were read as intended, the derivation hit on the first try. It
confirms the transform for the Italian hard tier: an Italian-only prose detail, triple
SHA-256, uncompressed.
