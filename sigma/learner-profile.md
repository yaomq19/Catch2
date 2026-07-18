# Learner Profile
Updated: 2026-07-18 Asia/Shanghai

## Learning Style
- Concrete-example-first: responds best to inventory-style scenarios (T1..Tn with tags) and "predict which run / what's the output" questions. Abstract rules land only after a worked example.
- Learns by discovering contradictions through scaffolded counter-examples (the `[parser][json],[slow]` journey worked well). Don't hand the rule — build the scenario that breaks their current model.
- Reframe-then-revisit: when an abstract explanation doesn't land, drop to a simpler rule-first model first, then return to the precise terms (this worked for the "AutoReg namespace scope" reasoning in the prior session).
- Pace: moderate, willing to sit with struggle. No need to soften feedback — direct "this is a fail, here's why" is received well.
- Format: open-ended plain-text questions for depth; AskUserQuestion for structured / self-assessment moments.

## Misconception Patterns (observed 2+ times)
- Reports "representative examples" instead of exhaustive enumeration when asked "which X?" — surfaced 3× in concept 6 (missed T3/T4, then T2, then T4 again). General habit to watch: in any set-prediction task, require the learner to list every item and label each before accepting the answer.
- Can verbalize a rule before being able to operationalize it (said "comma = OR / union" but still omitted T2 on the next question). Pattern: articulate ≠ apply. Always follow a stated rule with a transfer/application check before counting it mastered.
- Confuses "fails one group" with "doesn't run" under union semantics — remember union is two-sided: runs = matches any group; doesn't run = matches no group.
- Strong, honest metacognition: proactively flags "I forgot" / "I don't know why." Well-calibrated, NOT over-confident. Do not mistake honest under-confidence for low ability — the conceptual model is usually further along than the self-report.

## Mastered Topics
| Topic | Concepts Mastered | Date | Key Strengths | Persistent Gaps |
|-------|-------------------|------|---------------|-----------------|
| Catch2 library | 7 / 11 | 2026-07-19 | failure attribution; CMake targets; self-registration model; REQUIRE/CHECK control flow; SECTION execution tree; tag filters; floating-point (== unreliable + Approx + tolerance math); matchers (REQUIRE_THAT + combinators + diagnostic value); exception assertions (REQUIRE_THROWS_AS family + custom types) | concepts 8-11 pending; exhaustive-enumeration habit still fragile; under-confidence persists (rated solid concept-7 work "Shaky") |

## Metacognition
- Self-assessment accuracy: well-calibrated on RECALL (accurately flags forgotten items), but consistently UNDER-confident on overall MASTERY. Concept 7: rated "Shaky" despite one-shot practice passes + self-driven transfer + self-correction of a logic bug + boundary-probing questions. Pattern strengthened across sessions. Rule: do NOT use self-rating as a mastery gate — behavioral evidence (practice + transfer + self-correction) overrides self-report. No fluency illusion observed.
