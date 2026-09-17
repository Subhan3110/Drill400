# Drill 400

Investment banking interview drills — 459 multiple choice questions across
accounting, valuation, DCF, M&A, LBO, restructuring, capital markets, sectors
and brain teasers. Every answer comes with an explanation.

One file, no build step, no dependencies, no accounts. Open `index.html` and start.

**[Live site](https://subhan3110.github.io/Drill400/)**

---

## What it does

- **Multiple choice only.** Four options, one answer, and an explanation every
  time — not just why the right answer is right, but usually why the tempting
  wrong one is wrong.
- **Spaced repetition, lightly.** Anything you get wrong is saved to *Ones you
  missed*. Getting it right later works the counter back down.
- **Progress tracking.** Questions seen, running accuracy, day streak, and a
  mastery bar per topic. A question counts as mastered once you have seen it and
  have no outstanding wrong answers on it.
- **Multiplayer.** Pick a topic and length, press *Multiplayer*, and the link is
  there with a copy button — one press, no other steps. Whoever opens it gets
  that exact set, same questions in the same order. Both play on your own time,
  then send your result back and the app shows the head-to-head. If you have
  already played the set, a result link arriving back shows the comparison
  immediately without replaying.

  The whole set is encoded in the URL hash, so there is no server, no account
  and nothing to host — a 20-question invite is about 110 characters. Scores are
  self-reported, so it is for friends, not a ranked ladder.
- **Flags.** Mark any question to come back to it, then drill just those.
- **Resume.** Close the tab mid-set and pick up where you left off.
- **Review.** At the end of a set, expand any question to re-read the answer.
- **Light and dark themes**, following your OS by default.

Everything is stored in your browser's `localStorage`. Nothing is sent anywhere.

## Running it

```
open index.html
```

That is the whole setup. To host it, push to GitHub and enable Pages on the
repository — it is a static file. Add it to your phone's home screen and it opens
fullscreen like an app.

## The question bank

| Topic | Questions |
|---|---|
| Accounting | 69 |
| Valuation | 53 |
| DCF | 53 |
| M&A / Merger Model | 52 |
| LBO | 51 |
| Enterprise Value | 44 |
| Restructuring | 37 |
| Sectors | 34 |
| Brain Teasers | 34 |
| Markets & Capital Markets | 32 |
| **Total** | **459** |

By difficulty: 97 easy, 205 medium, 157 hard.

The **Sectors** section covers the industry-specific ground that generalist
question banks tend to skip: SaaS metrics, banks and insurers, healthcare and
biotech, consumer and retail, real estate and REITs, industrials, and oil and gas.

## Adding questions

Questions live in the `BANK` array in the first `<script>` block of `index.html`,
grouped by category. Add one anywhere in the array:

```js
{"c":"acct","l":2,"t":"mc",
 "q":"Interest expense increases by $10. Tax rate is 40%. What happens to net income?",
 "o":["Falls by $10","Falls by $6","Falls by $4","No change, interest is non-cash"],
 "a":1,
 "e":"Interest is tax-deductible, so pre-tax income falls $10 and taxes fall $4..."}
```

| Field | Meaning |
|---|---|
| `c` | Category key — one of `acct`, `ev`, `val`, `dcf`, `ma`, `lbo`, `restr`, `mkts`, `sect`, `brain` |
| `l` | Difficulty: `1` easy, `2` medium, `3` hard |
| `t` | Always `"mc"` |
| `q` | The question |
| `o` | Exactly four options |
| `a` | Index of the correct option, `0`–`3` |
| `e` | Why the answer is right, and ideally why a tempting wrong one is wrong |

Question ids are hashed from the category and question text, so you can reorder
or insert questions without invalidating saved progress. Deleting questions will
break any challenge links already shared, since those encode positions.

Conventions worth keeping: avoid double quotes inside strings, write numbers out
in prose, make the wrong options genuinely plausible rather than obviously wrong,
and check any arithmetic independently before committing it.

## Notes

- Progress is per browser. Clearing site data resets it.
- Progress from earlier versions of the app migrates automatically on first load.
