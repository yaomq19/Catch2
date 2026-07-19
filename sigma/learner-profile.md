# Learner Profile
Updated: 2026-07-20 Asia/Shanghai

## Learning Style
- Concrete-example-first: responds best to inventory-style scenarios (T1..Tn with tags) and "predict which run / what's the output" questions. Abstract rules land only after a worked example.
- Learns by discovering contradictions through scaffolded counter-examples (the `[parser][json],[slow]` journey worked well). Don't hand the rule — build the scenario that breaks their current model.
- Reframe-then-revisit: when an abstract explanation doesn't land, drop to a simpler rule-first model first, then return to the precise terms (this worked for the "AutoReg namespace scope" reasoning in the prior session).
- Pace: moderate, willing to sit with struggle. No need to soften feedback — direct "this is a fail, here's why" is received well.
- Format: open-ended plain-text questions for depth; AskUserQuestion for structured / self-assessment moments.
- Self-driven boundary probing: generates deep "what-if" 追问 (e.g. single-section equivalence, trailing-check-runs-on-probe, path-dependence) that consolidate mastery PAST the planned lesson. When they bite on a question, let them run with it — it produces stronger learning than the linear roadmap; just gently steer back to milestones after.

## Misconception Patterns (observed 2+ times)
- Reports "representative examples" instead of exhaustive enumeration when asked "which X?" — surfaced 3× in concept 6 (missed T3/T4, then T2, then T4 again). General habit to watch: in any set-prediction task, require the learner to list every item and label each before accepting the answer.
- Can verbalize a rule before being able to operationalize it (said "comma = OR / union" but still omitted T2 on the next question). Pattern: articulate ≠ apply. Always follow a stated rule with a transfer/application check before counting it mastered.
- Confuses "fails one group" with "doesn't run" under union semantics — remember union is two-sided: runs = matches any group; doesn't run = matches no group.
- Strong, honest metacognition: proactively flags "I forgot" / "I don't know why." Well-calibrated, NOT over-confident. Do not mistake honest under-confidence for low ability — the conceptual model is usually further along than the self-report.
- CMake API syntax decays in recall while conceptual target-SELECTION stays solid every time (seen 3+ times: missing `3 REQUIRED`, missing source file in `add_executable`, singular `target_link_library`, missing `PRIVATE`, commas instead of spaces). Learner deprioritized syntax drill ("不重要"). Procedural/lookup, NOT conceptual — will resurface naturally in concept 9 (custom main, more CMake). Don't force drills; flag once and move on.

## Mastered Topics
| Topic | Concepts Mastered | Date | Key Strengths | Persistent Gaps |
|-------|-------------------|------|---------------|-----------------|
| Catch2 library | 7 / 11 | 2026-07-20 | failure attribution; CMake TARGET SELECTION (concept solid, syntax not); self-registration model; REQUIRE/CHECK control flow + downstream-dependency axis (REQUIRE protects downstream from running on broken state); SECTION execution tree DEEPLY consolidated (probe mechanism, trailing-code-runs-every-call, path-dependence smell, single-section equivalence); tag filters; floating-point (== unreliable + power-of-2 exactness rule); matchers; exception assertions | concepts 8-11 pending (8 = test design, clamp probe posed); CMake API syntax unstable (procedural, recurring); exhaustive-enumeration habit consolidating; under-confidence persists (rated solid concept-7 work "Shaky") |

## Metacognition
- Self-assessment accuracy: well-calibrated on RECALL (accurately flags forgotten items), but consistently UNDER-confident on overall MASTERY. Concept 7: rated "Shaky" despite one-shot practice passes + self-driven transfer + self-correction of a logic bug + boundary-probing questions. Pattern strengthened across sessions. Rule: do NOT use self-rating as a mastery gate — behavioral evidence (practice + transfer + self-correction) overrides self-report. No fluency illusion observed.
