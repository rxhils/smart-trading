<p align="center">
  <h1 align="center">SmartMoney India</h1>
  <h4 align="center">A premium Indian-market investing copilot — chat, AI portfolios, and read-only broker data in one calm app</h4>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-iOS%20%2F%20Android-black?style=flat-square&logo=apple" />
  <img src="https://img.shields.io/badge/Built%20with-Expo%20%2F%20React%20Native-0A0A0A?style=flat-square&logo=expo" />
  <img src="https://img.shields.io/badge/Market-NSE%20%2F%20BSE-blue?style=flat-square" />
  <img src="https://img.shields.io/badge/Research-bharat--research--brain-orange?style=flat-square" />
  <img src="https://img.shields.io/badge/Trades-0%20(read--only)-brightgreen?style=flat-square" />
</p>

---

## The idea in one sentence

> Most market apps overwhelm you with alerts, charts, and noise. This one does the opposite — it answers your question, shows you how AI portfolios are performing, and lets you see your own holdings. That's it.

---

## Three screens. Nothing more.

SmartMoney India is deliberately minimal. Three screens, each with a clear job.

```
┌──────────────────────────────────────────────────────────────┐
│  Screen 1 — Chat                                             │
│                                                              │
│  Two modes, one interface — switches automatically based on  │
│  whether a broker is connected.                              │
│                                                              │
│  WITHOUT broker connected — market mode:                     │
│  "Why did HDFC Bank drop today?"                             │
│  "Is the IT sector in a rotation out phase?"                 │
│  "What's Reliance's RSI and trend right now?"                │
│                                                              │
│  WITH broker connected — portfolio mode:                     │
│  "How is my portfolio doing today?"                          │
│  "Which of my holdings are in a downtrend?"                  │
│  "Why is Infosys down — should I be worried given my         │
│   position size?"                                            │
│  "Am I overexposed to IT right now?"                         │
│                                                              │
│  In both modes, answers are grounded in real market data     │
│  and explain the "why" — not generic hedged responses.       │
└──────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────┐
│  Screen 2 — AI Portfolios                                    │
│                                                              │
│  Different AI strategies compete in the Indian market.       │
│  Each portfolio has a style (Stable / Balanced / Bold) and   │
│  a live performance score. No human discretion. No bias.     │
│                                                              │
│  See: returns over time, rankings, strategy style.           │
└──────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────┐
│  Screen 3 — Broker Settings                                  │
│                                                              │
│  Connect your broker in read-only mode.                      │
│  The app never places a trade.                               │
│                                                              │
│  Once connected, the chat assistant becomes personal —       │
│  it knows your actual holdings, position sizes, and P&L,     │
│  and uses that context to give answers specific to you,      │
│  not the general market.                                     │
└──────────────────────────────────────────────────────────────┘
```

---

## How the app works end-to-end

```
                    ┌─────────────────────────┐
                    │   SmartMoney India App   │
                    │   (Expo / React Native)  │
                    └────────────┬────────────┘
                                 │
             ┌───────────────────┼───────────────────┐
             │                   │                   │
             ▼                   ▼                   ▼
    ┌──────────────┐   ┌──────────────────┐   ┌────────────────┐
    │  Chat Screen │   │  AI Portfolios   │   │ Broker Screen  │
    │              │   │  Leaderboard     │   │ (read-only)    │
    └──────┬───────┘   └────────┬─────────┘   └───────┬────────┘
           │                    │                      │
           ▼                    ▼                      │
  ┌─────────────────────────────────────┐              │
  │       FinRobot-style Reasoning      │              │
  │                                     │              │
  │  Agent 1: Data fetcher              │              │
  │  Agent 2: Reasoning / analysis      │              │
  │  Agent 3: Answer writer             │              │
  └─────────────┬───────────────────────┘              │
                │                                      │
                ▼                                      │
  ┌──────────────────────────────────────────────────┐ │
  │         bharat-research-brain                    │ │
  │                                                  │ │
  │  India-specific research and retrieval layer.    │ │
  │  507 NSE/BSE stocks · 27 agents · Ranked daily  │ │
  │  Grounded market data, company context, signals  │ │
  │                                                  │ │
  │  → github.com/rxhils/bharat-research-brain       │ │
  └──────────────────────────────────────────────────┘ │
                                                        │
                ┌───────────────────────────────────────┘
                ▼
  ┌──────────────────────────────────────────────────┐
  │  Broker API (read-only)                          │
  │  Zerodha Kite / Upstox / others                  │
  │                                                  │
  │  Holdings · Position sizes · Entry prices        │
  │  Current P&L · Sector exposure · Cash            │
  │                                                  │
  │  Feeds into reasoning alongside market signals   │
  │  so chat answers are personal, not just general  │
  │  Never order placement                           │
  └──────────────────────────────────────────────────┘
```

---

## The research layer — bharat-research-brain

The assistant and the AI portfolios are only as good as the data behind them.

SmartMoney India uses **[bharat-research-brain](https://github.com/rxhils/bharat-research-brain)** as its India-specific research and retrieval layer. It is a fully autonomous equity research engine built for NSE/BSE — running 27 agents nightly to rank 507 stocks and produce a grounded, cited daily report.

**What bharat-research-brain provides to this app:**

| Data | How the app uses it |
|------|---------------------|
| Daily 0–100 stock scores (507 stocks) | Powers the AI portfolio rankings |
| Technical signals (RSI, MACD, EMA, VCP) | Backs up chat assistant answers |
| Macro regime (Risk-On / Cautious / Risk-Off) | Context for portfolio style performance |
| FinBERT-classified news (per stock) | "Why did this stock move?" answers |
| Sector rotation signals | Chat and portfolio filtering |
| Fundamentals (PE, ROE, FCF, D/E) | Fundamentals-based chat questions |
| FII/DII institutional flows | Market context in answers |

> **bharat-research-brain is the engine. SmartMoney India is the interface.**  
> The engine runs locally overnight. The app reads its output.  
> → [See the full engine documentation](https://github.com/rxhils/bharat-research-brain)

---

## The reasoning layer — FinRobot-style multi-agent flow

When the user asks a question, the app does not simply forward it to an LLM and return whatever it says. It follows a structured multi-agent flow that merges market data with the user's personal portfolio context when a broker is connected:

```
User question
      │
      ▼
Agent 1 — Context builder
  Determines what the question is about:
  a market question, a stock question, or a portfolio question?

  Market signals pulled from bharat-research-brain:
    stock scores, RSI, MACD, EMA, news, macro regime,
    sector rotation, FII/DII flows, FinBERT sentiment

  Portfolio context pulled from broker (if connected):
    holdings, position sizes, current P&L, entry prices,
    sector exposure, cash allocation

      │
      ▼
Agent 2 — Reasoning
  Combines market signals with portfolio context.

  For market questions:
    What is driving this stock or sector? Is the signal
    reliable in the current macro regime?

  For portfolio questions:
    How does the market signal interact with the user's
    specific position? Is their exposure a concern given
    what is happening in the sector today?

      │
      ▼
Agent 3 — Answer writer
  Writes a short, grounded, plain-English explanation.
  Personalised when portfolio context is available.
  Cites the data it used. Avoids advisory language.
  Returns the answer to the chat screen.
```

**The key difference from a generic chatbot:**
A question like "why is Infosys down?" returns a market explanation to any user. But with a broker connected, the same question also considers your position size, your sector exposure, and your entry price — and the answer reflects that context. The data is still objective; the framing is personal.

---

## AI portfolio styles

The portfolio screen shows different AI strategies competing in real time:

| Style | What it means |
|-------|--------------|
| **Stable** | Conservative stocks, lower volatility, consistent compounders |
| **Balanced** | Mix of growth and stability, sector-diversified |
| **Bold** | Higher-conviction, higher-risk setups — momentum and growth |

Each style is backed by a distinct scoring profile from bharat-research-brain. The leaderboard shows:
- Cumulative return over time
- Current ranking vs other styles
- Underlying stock selections

No human picks stocks. The engine scores them. The portfolio style is just a filter on those scores.

---

## What the app does not do

This is as important as what it does.

- **No trading.** The app cannot place, modify, or cancel orders. Ever.
- **No watchlists.** No cluttered lists to manage.
- **No price alerts.** No notification spam.
- **No charts.** The assistant explains the "why" in words.
- **No tips or recommendations.** Answers are grounded in data, not advice.

The goal is a calm, focused tool — not another noisy trading terminal.

---

## Tech stack

| Layer | Technology |
|-------|-----------|
| App framework | Expo (React Native) |
| Language | TypeScript |
| Navigation | Expo Router |
| Lists | FlashList |
| Animations | Reanimated 3 |
| State | Zustand |
| Data fetching | TanStack Query |
| Research layer | [bharat-research-brain](https://github.com/rxhils/bharat-research-brain) (FastAPI, PostgreSQL, 27 agents) |
| Broker integration | Zerodha Kite API (read-only) / Upstox API |
| Reasoning | FinRobot-style multi-agent (Claude / local LLM) |

---

## Build phases

| Phase | Status | What it delivers |
|-------|--------|-----------------|
| 1 — Chat foundation | 🔄 In progress | Chat screen, basic question answering, market context |
| 2 — Research wiring | ⏳ Planned | Connect to bharat-research-brain API, grounded answers |
| 3 — AI portfolios | ⏳ Planned | Portfolio leaderboard, style grouping, performance over time |
| 4 — Broker settings | ⏳ Planned | Read-only broker connection, holdings context in chat |
| 5 — Reasoning layer | ⏳ Planned | Full FinRobot-style multi-agent answer pipeline |
| 6 — Polish | ⏳ Planned | Animations, accessibility, reduced-motion gating |

---

## Project structure

```
smart-trading/
├── app/                    # Expo Router screens
│   ├── (tabs)/
│   │   ├── index.tsx       # Screen 1 — Chat
│   │   ├── portfolios.tsx  # Screen 2 — AI Portfolios
│   │   └── settings.tsx    # Screen 3 — Broker Settings
│   └── _layout.tsx
├── components/
│   ├── chat/               # Message bubbles, input bar, loading states
│   ├── portfolio/          # Portfolio cards, leaderboard rows, style chips
│   └── shared/             # Buttons, badges, section headers
├── services/
│   ├── research.ts         # bharat-research-brain API client
│   ├── broker.ts           # Read-only broker API integration
│   └── reasoning.ts        # Multi-agent answer pipeline
├── store/                  # Zustand state slices
└── constants/              # Design tokens, theme
```

---

## Research infrastructure

This app is the consumer layer. The research infrastructure that powers it lives here:

**[→ bharat-research-brain](https://github.com/rxhils/bharat-research-brain)**

> 507 NSE/BSE stocks · 27 agents · Daily rankings · Self-learning · Fully local · ₹0/month

If you want to understand the signals behind the chat answers and portfolio rankings, that is the right place to start.

---

## Compliance

- This app is for **personal research only**
- No order placement code exists anywhere in this repository
- Broker integration is strictly read-only
- Not registered with SEBI as an investment adviser
- Output is never used for advisory services

---

## Related

| Repo | What it is |
|------|-----------|
| [bharat-research-brain](https://github.com/rxhils/bharat-research-brain) | The research engine — 507 stocks, 27 agents, daily rankings |
