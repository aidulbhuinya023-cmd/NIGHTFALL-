Monorepo (pnpm workspaces):

apps/client      # Three.js + Vite frontend (not yet implemented)

apps/server      # Node.js + Express + Socket.IO authoritative server (not yet implemented)

packages/config  # Authoritative game balance JSON (classes, weapons, movement, match, combat, xp)

packages/protocol# Zod schemas for every config file + inferred TS types (z.infer only)

packages/shared  # Movement & damage math shared by client prediction and server simulation

docs/            # Full locked specification


Setup

pnpm install

pnpm typecheck # strict TS across all packages

pnpm test  # Vitest unit + integration tests


Status
 Monorepo scaffold (pnpm, strict TS, Vitest)
 packages/config — all balance data, Zod-validated at load (fail loudly)
 packages/protocol — Zod schemas for classes, weapons, movement, match, combat, xp
 packages/shared — computeFinalSpeed (multiplicative formula), jump physics, damage calc with config-driven falloff + headshot multiplier
 
 Movement physics engine — fixed-timestep kinematic step (WASD, sprint/crouch/ADS, jump w/ no air control, gravity, terminal velocity), AABB world collision (walls, crates, ceiling, bounds), server-side input validation + displacement cap
 Networking message protocol — Zod schemas for all 4 message families (input, state snapshot, events, lobby) + single typed dispatch with safeParse
 Combat resolution (hitscan / projectile / melee, server-authoritative)
 Server game core (20Hz MatchRoom, FFA mode)
 Client (Three.js rendering, HUD)
Full spec: docs/00-index.md and NIGHTFALL_Complete_Project_Plan.md.
