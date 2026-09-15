# Tester
Thai Tran - 261233478

# ECSE_Test_Ideas_002 - Test Ideas for Wrap-O-Matic

**Exercise.** Generate testing ideas for a fictitious product, two of each of five types, ten in total.
A test idea here is a potential testing objective, a statement of what we might want to learn, in 160 characters or less.
Ideas are not prioritized or triaged for this exercise.

The product is Wrap-O-Matic, an automated chocolate wrapping and boxing line.
Unwrapped chocolates arrive on a conveyor, are wrapped in paper, and are laid into boxes according to an entered manifest.

## Deliverable

[Test_Ideas_List.xlsx](Test_Ideas_List.xlsx) is the submission.
Columns are ID, Type, Test Idea, Source, and Notes.
The table below mirrors it so the ideas are readable without opening the spreadsheet.

| ID | Type | Test Idea | Source (Product Variable Map) |
|---|---|---|---|
| TI-01 | Capabilities | Whether the wrapper seals correctly for all 7 chocolate configurations (truffle, praline, bar, turtle, bon bon, filled, traditional) across all 3 sizes. | Inputs > Chocolates > Configuration, Size |
| TI-02 | Capabilities | Whether an entered manifest drives correct box layout for every box type (rectangular, circular, heart, OEM custom, bag), size, and layer count. | Inputs > Manifest; Inputs > Empty Boxes > Type, Size, Configuration |
| TI-03 | Failure Modes | What the machine does when wrapping paper runs out mid-run: stop, reject, or keep boxing unwrapped chocolates while reporting a normal run. | Inputs > Paper > None; Users > Loader > Chocolate Wrapping Paper |
| TI-04 | Failure Modes | Whether out-of-spec chocolates (too light, too heavy, jelly, hollow) divert to the reject output instead of jamming or crushing inside the wrapper. | Inputs > Chocolates > Weight, Viscosity; Outputs > Rejected Chocolates |
| TI-05 | Quality Factors | Whether wrap quality and reject rate hold as conveyor speed steps slow to very fast under a dense, randomly distributed input stream. | Inputs > Input Stream > Conveyor Speed, Frequency, Distribution |
| TI-06 | Quality Factors | Whether a peanut batch is fully purged at changeover so no trace reaches the next peanut-free run, and whether the inspector can prove it. | Users > Health Inspector > Peanuts, Contamination, Ingredients match labels |
| TI-07 | Usage Scenarios | Loader replenishing paper and ribbon in all three states (operating, idle, powered down): whether each is safe, permitted, and logged to stock. | Users > Loader > Chocolate Wrapping Paper (operating / idle / powered down), Ribbons |
| TI-08 | Usage Scenarios | Whether an auditor can reconcile prod run, daily, and monthly reports into matching totals after an operator stops and restarts mid-batch. | Users > Auditor > Batch, Daily, Monthly reports; Users > Operator > Starts, Stops |
| TI-09 | Creative Ideas | Feeding an already-wrapped chocolate back onto the belt: does the machine double-wrap it, reject it, or mis-count it as new production? | Inputs > Input Stream; Outputs > Wrapped box of chocolates |
| TI-10 | Creative Ideas | Entering a manifest whose layout cannot physically fit the loaded box (24 large turtles in a small heart box): is it caught before stock is consumed? | Inputs > Manifest; Inputs > Empty Boxes > Size; Inputs > Chocolates > Size |

## Scope and sourcing

Every idea traces to a named node in `Product_Variable_Map.mm`, recorded in the Source column.
The map covers the whole machine rather than the wrapping station alone, so boxing, manifests, reports, and health inspection are all in scope.

Coverage was spread across the map on purpose.
Inputs are hit through chocolate configuration, weight, viscosity, size, paper stock, and the input stream.
Users are hit through the loader, the operator, the auditor, and the health inspector.
Outputs are hit through the reject stream and the three report types.

The status light, ribbon variants, box wrapping materials, and the maintainer role are named in the map but carry no idea here.
No claim is made about them.

## Granularity

The target size is roughly two hours to elaborate and run each idea, assuming the machine behaves.

TI-01 is the largest at 21 configuration and size combinations, and would be sampled rather than run exhaustively.
TI-09 is the smallest and could be tried in minutes.
The remaining eight sit close to the two hour target.
