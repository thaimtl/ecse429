# Tester
Thai Tran - 261233478

# ECSE_Mind_Map_001 - Exploratory Testing of FreeMind

**Charter.** Identify capabilities and areas of potential instability of FreeMind.
Exercise each capability identified with data typical to the intended use of the application.
The intended use is to enable testers to take testing notes using a Mind Map.

Tested against FreeMind 1.0.1 on macOS 26.5.1 / arm64 / JDK 21.

## Start here

| File | What it is |
|---|---|
| [05-summary.md](05-summary.md) | **Read this first.** Findings, in order of severity |
| [04-session-notes.txt](04-session-notes.txt) | Full session sheet: charter, metrics, capability outline, running notes, bugs, issues |
| [02-test-plan.md](02-test-plan.md) | How the session was scoped and why coverage was ordered this way |
| [03-run-sheet.md](03-run-sheet.md) | What was tested |
| [01-freemind-macos-setup.md](01-freemind-macos-setup.md) | How the application was made to run at all, see note below |

## Findings

Three bugs, each with its own report and screenshot:

| Report | Finding | Severity |
|---|---|---|
| [bug-note-panel-buries-map.txt](bug-note-panel-buries-map.txt) | Reopening a map restores the note panel over the whole window, leaving the map unreachable with no in-app recovery | Blocking |
| [bug-multiline-paste-flattened.txt](bug-multiline-paste-flattened.txt) | Pasting multi-line text silently destroys every line break, permanently | High |
| [bug-remove-node-shortcut.txt](bug-remove-node-shortcut.txt) | Remove Node advertises a keyboard shortcut that does nothing | Low |

Two issues, recorded in the session sheet: `Enter` silently changes meaning on the root node, and root children are split across both sides of the map leaving no reading order.

## Evidence

| Screenshot | Shows |
|---|---|
| [note-panel-covers-map.png](note-panel-covers-map.png) | The note panel occupying the entire window, map unreachable |
| [multiline-paste-flattened.png](multiline-paste-flattened.png) | Six lines of shell output collapsed into one run of text |
| [remove-node-no-shortcut.png](remove-node-no-shortcut.png) | Context menu displaying a shortcut for Remove Node |
| [long-node-wraps.png](long-node-wraps.png) | A 9,996 character node stored and rendered without truncation |
| [java7-text-rendering.png](java7-text-rendering.png) | Text rendering under the bundled Java 7, see note below |

`ECSE 429 FreeMind testing.mm` is the map built during the session. Findings were verified by reading this file directly rather than trusting the screen, which is how the paste data loss was confirmed and how one suspected defect was ruled out.

## Note on the build

FreeMind 1.0.1 ships a bundled Java 7 that cannot render text on macOS 26. Characters are clipped and the interface is unreadable, as shown in `java7-text-rendering.png`. The application was repointed at JDK 21 before testing could begin.

This is a deviation from the shipped configuration, and any rendering observation should be read against it. The steps are recorded in [01-freemind-macos-setup.md](01-freemind-macos-setup.md).

## Coverage

Testing went deep on persistence and text fidelity, the two areas where failure costs a note-taker the most. Unicode entry, rich text paste, notes, images, hyperlinks, find, zoom, export, import, print, browse mode and encryption were identified in the capability outline but not exercised. No claim is made about them.
