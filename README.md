# TVX CTF 2026 Writeup (OSINT)


## Table of Contents
- [ASKME](#askme)
- [Digital Currencies](#digital-currencies)

---

## ASKME

![Inventory screenshot](https://github.com/LIMJH9032/TVX-CTF-2026-WRITEUP-LIM-/blob/main/inventory(ASKME).png?raw=true)

### Approach
1. The first thing I noticed was that the number of diamonds changes between photos. I tried using the sequence of changes, `6015531436920`, as the password, but it failed.
2. I looked at the challenge title again, and *ASKME* sounds like **ASCII**.
3. I took the **sum of the diamonds in each photo** and converted each sum to an ASCII character. Together they form the password.

### Password
```
F@OuNdIT
```

### Flag
![Flag screenshot](https://github.com/LIMJH9032/TVX-CTF-2026-WRITEUP-LIM-/blob/main/Flag(ASKME).png?raw=true)

---

## Digital Currencies

### Challenge
A routine transaction approved at 10:00 AM was the start of one of the largest cybercrimes involving digital currencies. The attackers got into the digital vaults "without breaking a single lock", and some of the stolen funds are still missing. The task is to find:
1. The name of the platform
2. The date of the event
3. The amount stolen

### Approach
I started with the recent **Binance hack**, but it turned out to be incorrect. I kept searching and found a write-up of the **2025 Bybit hack**, which matched every clue:

| Clue | Match |
|------|-------|
| Routine transaction approved | Bybit's signers approved a disguised transaction |
| Vaults breached without breaking a lock | The attackers took over a multisig cold wallet |
| Funds still stolen | The funds were laundered quickly and mostly not recovered |
| Over 100 million | About $1.46B in ETH |

> ### ⭐ 2. Bybit: $1.46B in ETH stolen in 2025 hack
>
> On February 21, 2025, Dubai-based Bybit lost about 400,000 ETH, worth $1.46B, in what was then the largest crypto theft in history. As we set out in our [breakdown of the Bybit exchange hack](https://crystalintelligence.com/investigations/breaking-down-the-bybit-exchange-hack/), attackers manipulated Bybit into approving a transaction that gave them control of a multisig cold wallet. In effect, they replaced Bybit's vault keys with their own, giving them free access to its funds.
>
> The attack began at 14:15 UTC on a Friday, as the UAE working day ended. A 90 USDT test transaction came first. One minute later, 401,347 ETH, 90,375 stETH, 15,000 cmETH, and 8,000 mETH left the wallet. Within 14 minutes, the attackers were swapping tokens for ETH through DeFi services and splitting funds across addresses.
>
> Bybit confirmed the attack on X at 15:51 UTC and asked the industry for help. The next day, CEO Ben Zhou launched a [bounty of up to 10%, or about $140M](https://crystalintelligence.com/news/bybit-offers-10-bounty-to-solve-1-5b-crypto-heist/), for help recovering the funds. On February 26, the FBI attributed the theft to North Korea's TraderTraitor.
>
> The response set a new standard for cooperation between exchanges, analytics firms, and law enforcement. Our [breakdown of how the hackers took control](https://crystalintelligence.com/investigations/the-bybit-heist-how-the-hackers-took-control/) covers what exchanges can learn from it.

### Answers
- **Platform:** Bybit
- **Date:** 21/2/2025
- **Amount stolen:** 1.5 billion

### Flag
```
TVX{bybit,21/2/2025,1.5billion}
```
