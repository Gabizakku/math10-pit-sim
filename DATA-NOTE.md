# Data, one stint of lap times

## What is owed

Gantt activity 3, owner Shandler, was due 10-29. The ask is **one column of lap
times from a single stint**, nothing else:

* one lap time per line, in order
* no lap numbers, no headings, no commentary
* `84.53` or `1:24.53` both work
* 15 to 20 laps is plenty
* in-laps, out-laps and traffic laps can stay in. The fitter drops them by itself
  (median-absolute-deviation filter, 3 sigma) and says which laps it dropped.

Put it in this folder as `stint_real.csv` and run:

```
python fit_stint.py data/stint_real.csv
```

## What is in here now

| file | what it is | may it be submitted? |
|---|---|---|
| `stint_template.csv` | empty template with the header only | no, it has no data |
| `stint_simulated.csv` | **simulated** stint, fixed seed, from t0 = 84.5 s and k = 0.035 s/lap, noise sd 0.12 s, one deliberate in-lap at lap 14 | **no** |
| `make_simulated_stint.py` | the generator for the above, so anyone can rebuild it exactly | n/a |

The simulated file exists for one reason: the fitting code needs something with a
known right answer while the real numbers are still owed. It is labelled everywhere
it appears. If it ends up in the report without that label, the report is making a
claim the group cannot support, and that is the one thing this project should not do.
A pit strategy simulator built on invented timing data would be a house with no
foundation, and Sir Durwin can ask for the source of any number on the page.

## Replacing it

Drop the real file in, run `python fit_stint.py data/stint_real.csv`, and put the
printed `t0` and `k` into the exhibit's sliders, or paste the column into the
fitter box on the page and press Fit. Same code path, no edit needed.
