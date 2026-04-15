# Unreal Engine Implementation Track

## Recommended Stack

- Unreal Engine 5.4+.
- C++ gameplay core, Blueprint for UI/content iteration.
- Built-in CharacterMovement + replication.
- Replication Graph for network scaling.
- EOS for session/auth if needed.

## Module Breakdown

- `BRCore` (match state, game mode, game state).
- `BRCombat` (weapons, damage, recoil, projectiles/hitscan).
- `BRInventory` (items, pickups, attachments).
- `BRZone` (safe zone phase logic).
- `BRUI` (HUD, inventory, minimap, kill feed).

## Key Classes

- `ABRGameMode` (server-only match authority).
- `ABRGameState` (replicated match data).
- `ABRPlayerState` (kills, assists, team, progression).
- `ABRCharacter` (movement/combat actions).
- `ABRWeapon` base class.

## Implementation Steps

1. Build traversal + combat sandbox map.
2. Implement authoritative fire and damage on server.
3. Add replicated inventory and loot pickups.
4. Add circle phases and zone damage.
5. Build dedicated server package and deploy test environment.
6. Integrate matchmaking and progression persistence.

## Unreal-Specific Performance Tips

- Configure NetUpdateFrequency by actor class.
- Use relevance and dormancy for distant/non-critical actors.
- Profile server threads with Unreal Insights.
- Keep Blueprint Tick usage minimal for replicated actors.
