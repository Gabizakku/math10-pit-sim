# When Do We Pit?

A pit strategy simulator: when does a single pit stop start paying for itself?

MATH 10 culminating project, Venice Sumadchat, Shandler, Zach Dela Cruz.
Sir Durwin, Canvas 68784.

The whole exhibit is `index.html`. One file, no libraries, no network. Open it
from a USB stick and it works. The maths behind it is checked by `model.py` in
the project folder; the page is generated from those files, so it cannot open on
numbers nobody verified.

## Using it

Four sliders set the race: distance, fresh-tyre lap time, degradation per lap,
and pit loss. The page draws the cost of every possible pit lap, marks the
cheapest one, says so in a sentence, and lists the cost of zero to four stops.

The fitter at the bottom takes one stint of lap times, one per line or as a CSV,
runs a least-squares fit, drops in-laps and traffic laps, and returns the two
numbers the model needs.

## Honest note on the data

The lap-time column used while building the page is simulated and labelled as
such. The real stint is still owed to us. A replacement drops into the same
fitter with no code change.
