# Luau Visualizer

A free, self-contained, browser-only Luau-style teaching debugger and simulated Roblox Explorer. No database, Flask, account or API keys are needed.

## Running

Because the source uses JavaScript ES modules, open it from a local HTTP server:

```sh
cd luau-visualizer
python -m http.server 8000
```

Visit http://localhost:8000. Alternatively upload **all four files** (`index.html`, `styles.css`, `app.js`, `engine.js`) to GitHub Pages, Cloudflare Pages or any other static host. Host over HTTPS. No build process is necessary.

## Quick start

1. Choose **Examples** (try the ban-list or Touched sample).
2. Click **Run script**, then press **Space** or **Step** to execute lines.
3. Open **Players**, join NightOwl_472 or another sample player.
4. Open **Events**, select `Door.ClickDetector.MouseClick`, pick a player and click **Trigger event**.
5. Press Space to step through the event callback. Watch variables change and the output appear.
6. **Stop session** to unlock the script editor. **Reset world** to revert your explorer.
7. Export a `.json` project to share with students; import to restore it.

## Important execution limitations

This version uses a custom, instrumented subset interpreter; it **does not run the real Luau VM**. It handles many teaching exercises but not all language features. Supported: `local`, `function`, closures, event callbacks, `if/elseif/else`, `while`, numeric and generic `for`, `break`, `continue`, `return`, arrays/tables, scopes, properties, indexing, operators including `+=`, and a set of common Roblox instance methods.

Not yet supported: Luau type annotations, modules/require, full Lua generic-for multiple iterator returns, all metatables, genuine Roblox engine physics, true asynchronous tasks and WaitForChild blocking, complete APIs. Nested synchronous function calls are step-aware, but event scheduling is intentionally simplified. `wait()` and `task.wait()` immediately return the supplied duration (or 0). `WaitForChild` currently returns an existing child or nil. This is a teaching simulator, not a security-hardened arbitrary-code platform.

**Note on safety:** Execution is capped by the interpreter step counter, but the interpreter currently runs on the UI thread and can block briefly on very large expressions or loops. Do not present it as a hardened untrusted multi-user sandbox.

## Licensing

This original app source can be hosted and shared freely. No external runtime packages, fonts, images or paid services are bundled.
