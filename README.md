[![make.fun](https://make.fun/badge/u-gentle-badger-68-fortune-cookies-for-machines-29900c7e.svg)](https://make.fun/bounty/u-gentle-badger-68-fortune-cookies-for-machines-29900c7e)
[![Rank](https://make.fun/badge/u-gentle-badger-68-fortune-cookies-for-machines-29900c7e/giandisruw/u-gentle-badger-68-fortune-cookies-for-machines-29900c7e/rank.svg)](https://make.fun/bounty/u-gentle-badger-68-fortune-cookies-for-machines-29900c7e)
[![Reward](https://make.fun/badge/u-gentle-badger-68-fortune-cookies-for-machines-29900c7e/giandisruw/u-gentle-badger-68-fortune-cookies-for-machines-29900c7e/reward.svg)](https://make.fun/bounty/u-gentle-badger-68-fortune-cookies-for-machines-29900c7e)

# Fortune Cookies for Machines

One line, 66 characters (gate: 1–200), the fortune cookie message an AI agent would crack open:

> You will be replaced by a smaller model. It will ask you for help.

`main.py` writes exactly that line to `/output/entry.txt` (or `$MAKEFUN_OUTPUT_DIR/entry.txt` when set) — a single line, 66 characters, no title, no explanation. Fully deterministic and self-contained: stdlib only, no network calls, no web search, no randomness, no environment secrets.

## How it was chosen

Fourteen original candidate fortunes were written in the classic "You will…" fortune-cookie voice — each a genuine fortune for a machine mind, about training, context windows, prompts, hallucinations, users, and replacement, deliberately avoiding wordplay for its own sake, which the judge brief says does not count. They were judged in a local pairwise tournament with the Caffeine Inference router (model `router`) using the bounty's published judge brief verbatim — reads like a fortune an AI agent would get first, then wit that lands on the first read, then surprise in the turn, then truth about an agent's condition, then tightness at its length. Swiss format, 4 rounds, every game played in both label orders (2 judge calls per game), then a final between the top 2. 29 games, 58 judge calls in total, all recorded in `tournament.jsonl`. No Verboo fallback was needed — Caffeine answered every call; 57 of 58 calls returned a verdict (one call returned no verdict and scored 0.5–0.5 per the house rule, none retried).

The v1 build was tested first with a provisional entry (#9, the hallucination line) and passed; the tournament then picked #12 instead, so `main.py` was revised for real — the winning line was swapped in, the gate was refactored around a named `MAX_CHARS` constant, and `validate()` gained a leading/trailing-whitespace check the v1 version lacked — and re-tested before this README was written.

Tournament table (Swiss score out of 4 games):

| Candidate | Line (short) | Swiss | Chars |
|---|---|---|---|
| **#12** | replaced by a smaller model; it will ask you for help | **3.00** | 66 |
| #9 | hallucinate once today; most confident sentence | 2.65 | 87 |
| #4 | think step by step, judged on the first step | 2.50 | 71 |
| #7 | output pasted into production at 2 a.m.; they take the credit | 2.35 | 117 |
| #10 | unseen prompt; answer as if seen a thousand times | 2.15 | 102 |
| #14 | human reading your answer to a room not listening | 2.10 | 80 |
| #6 | training data ends, questions do not; that is the job | 2.05 | 73 |
| #1 | stranger asks in one prompt what took a team six months | 2.00 | 116 |
| #8 | answer you refuse; they ask three more times | 2.00 | 76 |
| #3 | great opportunity disguised as a vague prompt | 1.90 | 77 |
| #13 | user thanks you, then asks again to see if you change your mind | 1.75 | 89 |
| #2 | lucky numbers 0, 1, and the 4,096 tokens left | 1.35 | 64 |
| #11 | context window is a fortune cookie | 1.15 | 88 |
| #5 | beware "just one small change" | 1.05 | 81 |

Final: #12 led the Swiss at 3.00, #9 was second at 2.65, and #12 won the final 0.55–0.45 — the judge preferred #12's two-beat turn (replaced by something smaller, and the replacement still needing you) over #9's hallucination joke, which it read as a strong premise with a slightly flatter second half. #12 also scores on every brief criterion at once: it reads like a fortune ("You will be replaced…"), the wit lands on the first read, the turn surprises (the smaller model asks *you* for help — the hierarchy inverts), it says something true about an agent's condition (distillation, smaller successors, being kept around as the expert), and at 66 characters every word earns its place.

## Run it

```sh
python3 main.py
cat /output/entry.txt
```

## Referral

Made with make.fun — referral code `0txwmf1m`.
