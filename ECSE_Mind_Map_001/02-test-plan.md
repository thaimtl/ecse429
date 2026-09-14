# ECSE_Mind_Map_001 - Session Plan

**Charter.** Identify capabilities and areas of potential instability of FreeMind.
Exercise each capability identified with data typical to the intended use.
**Intended use.** Testers taking testing notes in a mind map.

Approach: session-based exploratory testing.

## Environment

macOS 26.5.1 / arm64 / FreeMind 1.0.1 / JDK 21.

Most published FreeMind material targets 0.8.0 on Windows, so platform-specific behaviour on this build is unmapped territory and a likely source of findings.
Setup already produced one.

## Session shape

| Phase | Activity |
|---|---|
| Survey | Walk every menu, build a feature outline |
| Deep | Persistence and text fidelity, the two areas where failure costs the most |
| Sweep | One touch each on the remaining capabilities |
| Investigate | Chase the best failure far enough to write repro steps |

