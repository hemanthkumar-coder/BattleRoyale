# Unity Implementation Track

## Recommended Stack

- Unity 6 LTS.
- URP for broad platform support.
- Input System package.
- Netcode for GameObjects (MVP) + Unity Transport.
- Addressables for live content delivery.

## Scene Layout

- `Bootstrap` scene (services, auth, config).
- `MainMenu` scene.
- `Lobby` scene.
- `Match` scene.

## Core Prefabs

- `PlayerController` (movement + camera + animation state).
- `WeaponController` (fire/reload/attachments).
- `InventoryComponent`.
- `ZoneController`.
- `LootSpawner`.

## Implementation Steps

1. Build local offline shooter loop first.
2. Convert player and weapon logic to server-authoritative netcode.
3. Add match state machine (waiting, dropping, active, ended).
4. Implement replication for:
   - transform and stance
   - health/armor
   - weapon state and ammo
   - zone phase
5. Add dedicated server headless build profile.
6. Integrate matchmaking and account backend.

## Unity-Specific Performance Tips

- Use non-allocating physics APIs where possible.
- Pool loot pickups, shell VFX, and impact effects.
- Keep Animator layers minimal for many remote players.
- Use LOD groups and occlusion culling aggressively.
