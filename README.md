# 🌐 DomainRouter

![java](https://raw.githubusercontent.com/intergrav/devins-badges/refs/heads/v3/assets/cozy/built-with/java21_vector.svg) ![veloc](https://raw.githubusercontent.com/intergrav/devins-badges/refs/heads/v3/assets/cozy/supported/velocity_vector.svg) ![modrinth](https://raw.githubusercontent.com/intergrav/devins-badges/refs/heads/v3/assets/cozy/available/modrinth_vector.svg)

A modern, high-performance proxy routing and network management plugin for Velocity. DomainRouter allows you to seamlessly route incoming players to different backend servers based on the specific domain or IP address they use to connect, while giving you complete control over your network's first impression. Perfect for server networks, lobby systems, or multi-brand Minecraft setups.

---

## ✨ Features (Major Update v1.3)

* **Domain-Based Routing** – Direct players instantly to specific backend servers (e.g., Survival, Lobby, PvP) depending on their connection address.
* **Advanced Maintenance Mode** – Shut down public access to your network with a single switch. Features a customizable protocol text, custom multi-line kick messages, and a player whitelist/bypass system via nicknames or UUIDs.
* **Smart Fallback & Multi-Server Redirects** – Prevent players from being disconnected from the entire proxy! If a sub-server crashes or shuts down, DomainRouter automatically routes them to a designated backup server.
* **Per-Domain Dynamic MOTD & Icons** – Deliver distinct server list descriptions and custom `.png` icons/favicons based on the domain used.
* **MiniMessage & Legacy Support** – Express your brand beautifully. Full support for modern RGB gradients, HEX color codes, and legacy formatting (`&`) across MOTDs and kick screens.
* **Isolated Player Counters** – Configure specific domains to count and display players only from selected backend instances rather than displaying the total proxy count.
* **Automated Localization System** – The plugin now automatically generates complete local language template files (`en.yml` and `cz.yml`) on its very first launch.

---

## 📦 Example Routing

* `survival.yourserver.com` ➔ Survival server
* `bedwars.yourserver.com` ➔ BedWars server
* `event.yourserver.com` ➔ Event server

---

## ⚙️ Configuration

<details>
<summary>Click to view automatically generated config.yml (v7)</summary>

```yaml
# ================================================================= #
#                     DOMAINROUTER CONFIGURATION                     #
# ================================================================= #

lang: "en"
debug: true

# Default server where the proxy sends players if the domain has no specific route
default-fallback-server: "lobby"

# --- ROUTES ---
# Mapping of domains used by players to specific starting servers
routes:
  mc.example.com: "lobby"
  survival.example.com: "survival"
  pvp.example.com: "pvp"

# --- MAINTENANCE MODE ---
maintenance:
  enabled: false             # true = enables global proxy maintenance / false = disabled
  protocol-text: "§cMaintenance"
  
  # Custom kick message for players trying to join during maintenance
  kick-message: "&8[&4Maintenance&8]\n\n&cThe entire network is currently undergoing scheduled maintenance!\n&7Check our Discord for more info.\n\n&6Updating network to version 1.3..."
  
  # Players with a bypass to join during active maintenance (Nick or UUID)
  allowed-players:
    - "KuklincYT"

  # MOTD shown in the server list when maintenance is active
  motd:
    - "<gradient:#8a2be2:#da70d6><bold>EXAMPLE NETWORK</bold></gradient> <gray>•</gray> &cMAINTENANCE\n&7We are currently performing a massive proxy update!"

# --- DYNAMIC MOTD PER DOMAIN ---
domains:
  mc.example.com:
    icon: "server-icon.png"
    max-players: 1000
    # Sums online players only from defined servers (if missing, sums the whole proxy)
    player-counting-servers:
      - "lobby"
      - "survival"
    # List of MOTDs for this domain (plugin picks randomly if multiple exist)
    motds:
      - "<gradient:#8a2be2:#da70d6><bold>Example Network</bold></gradient> <gray>•</gray> <white>1.19 - 1.21</white>\n&aThe new Survival season has started!"
      - "<gradient:#8a2be2:#da70d6><bold>Example Network</bold></gradient> <gray>•</gray> <white>News</white>\n&eJoin and claim your rewards in the lobby!"

  pvp.example.com:
    icon: "pvp-icon.png"
    max-players: 150
    player-counting-servers:
      - "pvp"
    motds:
      - "&c&lPVP ARENA\n&7Come test your combat skills!"

  # Default MOTD if someone connects via an unconfigured subdomain
  default:
    icon: "default.png"
    max-players: 500
    motds:
      - "&8[&dExample Network&8]\n&fYou have connected via a backup domain."

# --- FALLBACKS AND KICKS ---
# When a server on the left goes offline, players are sent to the right (instead of being kicked from proxy)
server-fallbacks:
  survival: "lobby"
  skyblock: "lobby"

# List of servers from which players are completely kicked off the proxy when they shut down
kick-servers:
  - "pvp"
  - "minigames"

# Custom message for kick / disconnect from a server on the fly
kick-message: "&8[&dExample Network&8]\n\n&aServer &d%server% &ais currently offline.\n&8>> &aMoving you to the main lobby... &8<<"

# --- CONFIG METADATA ---
config-version: 7
plugin-version: "1.3"
```

</details>

---



## 🌍 Extra Translations & Custom Languages



To ensure 100% completeness and professional quality, you can find and download additional language files directly from our repository workspace:



➔ **[Download Official Extra Translations](https://github.com/kuklinc-youtuber/domain-router/tree/main/lang)**



### How to use them:

1. **Download** the language file you need (e.g., `de.yml`, `es.yml`) from the link above.

2. **Upload** the file into your proxy folder at: `plugins/DomainRouter/languages/`

3. **Update** the `lang` option in your main `config.yml` to match the file name (e.g., `lang: de`).

4. **Run** `/domainrouter reload` to apply the changes.



> **💡 NOTE:** You can fully modify and tweak any downloaded language file to better suit your network's style!



---



⚡ **Perfect for Minecraft networks that want professional server routing without complicated setup.**



🛠️ The plugin is actively being developed and will receive new features and improvements over time.



![bstat](https://bstats.org/signatures/velocity/DomainRouter.svg)
