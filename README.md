# APEX KART

An original PC browser kart racer built with Three.js, Vite, and PeerJS. All worlds, karts, track illustrations, and character art are generated in code. Inspired by the arcade kart racing genre; no KartBros assets or source code are used.

## Play

- **WASD / arrow keys:** accelerate, brake, and steer.
- **Space + steering:** hold a drift at speed, then release for a charged turbo.
- **E:** use a collected turbo, rocket, shield, or banana.
- **R:** recover to the center of the track.
- **Escape:** pause solo races. Online races continue when the menu opens.

Choose Sunshore Circuit, Redrock Rally, or Neon Nights. Quick races have three laps and seven AI opponents. Difficulty changes AI pace. Time trial runs the course alone. Race results award XP; finishing races unlocks Jax (2), Rio (5), Pixel (10), and Phantom (20). Nova and Milo are available immediately. Profiles, unlocks, and best trial times are stored in this browser; clearing site data resets them.

For online play, select **Play with friends**, create a room, and share the six-character code. The host starts the race and must keep the tab open. Create a new room for each race. See [NETWORK.md](NETWORK.md) for connection details and limits.

## Run locally

Requires Node.js 22 or newer.

```sh
npm ci
npm run dev
```

Build the static website with `npm run build`. The deployable output is `dist/`. All asset URLs are relative, so GitHub repository subpaths work.

## Publish for free on GitHub Pages

1. Create a **public GitHub repository** and upload this project's source files, including `.github/workflows/deploy.yml`, `package.json`, and `package-lock.json`. Do not upload `node_modules`.
2. In the repository, open **Settings → Pages → Build and deployment → Source** and choose **GitHub Actions**.
3. Push the files to the `main` branch, or run **Actions → Deploy to GitHub Pages → Run workflow**.
4. When the workflow finishes, the deployment URL appears in **Settings → Pages** and the workflow's `github-pages` environment.

The included workflow installs locked dependencies, builds, and publishes `dist`. No paid game server is required for single-player or direct peer-to-peer rooms. Public signaling and STUN services have no uptime guarantee. A TURN relay is needed for connections on some restrictive networks. No secrets are needed for the included setup. The `.openai/hosting.json` file is only used by the separate Sites deployment; GitHub Pages ignores it.

## Hidden developer menu

Set the player name to **APEXDEV**. Press **F8** or **Ctrl + Shift + D** to open the developer pit lane. It provides infinite boost, invincibility, and speed multipliers for local practice. Assisted races do not count toward racer unlocks or best trial times. Tools are disabled online. This is an Easter egg in a public static client, not an authentication or security boundary.

## Verification and limits

Production builds and JavaScript syntax checks pass. Node checks exercise all three world construction/disposal paths and track continuity, item pickup and shield logic, drift release boosts, lap completion, and the room relay protocol with simulated peers. Browser rendering, keyboard feel, and live cross-network WebRTC still require a real desktop browser playtest. There is no public matchmaking, account system, authoritative server, anti-cheat, host migration, or global leaderboard. This is a compact playable arcade game, not a production-scale live service.
