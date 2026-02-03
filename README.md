# Trading 212 API Agent Skills

[![Trading 212](https://img.shields.io/badge/Trading212-API-0066FF)](https://docs.trading212.com/api) [![Claude Code](https://img.shields.io/badge/Claude_Code-Plugin-8B5CF6)](https://claudemarketplaces.com) [![OpenClaw](https://img.shields.io/badge/OpenClaw-Plugin-10B981)](https://www.clawhub.ai) [![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE) [![Maintained](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://github.com/trading212-labs/agent-skills/graphs/commit-activity)

An **AgentSkills** plugin that wraps the [Trading 212 API](https://docs.trading212.com/api) and exposes its capabilities in a **tool-friendly format** for AI assistants (e.g. [OpenClaw](https://openclaw.ai/), [Claude Code](https://claude.com/product/claude-code), and others). The plugin provides skills that teach AI agents how to work with the API: retrieving portfolio and transaction history, placing and managing orders, querying instruments, and related operations—with **consistent, schema-based inputs and outputs**, **authentication and error mapping**, and **rate-limit handling**.

## Features

- **Portfolio Management** - View account summary, cash balance, and investment metrics
- **Order Placement** - Place market, limit, stop, and stop-limit orders
- **Position Monitoring** - Track open positions with P&L calculations
- **Instrument Lookup** - Search and browse tradable instruments
- **Historical Data** - Access order history, dividends, transactions, and export CSV reports
- **Exchange Metadata** - View trading hours and exchange schedules

Supports both **Demo** (paper trading) and **Live** (real money) Trading 212 environments. The Trading 212 API is in **beta** and under active development; endpoints or behaviour may change.

## Supported Account Types

- Invest accounts
- Stocks ISA accounts

## Installation

### Claude Code

```bash
/plugin marketplace add https://github.com/trading212-labs/agent-skills.git
/plugin install trading212-api
```

### OpenClaw / Moltbot / Clawdbot

```bash
clawdbot plugins install github:trading212-labs/agent-skills
```

### Cursor

1. Open Cursor Settings
2. Navigate to `Rules, Skills, Subagents`
3. Click `Add Rule` on Rules section -> Add from Github
4. Submit GitHub url: `https://github.com/trading212-labs/agent-skills.git`

### OpenAI Codex CLI

```bash
$skill-installer https://github.com/trading212-labs/agent-skills/tree/master/plugins/trading212-api/skills/trading212-api
```

## Configuration

Generate API credentials in the Trading 212 app under **Settings > API** (API Key ID and API Secret). See [How to get your Trading 212 API key](https://helpcentre.trading212.com/hc/en-us/articles/14584770928157-Trading-212-API-key) for step-by-step instructions. Store them securely and use only in a trusted, secure environment. See **Credentials and security** below.

**Single account (Invest or Stocks ISA):**

```bash
# Invest or Stocks ISA
export T212_API_KEY="your-api-key"
export T212_API_SECRET="your-api-secret"

#Environment
export T212_ENV="live"   # optional; default is "live"; use "demo" for paper trading
```

**Both accounts (Invest and Stocks ISA):** set a key/secret pair per account.

```bash
# Invest
export T212_API_KEY_INVEST="your-invest-api-key"
export T212_API_SECRET_INVEST="your-invest-api-secret"

# Stocks ISA
export T212_API_KEY_STOCKS_ISA="your-stocks-isa-api-key"
export T212_API_SECRET_STOCKS_ISA="your-stocks-isa-api-secret"

#Environment
export T212_ENV="live"   # optional; default is "live"; use "demo" for paper trading
```

API keys are environment-specific (LIVE vs DEMO). For details, see [Trading 212 API Documentation](https://docs.trading212.com/api).

### Credentials and security

- **Handle with extreme care** — API keys grant access to your Trading 212 account. Set and use them only when you understand the risks. Never paste keys into untrusted chat, shared machines, or public places.
- **Use only in a secure environment** — Use credentials only on a machine and in an environment you control and trust (e.g. your own device, trusted IDE/plugin). Avoid shared or public computers, unverified third-party tools, or environments where others can see your screen or logs.
- **No responsibility** — The maintainers and contributors of this plugin are not responsible for any loss, misuse, or compromise of your API keys or account. You use this plugin and your credentials at your own risk.
- **If your keys are leaked** — If you suspect your API key or secret has been exposed (e.g. committed to a repo, shared by mistake, or seen by someone else), **revoke it immediately** in the Trading 212 app: **Settings > API**, then delete/revoke the affected key and generate a new one. Do not continue using a compromised key.

## Disclaimer

This plugin is an experimental technical integration tool only. AI tools can misinterpret instructions and execute unintended actions, including placing incorrect orders. Never share your API key with tools or services you don't trust. You are solely responsible for any actions carried out using your API key. This plugin does not provide financial advice. You are required to comply with our API Terms at all times. As required by MiFID II, you are prohibited from using this tool for algorithmic trading.

## License

[MIT License](LICENSE)
