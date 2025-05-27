# GDevelop Chicken + Egg Spawn System (No JavaScript)

---

## Objects Needed
- **Chicken** (enemy sprite)
- **Egg** (bomb-like sprite)
- **Desappearing** (effect sprite)

---

## Object Variables

- **Egg**
  - `HatchTimer` (Number) — tracks time until hatch
- **Chicken**
  - `DeadClone` (Number) — tracks if respawn happened (0 or 1)

---

## Event Logic

### 1. Egg Hatch Timer
- Always add `TimeDelta()` to `Egg.HatchTimer`
- If `Egg.HatchTimer >= 5` seconds:
  - Create a `Chicken` at Egg’s position
  - Delete the `Egg`

### 2. Destroy Egg Early (Example: on key press)
- If key `D` pressed:
  - Create `Desappearing` at Egg’s position
  - Delete the `Egg`

*(Replace key press with collision or damage event as needed)*

### 3. Chicken Death & Respawn
- When `Chicken` dies (e.g., health ≤ 0) and `DeadClone = 0`:
  - Create new `Chicken` at dead Chicken’s position
  - Set `DeadClone = 1` to avoid multiple spawns
  - Delete the original `Chicken`

### 4. (Optional) Chicken Laying Eggs
- If timer `EggSpawn` ≥ 4 seconds:
  - Create `Egg` at Chicken’s position
  - Reset `EggSpawn` timer
  - Set new Egg’s `HatchTimer` to 0

---

## Summary Table

| Object  | Variable    | Purpose                     |
|---------|-------------|-----------------------------|
| Egg     | HatchTimer  | Time counter to hatch Chicken |
| Chicken | DeadClone   | Prevent duplicate respawns   |

---

*Use this system to have eggs hatch into chickens, eggs destroyed early with effects, and chickens respawn when killed.*
