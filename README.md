# battery-mcp-server

> Let AI agents run battery testing experiments through the Model Context Protocol.

🚧 **Status: In Development** — First public release coming soon.

---

## 🎯 Why This Exists

Most MCP demos show "AI reads from a file." This project shows how to build a
**production-grade MCP server** for industrial hardware, with the engineering
discipline that turns "AI demo" into "AI production system."

---

## ✨ Planned Features

- ⚡ **Real-time data streaming** from simulated battery testing hardware
- 🛡️ **Safety guardrails** — AI can't execute unsafe operations
- 📊 **Zero-loss data persistence** (SQLite time-series storage)
- 🔒 **Fault-tolerant error recovery** — built for 24/7 unattended operation
- 📈 **Anomaly detection** during tests
- 🤖 **Works with Claude Desktop, LangChain, and custom agents**

---

## 🎬 Demo Scenarios (Planned)

```
User: "Start a charge-discharge cycle on channel 1 with standard parameters"
AI:   [calls start_test tool] → "Test #42 started. Monitoring voltage & temp..."

User: "Did anything unusual happen in yesterday's tests?"
AI:   [calls analyze_data tool] → "Channel 3 showed temperature spike at cycle 47.
      Capacity degradation 2.3x faster than baseline. Recommend inspection."

User: "Set charge current to 100A on the small cell"
AI:   [checks safety layer] → "Cannot execute: requested current exceeds cell's
      rated maximum (5A). This operation could cause thermal runaway."
```

---

## 🏗️ Architecture (Planned)

```
┌─────────────────────────────────────────────┐
│         MCP Server (this project)            │
│  ┌────────────────────────────────────────┐ │
│  │   Tools Layer                          │ │
│  │   start_test · get_status · get_data   │ │
│  │   stop_test · analyze_data · report    │ │
│  └────────────────────────────────────────┘ │
│  ┌────────────────────────────────────────┐ │
│  │   Safety / Guardrails Layer            │ │
│  └────────────────────────────────────────┘ │
│  ┌────────────────────────────────────────┐ │
│  │   Battery Hardware Simulator           │ │
│  │   (voltage · current · temp · SOC)     │ │
│  └────────────────────────────────────────┘ │
│  ┌────────────────────────────────────────┐ │
│  │   Data Layer (SQLite time-series)      │ │
│  └────────────────────────────────────────┘ │
└─────────────────────────────────────────────┘
                  ↑ MCP Protocol
            ┌─────────────┐
            │  AI Agent   │  Claude / LangChain / custom
            └─────────────┘
```

---

## 🛠️ Tech Stack

- **Python 3.11+** · asyncio
- **MCP Protocol** (Model Context Protocol by Anthropic)
- **SQLite** (time-series storage)
- **pytest** (test coverage target: 90%+)

---

## 📅 Roadmap

- [ ] Week 1: Core MCP server skeleton + battery simulator
- [ ] Week 2: Safety guardrails + data persistence
- [ ] Week 3: LangChain + Claude Desktop integration
- [ ] Week 4: Demo video + blog post + v1.0 release

---

## 📜 License

MIT — will be added at first release.

---

## 👤 Author

**Howie** — Director of Software R&D @ CYGIA (Changyuan Group)
- 🏭 10+ years building industrial-grade automation & testing systems
- 🤖 Now bringing that discipline to AI agent systems
- 📧 [GitHub](https://github.com/hongweiduan) · [Profile](https://github.com/hongweiduan)

---

<sub><i>"From industrial-grade reliability to AI agent systems."</i></sub>
