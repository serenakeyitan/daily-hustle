---
name: hustle-daily
description: 每日搞钱日报 — 5 个低门槛赚钱点子，来自 Reddit 和 Twitter
metadata: {"clawdbot":{"emoji":"💰","requires":{"bins":["python3"]}}}
---

# 搞钱日报 (Money Hustle Daily)

Curated daily newsletter of 5 low-barrier money-making ideas sourced from Reddit and Twitter/X, translated and condensed into Chinese.

## Flow

### Step 1: Fetch raw candidates

```bash
python3 /root/.openclaw/skills/hustle-daily/scripts/run.py
```

This outputs up to 30 JSON candidates sorted by score. Each item has:
```json
{"source": "reddit|twitter", "title": "...", "url": "...", "score": 123, "details": "...", "created": "2026-03-08T..."}
```

### Step 2: Curate top 5

From the candidates, pick the **top 5 genuine money-making opportunities**.

**REJECT:**
- Ads or sponsored content
- MLM / pyramid schemes
- Crypto / NFT scams
- Anything requiring significant upfront investment (>$500)
- Vague motivational posts with no actionable info

**PREFER:**
- Genuine niche opportunities (e.g., "sell printables on Etsy")
- Arbitrage plays (retail, digital, services)
- Digital services and freelancing with low barrier to entry
- Passive income methods with clear steps
- Unusual or creative side hustles

**Quality test:** Each idea must pass the "can I explain this in one sentence?" test. If you can't summarize the opportunity in one clear sentence, skip it.

Evaluate content quality regardless of source (Reddit vs Twitter). Pick the best 5 overall.

### Step 3: Format newsletter

Translate/localize each idea into Chinese. Use this exact format:

```
搞钱日报 | YYYY-MM-DD

1. [一句话描述这个赚钱方法]
   • 关键点1
   • 关键点2
   • 启动成本/难度
   → 来源链接

2. ...
(5 items total)

---
数据来源：Reddit, Twitter/X
```

### Step 4: Mark seen items and cleanup

After finalizing the 5 picks, mark them as seen so they won't appear again:

```bash
echo '<JSON array of the 5 picked items>' | python3 /root/.openclaw/skills/hustle-daily/scripts/dedup.py mark
```

Then prune old entries:

```bash
python3 /root/.openclaw/skills/hustle-daily/scripts/dedup.py cleanup
```

### Step 5: Output the newsletter

Output the formatted newsletter text. The caller decides where to send it (Discord, Feishu, etc.).

## Data Files

| File | Location | Purpose |
|------|----------|---------|
| Seen items | `workspace/memory/hustle-daily-seen.json` | 30-day dedup state |

## Scripts

| Script | Purpose |
|--------|---------|
| `scripts/fetch_reddit.py` | Fetch top posts from side-hustle subreddits |
| `scripts/fetch_twitter.py` | Search Twitter via twitter_client.py |
| `scripts/dedup.py` | 30-day rolling dedup manager |
| `scripts/run.py` | Orchestrator: fetch + dedup + output candidates |
