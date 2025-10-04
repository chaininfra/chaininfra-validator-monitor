---

````markdown
# ChainInfra Validator Monitor

A lightweight Telegram alerting system for Metal Blockchain validator nodes.  
Built by [ChainInfra](https://chaininfra.net) for operators who want instant alerts when their node goes offline or recovers.

---

## 🚀 Features

- ✅ Monitors one or multiple Metal validator nodes via the public Explorer API  
- 🚨 Sends alerts only when status changes (no noise)  
- 🔒 Keeps local state between runs  
- 🕐 Configurable check interval (default 5 min)  
- 📄 Simple text-based configuration (`config.env`, `nodes.txt`)  
- 💬 Telegram integration (Bot Token + Group Chat ID)  
- 👥 Multi-node ready — perfect for community validators and home-lab setups  

---

## 🧰 Requirements

- Ubuntu 20.04 or newer (tested on 22.04 LTS)  
- `curl`, `jq`, `bc`, and `cron`  
- A Telegram **Bot Token** and **Group Chat ID**

---

## ⚙️ Installation

Clone the repo and run the setup wizard:

```bash
git clone https://github.com/chaininfra/validator-monitor.git
cd validator-monitor
chmod +x setup_chaininfra_monitor.sh
sudo ./setup_chaininfra_monitor.sh
````

During setup you’ll be prompted for:

* **Bot Token** (from @BotFather)
* **Chat ID** (your group or channel)
* **Check interval** (e.g. 5 minutes)

---

## 🧩 Configuration Files

| File                                  | Purpose                        |
| ------------------------------------- | ------------------------------ |
| `/opt/chaininfra-monitor/config.env`  | Bot token, chat ID, thresholds |
| `/opt/chaininfra-monitor/nodes.txt`   | One NodeID per line            |
| `/opt/chaininfra-monitor/status.json` | Internal state (auto-managed)  |
| `/usr/local/bin/chaininfra`           | Helper CLI command             |

---

## 🧠 Commands

```bash
chaininfra status              # show current status (no alerts)
sudo chaininfra run            # run monitor manually
sudo chaininfra add <NodeID>   # add a validator
sudo chaininfra test           # send test alert
chaininfra logs                # view recent logs
```

---

## 🔔 Alert Logic

| Transition    | Telegram Alert       |
| ------------- | -------------------- |
| **up → down** | 🚨 Validator Down    |
| **down → up** | ✅ Validator Restored |
| anything else | (no message)         |

Alerts fire only on **state change** — no hourly spam.

---

## 🧱 Example Telegram Output

```
🔥 ChainInfra Validator Alerts

🚨 Validator Down: ChainInfra
Uptime: 0%

✅ Validator Restored: ChainInfra
Uptime: 99.56%
```

---

## 🧑‍💻 Contributing

If you’re running a Metal node or building a home-lab setup, DM **@Leenoh** to get your NodeID added to the ChainInfra Ops chat.

---

© 2025 ChainInfra | Made for the Metal Blockchain community

```

```
