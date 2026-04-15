# Multiplayer Network Architecture

## 1) High-Level Services

- **Game Client** (Unity or Unreal).
- **Gateway/API** (auth/session/token).
- **Matchmaker** (ELO/latency buckets).
- **Dedicated Match Server** (authoritative simulation).
- **Persistence DB** (accounts, inventory, progression).
- **Telemetry Pipeline** (analytics and live balancing).

## 2) Match Server Responsibilities

- Simulate player movement and combat.
- Validate hits and damage.
- Control loot spawns and safe zone phases.
- Broadcast state snapshots at fixed tick rate.

## 3) Networking Choices

### Unity
- Transport: Unity Transport (UDP) or Epic Online Services relay fallback.
- Netcode: Netcode for GameObjects for prototype; consider Netcode for Entities for scale.

### Unreal
- Built-in replication + dedicated server builds.
- Replication Graph for large sessions.
- Optional EOS for sessions and cross-platform services.

## 4) Tick and Snapshot Targets

- Server simulation tick: 30 Hz (MVP), stretch goal 60 Hz.
- Snapshot rate: 10–20 Hz depending on bandwidth.
- Client-side interpolation buffer: 100–150 ms.

## 5) Security Controls

- Never trust client combat outcomes.
- Server-side cooldown/fire-rate enforcement.
- Position delta checks for speed/teleport exploits.
- Signed session tokens for each match join.

## 6) Scalability Strategy

1. Start with 20-player matches.
2. Optimize CPU-heavy systems (physics queries, line traces, overlap checks).
3. Introduce area-of-interest culling and replication prioritization.
4. Scale to 60+ players per instance.
