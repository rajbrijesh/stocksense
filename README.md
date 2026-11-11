# StockSense

A Claude skill for fundamentals-only analysis of Indian (NSE/BSE) listed stocks, for long-term investors.

It uses live data from Screener.in, Tickertape and Moneycontrol, shows the source for every key figure, and never gives a buy/sell/hold call or target price. This is not investment advice.

## Modes

Quick Take, Deep Dive (interactive report), Compare, Pros & Cons, Portfolio Fit, Bull vs Bear debate, and Thesis Check after new results.

## Files

```
skills/stocksense/
├── SKILL.md
├── references/     # data-sources, research-desks, bull-bear-debate, thesis-check
└── assets/
    └── deep-dive-template.html
```

## Install

**Claude Code — plugin marketplace**

```
/plugin marketplace add rajbrijesh/stocksense
/plugin install stocksense@rajbrijesh-stocksense
```

**Claude Code — copy**

Copy `skills/stocksense` into `~/.claude/skills/` (all projects) or `.claude/skills/` (one project).

**Claude.ai / Cowork**

Zip the `stocksense` folder and upload it as a custom skill in Claude settings.

## License

[MIT](LICENSE)
