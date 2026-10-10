# lane_lint

A small, dependency-free checker for roleplay text. It finds **"head-hopping"**: replies where the model writes the *other* character's words, actions, feelings or completed outcomes, instead of staying in its own lane.

Use it on model replies, on transcripts, or on any roleplay passage you want to check.

## Use
```
# check a whole file (chat format: system / user / assistant messages, JSON lines)
python3 lane_lint.py examples/sample.jsonl

# check one passage, saying who is speaking and who the other character is
python3 lane_lint.py --text passage.txt --self Ava --other Ben
# if the other character is addressed as "you" (second person), add --second-person
```
Options: `--strict` (also show low-severity hits), `--show N` (how many flagged examples to print), `--json out.json` (write the full report).

## What it flags
| Severity | Meaning |
|---|---|
| HIGH | The other character is written as the subject doing, saying or feeling something; a speaker label appears; or (second person) "you" does a completed reaction. Rewrite these. |
| LOW | Hedged reads ("seemed to", "looked like") or the other character's body part as a possessive. Review only. |
| REVIEW | A he/she/they does something; usually the other character, sometimes an NPC. |
| HORROR | Violence described as already *landing* on the other character's body. End on the attempt and leave the landing to the other writer. Damage to yourself, monsters, NPCs, objects and the room is allowed. |

## Limits
It is a set of text heuristics, not a language model. It will miss some cases and flag some fine ones. Treat it as a first pass that saves you reading time, not a replacement for reading the text.

## License
MIT (see `LICENSE`).

## Questions
By Anthony "Othello" Merriweather, WordBlock Labs (wordblocklabs.com). Questions or problems: wordblocklabs.com/support or support@wordblocklabs.com.
