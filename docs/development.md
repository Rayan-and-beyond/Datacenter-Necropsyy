# Developer notes

Datacenter Autopsy is a browser-only React and Three.js application. The source layout keeps hardware-specific models separate from the rendering engine and shared UI.

| Path | Purpose |
| --- | --- |
| `src/App.tsx`, `src/index.css` | Interface and styling |
| `src/server/` | Machine data, geometry, and interactive viewer |
| `src/engine/`, `src/lib/` | Shared rendering and geometry utilities |
| `tests/tests.json` | Manual browser test scenarios |
| `docs/` | Reference material and documentation assets |

## Architecture

- src/server/catalog.ts: platform-specific inventory, dimensions, extraction vectors, descriptions and guided sequence.
- src/server/macMini.ts: M4 Pro parts, precise exterior size, bottom-opening guided walkthrough.
- src/server/macMini3d.ts: rounded aluminum extrusion, radial fan, copper cooling stack, Apple silicon, removable SSD, power board and realistic ports.
- src/server/hardware3d.ts: procedural GPU/CPU modules, metalwork, fans, PCBs, DIMMs, cables, liquid manifolds and dense rack trays.
- src/server/geometry.ts: original custom 2U geometry.
- src/server/Viewer.tsx: Three.js viewer via adapted MIT-licensed Bygga Stage, camera/picking/interpolation.
- src/App.tsx: machine tabs, collapsible inspector, fullscreen, exploder and guide.
- src/engine/*, src/lib/types.ts, src/lib/plan/math.ts: MIT-licensed Bygga code, copyright retained in LICENSE.

## Development

Use Node.js 22+ and a WebGL2-capable browser. Install dependencies with `npm install`, start the development server with `npm run dev`, and check the production build with `npm run build`.

The project has manual test scenarios in `tests/tests.json`; it does not define an automated test script. The original Bygga MIT copyright is retained in the root LICENSE.
