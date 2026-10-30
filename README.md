# Wheel Merge

A fast arcade merge game powered by **Squeekchain**, the hamster-powered proof-of-work blockchain.

Hamsters sit on a 12-slot wheel. Drop the next hamster into the targeted slot: two neighbours of the
same level merge into the next level, in chains, up to the Legend. The timer is tight, and every merge
buys back a little time.

## Powered by the real hamster

- **Live wheel.** In Live mode the wheel turns at the real speed of Squeektoshi's wheel, read from
  Squeekchain's public status API. When he sleeps, you turn the wheel yourself.
- **Real blocks.** Every completed Squeekchain block drops a ★ joker into your queue.
- **On-chain stamp.** Every saved score is stamped with the Squeekchain block height, read on-chain
  from the SqueekCore contract at the moment of submission.

## Modes and leaderboards

| Mode | Wheel |
|---|---|
| Live | Squeektoshi's real wheel |
| Auto-spin | Simulated running wheel (practice) |
| Manual | Simulated sleeping wheel, turned by the player (practice) |

Each mode has its own **weekly** leaderboard (new season every Thursday 00:00 UTC) and **all-time**
leaderboard, stored on Sepolia.

## What players sign

Playing needs no wallet. Saving a score is optional and sends **one** transaction on the **Sepolia
testnet**:

- function: `submitScore(mode, score, maxLevel, nickname, version)`
- value: **0 ETH** (only a small fee in free Sepolia test ETH)
- no token access, no approvals, no signature of messages

The game shows a full summary before the wallet opens and refuses to send anything outside Sepolia.

## Contracts (Sepolia)

| Contract | Address |
|---|---|
| Wheel Merge Leaderboard | [`0xa66c68edd8df3090557ab677444f8f0e1fa0df06`](https://sepolia.etherscan.io/address/0xa66c68edd8df3090557ab677444f8f0e1fa0df06) · [verified source](https://repo.sourcify.dev/11155111/0xa66c68edd8df3090557ab677444f8f0e1fa0df06) |
| SqueekCore (Squeekchain) | [`0x980b4424c007caf7a1f3670b48c8eaef7ebc3d44`](https://sepolia.etherscan.io/address/0x980b4424c007caf7a1f3670b48c8eaef7ebc3d44) |

The leaderboard holds no funds and accepts no ETH. Its owner can moderate (remove entries, exclude
addresses, pause submissions), reset leaderboards and tune the game rules.

## Running locally

This repository is the static build of the game: serve the folder with any static server, for example

```bash
python -m http.server 8080
```

then open `http://localhost:8080/`.

## License

MIT for the game code. Third-party components are listed in `THIRD_PARTY_NOTICES.md`.
