# Session 1 - What to test

Test data is my own, chosen to resemble real testing notes.

## A. Persistence

1. New map, root plus several nodes of testing notes
2. Fold a branch, add an icon to one node, bold another
3. Save as `session-map.mm`, quit
4. Reopen. Does everything match - text, fold state, icon, bold?
5. Rename a node ten times, then undo repeatedly. How many undos take?

## B. Text fidelity

Four shapes, each stressing something different:

1. Multi-line text with leading indentation
2. One very long unbroken line
3. Non-Latin text and emoji
4. Styled text pasted from a web page

Save, quit, reopen, confirm all four survived.

## C. Sweep

Roughly a minute each: multiple icons on one node, note, image, hyperlink,
find a string that exists only inside a note, zoom extremes, export as HTML,
print preview, browse mode, encrypted map.

## Investigate

Pin down the most interesting failure: preconditions, minimal steps, frequency.
