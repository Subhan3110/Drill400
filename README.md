# Drill 400

Investment banking interview drills — 440 questions across accounting, valuation,
DCF, M&A, LBO, restructuring, capital markets, fit and brain teasers.

One file, no build step, no dependencies. Open `index.html` and start.

**[Live site](https://subhan3110.github.io/Drill400/)** (once GitHub Pages is enabled on this repo)

---

## What it does

- **Two question formats.** Multiple choice to check recall, written answers for
  the questions you would actually have to talk through.
- **Optional AI grading.** Paste an Anthropic API key and written answers get
  scored out of 10 with what landed, what was missing, and one delivery tip.
  Without a key everything still works — you self-mark against the model answer.
- **Spaced repetition, lightly.** Anything you get wrong is saved to *Ones you
  missed*. Getting it right later works the counter back down.
- **Progress tracking.** Questions seen, running accuracy, day streak, and a
  mastery bar per topic. A question counts as mastered once you have seen it and
  have no outstanding wrong answers on it.
- **Flags.** Mark any question to come back to it, then drill just those.
- **Resume.** Close the tab mid-set and pick up where you left off.
- **Review.** At the end of a set, expand any question to re-read the answer.
- **Keyboard driven.** `1`–`4` or `A`–`D` to answer, `Enter` to continue, `F` to
  flag, `Cmd/Ctrl+Enter` to grade a written answer.
- **Light and dark themes**, following your OS by default.

Everything is stored in your browser's `localStorage`. Nothing is sent anywhere
except, if you turn grading on, your answer to the Anthropic API.

## Running it

```
open index.html
```

That is the whole setup. To host it, push to GitHub and enable Pages on the
repository — it is a static file.

If you want AI grading, get a key at [console.anthropic.com](https://console.anthropic.com),
then click *Turn on AI grading of written answers* on the home screen. The key is
kept in `localStorage` in your browser and is sent only to Anthropic. Because the
site is static, the call goes directly from the browser, which is why it uses the
`anthropic-dangerous-direct-browser-access` header. Do not use a key you would
mind being visible on a shared machine.

## The question bank

| Topic | Questions |
|---|---|
| Accounting | 58 |
| Enterprise Value | 42 |
| Valuation | 50 |
| DCF | 50 |
| M&A / Merger Model | 50 |
| LBO | 48 |
| Restructuring | 36 |
| Markets & Capital Markets | 32 |
| Fit & Behavioural | 42 |
| Brain Teasers | 32 |
| **Total** | **440** |

Split 205 multiple choice / 235 written. By difficulty: 100 easy, 200 medium, 140 hard.

## Adding questions

Questions live in the arrays `Q` through `Q14` in the first `<script>` block of
`index.html`. Add to any of them, or start a new array and include it in the
`QUESTIONS` spread.

Multiple choice:

```js
{ c:"acct", l:2, t:"mc",
  q:"Interest expense increases by $10. Tax rate is 40%. What happens to net income?",
  o:["Falls by $10","Falls by $6","Falls by $4","No change, interest is non-cash"],
  a:1,
  e:"Interest is tax-deductible, so pre-tax income falls $10 and taxes fall $4..." }
```

Written:

```js
{ c:"dcf", l:2, t:"open",
  q:"How do you decide on the length of the explicit forecast period?",
  m:"The forecast runs until the business reaches a steady state..." }
```

| Field | Meaning |
|---|---|
| `c` | Category key — one of `acct`, `ev`, `val`, `dcf`, `ma`, `lbo`, `restr`, `mkts`, `fit`, `brain` |
| `l` | Difficulty: `1` easy, `2` medium, `3` hard |
| `t` | `"mc"` or `"open"` |
| `q` | The question |
| `o` | MC only — exactly four options |
| `a` | MC only — index of the correct option, `0`–`3` |
| `e` | MC only — why the answer is right, and ideally why the others are wrong |
| `m` | Written only — what a strong answer covers. This is also the reference the AI grader marks against, so it pays to be thorough |

Question ids are hashed from the category and question text, so you can reorder,
insert or delete questions without invalidating anyone's saved progress.

A few conventions worth keeping: avoid double quotes inside strings, write out
numbers in prose rather than relying on symbols, and for written answers aim to
cover not just the correct content but the structure a good candidate would use.

## Notes

- Stats are keyed per browser. Clearing site data resets progress.
- Progress from the original version of the app migrates automatically on first
  load.
