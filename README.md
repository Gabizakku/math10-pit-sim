# When Do We Pit?

A pit strategy simulator: which lap should a driver pit on?

MATH 10 culminating project, Venice Sumadchat, Shandler Ngu, Zach Dela Cruz.
Sir Durwin, Canvas 68784.

The whole exhibit is `index.html`: one file, no libraries, no network calls.
Open it from a USB stick and it works.

## What the page shows

Three parts, as the project proposal promises.

1. **Parameters.** Three sliders: fresh-tyre lap time `t0`, tyre wear `k` in
   seconds per lap, and race distance `N` in laps.
2. **The graph.** The predicted total race time `T(p)` for every lap `p` you
   could stop on, the cheapest lap marked, and the pit window shaded, where
   the window is every lap within `ΔT = 1 s` of the cheapest time.
3. **The race.** A car on the circuit, a play button and a race timer. The car
   runs at 5× real time, stands in the pit box for one second on your pit lap
   (the 20-second stop, compressed so it is watchable), and finishes on the last
   lap. The timer is not a stopwatch, it is the model: at the flag it reads
   exactly the `T(p)` the graph predicted.

The model, per the proposal:

    lap n on a set of tyres   t(n) = t0 + k*n
    a stint of p laps         S(p) = p*t0 + k*p*(p-1)/2
    a stop after lap p        T(p) = S(p) + 20 + S(N-p)
    the pit window            T(p) <= T(p*) + 1

## How the maths is checked

| file | what it proves | run |
|---|---|---|
| `model.py` | the model spec, brute-force optimum, 82 reference cases | `python model.py` |
| `test_core.js` | the page's maths matches the Python reference | `node test_core.js` |
| `test_sim.js` | the race schedule the animation replays equals `T(p)`, the pit window equals the brute-force set, and the closed form holds on 100 input combinations | `node test_sim.js` |

`build_site.py` assembles `index.html` from `exhibit/` plus `core.js`, so the
page can never open on numbers nobody verified.
