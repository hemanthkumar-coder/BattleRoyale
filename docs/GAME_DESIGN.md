# Game Design Document (MVP)

## 1) Match Flow

1. Lobby (players ready up).
2. Matchmaking creates a dedicated match server.
3. Drop phase (aircraft insertion / spawn points).
4. Early loot + rotate to zone.
5. Mid-game engagements.
6. Final circles and showdown.
7. Results screen + rewards + progression updates.

## 2) Core Systems

### Player
- Movement: walk, sprint, crouch, prone, jump, mantle.
- Combat: ADS, hip-fire, recoil, reload, weapon sway.
- Survival: health + armor + healing items.

### Inventory
- Capacity by slot count and weight.
- Attachments: scope, magazine, muzzle, stock.
- Quick slots for healing and throwables.

### Weapons
- Weapon classes: AR, SMG, DMR, SR, Shotgun, Pistol.
- Server authoritative hit validation.
- Ballistics mode toggle:
  - Hitscan (MVP simplicity)
  - Projectile (phase 2 realism)

### Safe Zone
- 6 phase circle collapse.
- Variable damage per phase.
- Broadcast phase timings to all clients.

### Teams and Win Conditions
- Solo and Duo for MVP.
- Team wipe = full elimination.
- Last alive team wins.

## 3) Balancing Defaults

- TTK (close range): 0.7s–1.1s.
- Armor tiers: +0%, +15%, +30% effective HP.
- Zone damage per tick: 1, 2, 4, 8, 12, 18.
- Revive duration: 8 seconds.

## 4) Anti-Cheat Baseline

- Authoritative server movement and combat checks.
- Rate limiting and sanity checks for RPC calls.
- Basic replay/event logs for suspicious sessions.

## 5) Live Operations Readiness

- Rotating store catalog.
- Daily/weekly missions.
- Telemetry events: match start/end, kill, death, damage, loot, zone damage.
