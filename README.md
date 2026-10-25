# Skybound - Free Web Flight Sim

A free, browser-based 3D flight simulator. Fly from London Heathrow to airports across Europe, explore a London-inspired landscape, or try an assisted spacecraft launch.

**Play online:** [Skybound - Free Web Flight Sim](https://skybound-free-web-flight-sim.amberberry9.chatgpt.site)

## Features

- **Aircraft selection:** Cessna 172; Airbus A220, A300, A310, A320, A330, A340, A350, and A380 families; Beluga ST and BelugaXL; A400M; Boeing 737 and 777; Su-35; and F-35B with VTOL.
- **Spaceflight:** Space Shuttle Atlantis and Falcon 9 with a launchpad and guided or manual ascent.
- **Flight experience:** takeoff, climb, turns, descent, landing, braking, crash recovery, and restart.
- **Cameras:** chase, freecam follow, and cockpit views.
- **Airports and routes:** Heathrow, London City, Gatwick, Luton, Stansted, Northfield Field, and major European destinations. Select a destination on the map or from the menu.
- **Airport operations:** gate starts, taxiways, terminal scenery, and guided taxi between runway and gates.
- **Flight tools:** instruments, interactive map, flight plan, autopilot, replay recorder, approach skip, and 100 km fast-forward.
- **Environment:** procedural London and Europe scenery, London landmarks, neighborhoods, weather presets, and time-of-day settings.
- **Difficulty:** Beginner, Intermediate, and Hard modes.

The simulator uses Three.js and native JavaScript modules. It runs as a static website and does not require a paid service or API key. An internet connection is needed for the Three.js CDN and online imagery resources.

## Run locally

You need Python 3 or Node.js and a modern browser with WebGL.

```sh
git clone <your-repository-url>
cd <repository-folder>
python3 -m http.server 8000
```

Then open [http://localhost:8000](http://localhost:8000). You can also run `npx serve .` with Node.js. Do not open `index.html` directly as a `file://` URL; browser module security requires an HTTP server.

## Controls

| Key | Action |
| --- | --- |
| `W` / `S` | Increase / decrease throttle |
| `↑` / `↓` | Pitch up / down |
| `←` / `→` | Bank and turn |
| `A` / `D` | Rudder; also helps steer on the ground |
| `Space` | Hold to brake; cancels guided taxi |
| `C` | Cycle chase, freecam follow, and cockpit cameras |
| `G` | Retract / extend landing gear where available |
| `F` | Cycle flaps |
| `X` | Toggle spoilers / speedbrakes where available |
| `V` | Replay; toggles F-35B VTOL when flying the F-35B |
| `N` | Open / close the flight plan |
| `R` | Restart at the selected starting position |
| `Esc` | Pause and open the menu |

The on-screen **CONTROLS** panel also lists the controls. A standard gamepad is supported.

### First flight

1. Choose an aircraft, starting airport, runway or gate, and destination.
2. Select **Beginner** to start with flight protection. From a gate, use **TAXI TO RUNWAY**.
3. Increase throttle with `W`, stay aligned with the runway, and gently pitch up near the aircraft's rotation speed.
4. Climb and turn toward your destination. Use the live instruments and map to monitor the flight.
5. Reduce power and descend toward the runway. Touch down with a shallow descent and wings close to level, then hold `Space` to brake.

Use **APPROACH** to begin near the selected destination, or **+100KM** to skip part of a long flight.

### Difficulty levels

- **Beginner:** flight-envelope and stall protection are available. The optional beginner assist can be toggled in the controls panel.
- **Intermediate:** reduced stability, with limited stall and flight-envelope protection.
- **Hard:** no flight stabilization, stall recovery, pitch trim, or autopilot. For spacecraft, launch power is automatic, but you control pitch-over yourself: hold `↓` after **AUTO LAUNCH** to pitch away from vertical.

### Spaceflight

Choose **Space Shuttle Atlantis** or **Falcon 9**. Both start upright on the launchpad. In Beginner or Intermediate, press **AUTO LAUNCH** for an assisted ascent. In Hard, use the arrow keys to control pitch and steering after launch. **RESET TO LAUNCHPAD** restarts the attempt.

## Project structure

```text
index.html                 Interface and simulator shell
style.css                  UI styling
src/main.js                Game loop, rendering, cameras, map, instruments, and UI
src/physics.js             Flight, ground, and spacecraft simulation
src/input.js               Keyboard and gamepad input
src/aircraft.js            Aircraft profiles and procedural models
src/airports.js             Airport data and Europe map coordinates
src/taxi.js                 Airport gates and guided taxi routes
src/autopilot.js            Route and altitude assistance
src/replay.js               Flight recording and replay
src/world.js                Three.js scene, lighting, and camera support
src/europe.js               Procedural Europe scenery
src/londonEnvironment.js    Procedural London scenery
src/audio.js                Synthesized engine audio
assets/aircraft/            Aircraft models and attribution
```

## Aircraft assets and imagery

Some aircraft models are third-party assets. Their credits and license information are in [assets/aircraft/ATTRIBUTION.md](assets/aircraft/ATTRIBUTION.md); the included model collection is licensed under CC BY 4.0. Other aircraft and scenery are procedural approximations made for the simulator. Models are not exact replicas of real aircraft.

The London terrain uses EOxCloudless Sentinel-2 imagery. Attribution is shown in the simulator, and the public imagery layer is licensed for non-commercial use. Wider Europe scenery is procedural and does not use detailed satellite imagery throughout.

## Limitations

This is an arcade-style regional simulator, not a certified training tool or physically accurate orbital simulator. Flight physics are simplified. Europe airports and terrain are modeled for gameplay; the project does not include live weather, real air traffic, multiplayer, worldwide coverage, or surveyed elevation data. Some aircraft variants share a related model or use procedural geometry.
