# 🌐 DomainRouter 
![java](https://raw.githubusercontent.com/intergrav/devins-badges/refs/heads/v3/assets/cozy/built-with/java21_vector.svg) ![veloc](https://raw.githubusercontent.com/intergrav/devins-badges/refs/heads/v3/assets/cozy/supported/velocity_vector.svg) ![modrinth](https://raw.githubusercontent.com/intergrav/devins-badges/refs/heads/v3/assets/cozy/available/modrinth_vector.svg)

A modern proxy/router plugin for Minecraft servers. This plugin allows you to automatically route players to different backend servers based on the domain or IP address they use. Perfect for server networks, lobby systems, or multi-brand Minecraft setups.

---

# ✨ Features

* **Domain-based server routing** – Route players instantly based on how they connected.
* **Multi-server support** – Easily link as many subdomains and backend servers as you need.
* **Custom kick messages** – Full support for Minecraft color codes (`&`) and newlines (`\n`) directly in the main configuration! *(New in v1.2)*
* **Lightweight & Fast** – Optimized code that won't lag your proxy network.
* **Clean config system** – Simple, clean, and extremely easy to set up.

---

# 📦 Example routing

* `survival.yourserver.com` ➔ Survival server
* `bedwars.yourserver.com` ➔ BedWars server
* `event.yourserver.com` ➔ Event server

---

<details>
<summary>⚙️ Click to view example config.yml</summary>

```yaml
lang: en # Language for messages and interface (e.g., en, cz)

minigames.example.com: minigames
pvp.example.com: pvp
mc.example.com: main

default: main

# Comma-separated servers where players will be KICKED directly from the proxy (no fallback)
kick-servers: pvp, minigames

# Custom kick message (supports & color codes and \n for a new line)
kick-message: "&8[&aDomainRouter&8] &7Server &d%server% &7has been shut down.\\n&cYou have been disconnected from the proxy!"

debug: true # Default is true for logging to console.

#Plugin Version: 1.2
#Config Version: 5
#Config can be fully changed, only the structure, debug: and default: must be maintained.
