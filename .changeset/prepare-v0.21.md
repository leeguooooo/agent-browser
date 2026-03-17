---
"agent-browser": minor
---

### New Features

- **`batch` command** -- Execute multiple commands from stdin in a single invocation. Accepts a JSON array of string arrays and returns results sequentially. Supports `--bail` to stop on first error and `--json` for structured output (#865)
- **iframe support** -- CLI interactions and snapshots now traverse into iframe content, enabling automation of cross-frame pages (#869)
- **`network har start/stop` command** -- Capture and export network traffic in HAR 1.2 format (#874)
- **WebSocket fallback for CDP discovery** -- When HTTP-based CDP endpoint discovery fails, the CLI now falls back to a WebSocket connection automatically (#873)

### Improvements

- **`--full`/`-f` refactored to command-level flag** -- Moved from a global flag to a per-command flag for clearer scoping (#877)
- **Enhanced Chrome launch** -- Added `--user-data-dir` support and configurable launch timeout for more reliable browser startup (#852)

### Bug Fixes

- Fixed `/json/list` fallback when `/json/version` endpoint is unavailable, improving compatibility with non-standard CDP implementations (#861)
- Fixed daemon liveness detection for PID namespace isolation (e.g. `unshare`). Uses socket connectivity as the sole liveness check instead of `kill(pid, 0)`, which fails when the caller cannot see the daemon's PID (#879)
- Fixed Ubuntu dependency install accidentally removing system packages (#884)
