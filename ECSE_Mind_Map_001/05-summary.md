# Session 1 Summary - ECSE_Mind_Map_001

FreeMind 1.0.1 on macOS 26.5.1 / arm64 / JDK 21.

## Bugs

**1. Note panel buries the map. Blocking.**
Reopening a saved map restored the note panel filling the entire window. The map pane had no height, and no in-application recovery worked: the split divider could not be grabbed, Escape did nothing, and the panel toggle had no effect. Caused by `split_pane_position` in `auto.properties` being restored without validating that the map pane remains usable. Recoverable only by editing that file outside the application.
Evidence: `note-panel-covers-map.png`. Full report: `bug-note-panel-buries-map.txt`.

**2. Multi-line paste silently discards line breaks.**
Pasting several lines into a node converts every newline to a single space. The newlines are absent from the saved `.mm` in every encoding, so the loss happens at paste time and is permanent. Spacing within each line survives, which makes the damage easy to miss. This is the finding most directly opposed to the intended use, since pasting log output and stack traces into notes is routine for a tester.
Evidence: `multiline-paste-flattened.png`. Full report: `bug-multiline-paste-flattened.txt`.

**3. Remove Node advertises a shortcut that does nothing.**
The context menu displays a keyboard shortcut for Remove Node, but no key press invokes it. The shipped configuration binds that action to `none`, while the delete key is claimed twice by two other actions. Node removal requires the mouse.
Evidence: `remove-node-no-shortcut.png`. Full report: `bug-remove-node-shortcut.txt`.

## Issues

1. `Enter` is bound to "new sibling" but creates a child when the root is selected, since the root has no parent. The key changes meaning with no feedback.
2. Children of the root are distributed across both sides of the map, leaving no clear reading order for a set of notes.
