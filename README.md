# hustle-daily — 搞钱日报

Daily newsletter skill that curates 5 low-barrier money-making ideas from Reddit and Twitter/X.

## What it does

When triggered, the skill:
1. Fetches top posts from side-hustle subreddits (r/sidehustle, r/beermoney, r/passive_income, r/Entrepreneur, r/sweatystartup)
2. Searches Twitter/X for side hustle content
3. Deduplicates against a 30-day rolling history
4. Agent curates the best 5 ideas — rejects ads/MLM/scams, prefers genuine low-barrier opportunities
5. Outputs a Chinese mini-newsletter with one-sentence summaries + bullet points + source links

## Output format

```
搞钱日报 | 2026-03-08

1. 用AI批量生成婚礼请柬模板，Etsy上月入$2K
   • 工具：Canva + ChatGPT，零设计基础
   • 启动成本 < $50
   → https://reddit.com/r/sidehustle/...

2. ...
(5 items total)
```

## Setup

1. Place in your `skills/` directory (or unzip the release)
2. Ensure `python3` and `requests` are available
3. (Optional) Configure [twitter-scraper](https://github.com/serenakeyitan/openclaw-pi) cookies for dual-source coverage

## Requirements

- Python 3.10+
- `requests` library
- (Optional) twikit-based twitter-scraper skill for Twitter/X data

## Compatible with

- Claude Code skills
- Kael.im skills
- Any agent that reads SKILL.md format

## License

MIT
