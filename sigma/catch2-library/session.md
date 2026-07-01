# Session: Catch2 Library

## Learner Profile
- Level: C++ foundation is usable; systematic unit testing experience is limited.
- Language: zh
- Started: 2026-06-30 Asia/Shanghai
- Goal: Learn practical Catch2 usage first, then read the internal implementation.
- Current concept: Tags, filters, and command-line selection

## Concept Map
| # | Concept | Prerequisites | Status | Score | Last Reviewed | Review Interval |
|---|---------|---------------|--------|-------|---------------|-----------------|
| 1 | Test intent and failure attribution | - | mastered | 90% | 2026-06-30 | 1d |
| 2 | Minimal Catch2 executable and CMake targets | 1 | mastered | 90% | 2026-06-30 | 1d |
| 3 | TEST_CASE and self-registration model | 2 | mastered | 92% | 2026-07-01 | 1d |
| 4 | REQUIRE, CHECK, and assertion control flow | 3 | mastered | 90% | 2026-07-01 | 1d |
| 5 | SECTION as an execution tree | 3, 4 | mastered | 90% | 2026-07-01 | 1d |
| 6 | Tags, filters, and command-line selection | 3 | in-progress | 82% | - | - |
| 7 | Matchers, exceptions, and floating-point assertions | 4 | not-started | - | - | - |
| 8 | Designing useful tests for own code | 1, 4, 5 | not-started | - | - | - |
| 9 | Custom main and Catch::Session | 2, 6 | not-started | - | - | - |
| 10 | Source tour: macros, registry, run context, reporters | 3, 4, 9 | not-started | - | - | - |
| 11 | Extension points: listeners, reporters, generators, benchmarks | 10 | not-started | - | - | - |

## Misconceptions
| # | Concept | Misconception | Root Cause | Status | Counter-Example Used |
|---|---------|---------------|------------|--------|----------------------|
| 1 | Test intent and failure attribution | If a simple `std::vector` behavior test fails, first suspect `std::vector` itself. | The trusted layer stack is not separated from the unit under test; dependency behavior and test code are being treated as equally likely first suspects. | resolved | `reserve` changes capacity, not size; `clamp_to_percent(150)` should clamp to `100`. |
| 2 | Minimal Catch2 executable and CMake targets | `add_executable` might automatically search linked libraries for `main`. | CMake target creation and the later linker step are being treated as one operation. | resolved | `add_executable` creates the target from sources; `target_link_libraries` attaches Catch2 libraries, include paths, and optionally the default `main`. |
| 3 | Minimal Catch2 executable and CMake targets | The right Catch2 target is enough even if CMake command spelling, target name, or version syntax is off. | Conceptual target selection is understood, but exact CMake API usage has not been stabilized yet. | resolved | Corrected to `find_package(Catch2 3 REQUIRED)`, `add_executable(my_tests test.cpp)`, and `target_link_libraries(my_tests PRIVATE Catch2::Catch2WithMain)`. |
| 4 | TEST_CASE and self-registration model | `TEST_CASE` might only create a registration object, without also producing a callable test body. | The registration side is understood, but the executable payload that gets registered has not been made explicit yet. | resolved | A registry entry needs both metadata and a callable test body, commonly understood as a generated function. |
| 5 | TEST_CASE and self-registration model | `AutoReg` could live inside the generated test function. | Registration must happen before the runner can decide to invoke the test function; a local object inside that function would be constructed too late. | resolved | If registration waits for `TestName()` to be called, Catch2 cannot discover `TestName()` before calling it. |

## Session Log
- [2026-06-30 00:00 Asia/Shanghai] Started new Catch2 learning session.
- [2026-06-30 00:00 Asia/Shanghai] Goal selected: both practical usage and source understanding.
- [2026-06-30 00:00 Asia/Shanghai] Initial level selected: C++ foundation is usable; testing experience is limited.
- [2026-06-30 00:00 Asia/Shanghai] Diagnostic answer: identified `TEST_CASE` registration and `REQUIRE` checks in a vector example.
- [2026-06-30 00:00 Asia/Shanghai] Diagnostic gap: when asked what to suspect first on failure, learner chose `std::vector` implementation.
- [2026-06-30 00:00 Asia/Shanghai] Counter-example handled: learner correctly identified that a failing `reserve` test likely has the wrong expectation because `reserve` does not change `size`.
- [2026-06-30 00:00 Asia/Shanghai] Transfer scenario handled: learner correctly identified that `clamp_to_percent(150) == 0` is a wrong test expectation and should be `100`.
- [2026-06-30 00:00 Asia/Shanghai] Practice completed: learner wrote three boundary assertions for `clamp_to_percent`; logical coverage was correct, with a minor missing-semicolon syntax issue.
- [2026-06-30 00:00 Asia/Shanghai] Concept 1 mastered. Concept 2 started.
- [2026-06-30 00:00 Asia/Shanghai] Concept 2 gap: learner does not yet know the difference between `Catch2::Catch2` and `Catch2::Catch2WithMain`.
- [2026-06-30 00:00 Asia/Shanghai] Concept 2 progress: learner correctly inferred that a test executable without user-provided `main` should link `Catch2::Catch2WithMain`.
- [2026-06-30 00:00 Asia/Shanghai] Concept 2 gap: learner was unsure which target to link when providing a custom `main` that calls `Catch::Session`.
- [2026-06-30 00:00 Asia/Shanghai] Concept 2 progress: learner correctly identified that linking a default-main library while also defining `main` would create two `main` definitions and fail to link.
- [2026-06-30 00:00 Asia/Shanghai] Concept 2 progress: learner correctly chose `Catch2::Catch2` for custom-main tests because `Catch2::Catch2WithMain` would provide a second `main`.
- [2026-06-30 00:00 Asia/Shanghai] Concept 2 partial answer: learner knows the executable needs a `main`, but currently conflates `add_executable` with the later library-linking step.
- [2026-06-30 00:00 Asia/Shanghai] Counter-example step: learner correctly identified `add_executable(my_tests test.cpp)` as target creation with sources, not Catch2 lookup or test discovery.
- [2026-06-30 00:00 Asia/Shanghai] Counter-example resolved: learner correctly identified `target_link_libraries(my_tests PRIVATE Catch2::Catch2WithMain)` as the step that attaches Catch2 dependencies and the provided default `main`.
- [2026-06-30 00:00 Asia/Shanghai] Practice attempt for concept 2: learner chose `Catch2::Catch2WithMain` correctly, but used imprecise CMake syntax (`v3`, `target_link_library`) and did not preserve the requested target name `my_tests`.
- [2026-06-30 00:00 Asia/Shanghai] Practice retry for concept 2: learner still chose the right Catch2 target, but omitted the requested major version, used `my_test` instead of `my_tests`, and repeated singular `target_link_library`.
- [2026-06-30 00:00 Asia/Shanghai] Practice retry for concept 2: learner corrected `find_package(Catch2 3 REQUIRED)`, target name `my_tests`, and `target_link_libraries`; remaining issue is missing modern CMake scope keyword such as `PRIVATE`.
- [2026-06-30 00:00 Asia/Shanghai] Learner correctly chose `PRIVATE` because the test executable consumes Catch2 and does not need to propagate it to downstream dependents.
- [2026-06-30 00:00 Asia/Shanghai] Concept 2 mastered. Concept 3 started.
- [2026-06-30 00:00 Asia/Shanghai] Concept 3 progress: learner correctly rejected compile-time execution and CMake modification, and identified that `TEST_CASE` likely creates a registration object. Missing piece: it must also produce a callable test body for the registry to invoke later.
- [2026-06-30 00:00 Asia/Shanghai] Concept 3 progress: learner identified that a callable function/test body must exist in addition to the registration object.
- [2026-06-30 00:00 Asia/Shanghai] Concept 3 progress: learner correctly identified registration as occurring during executable startup before `main`, not during compilation, CMake configure, or after assertions execute.
- [2026-06-30 00:00 Asia/Shanghai] Source checkpoint: current code maps `TEST_CASE` to `INTERNAL_CATCH_TESTCASE`, which generates a static test function and a namespace-scope `Catch::AutoReg` object.
- [2026-06-30 00:00 Asia/Shanghai] Concept 3 progress: learner correctly identified `&TestName` as the function address passed to the invoker.
- [2026-06-30 00:00 Asia/Shanghai] Concept 3 gap: learner does not yet understand why `AutoReg` must live at namespace scope instead of inside the generated test function.
- [2026-06-30 00:00 Asia/Shanghai] Concept 3 progress: learner correctly identified that a namespace-scope `Registrar` can be constructed before `main` even if `test()` has not been called.
- [2026-06-30 00:00 Asia/Shanghai] Concept 3 gap persists: learner is not yet able to connect local-in-function registration with the runner's need to discover tests before invoking them.
- [2026-07-01 00:00 Asia/Shanghai] Concept 3 gap needs rephrasing: learner did not understand the registry-before-invocation ordering explanation.
- [2026-07-01 00:00 Asia/Shanghai] Teaching adjustment: prior explanation was too abstract; switch to a simpler rule-first model before returning to source terms.
- [2026-07-01 00:00 Asia/Shanghai] Concept 3 progress: learner confirmed that `AutoReg` lives outside the generated test function so registration happens before `TestName()` is invoked.
- [2026-07-01 00:00 Asia/Shanghai] Concept 3 progress: learner correctly mapped simplified macro expansion: forward declaration for `makeTestInvoker(&TestName)`, namespace-scope `AutoReg` for registration, and final function body for the test implementation.
- [2026-07-01 00:00 Asia/Shanghai] Practice completed for concept 3: learner wrote pseudocode with function declaration, function-external registration, and function definition for a `TEST_CASE`.
- [2026-07-01 00:00 Asia/Shanghai] Concept 3 mastered. Concept 4 started.
- [2026-07-01 00:00 Asia/Shanghai] Concept 4 gap: learner does not yet know the control-flow difference between `REQUIRE` and `CHECK` after assertion failure.
- [2026-07-01 00:00 Asia/Shanghai] Concept 4 progress: learner correctly stated that a failed `REQUIRE` stops the current test case, so following assertions are not executed.
- [2026-07-01 00:00 Asia/Shanghai] Concept 4 progress: learner correctly stated that a failed `CHECK` lets later assertions run, while the test case is still marked failed.
- [2026-07-01 00:00 Asia/Shanghai] Concept 4 progress: learner correctly chose `REQUIRE(user != nullptr)` for a prerequisite before dereferencing `user`.
- [2026-07-01 00:00 Asia/Shanghai] Concept 4 progress: learner correctly chose `CHECK` for independent profile fields to collect multiple failures in one run.
- [2026-07-01 00:00 Asia/Shanghai] Practice completed for concept 4: learner used `REQUIRE(order != nullptr)` as a prerequisite and `CHECK` for independent fields.
- [2026-07-01 00:00 Asia/Shanghai] Concept 4 mastered. Concept 5 started.
- [2026-07-01 00:00 Asia/Shanghai] Concept 5 progress: learner guessed correctly that Catch2 executes the `TEST_CASE` multiple times, entering one section path per run. Rationale still needs grounding in state isolation.
- [2026-07-01 00:00 Asia/Shanghai] Concept 5 progress: learner correctly explained that the `clear` section starts from the shared setup with one element, because sibling section `push second` did not execute on that path.
- [2026-07-01 00:00 Asia/Shanghai] Concept 5 progress: learner correctly answered nested section sizes as `2, 2, 1`, explaining the tree-shaped execution model.
- [2026-07-01 00:00 Asia/Shanghai] Practice completed for concept 5: learner placed `Stack<int> stack` in shared setup, used sibling sections for empty and pushed states, and nested a pop path under the pushed state.
- [2026-07-01 00:00 Asia/Shanghai] Concept 5 mastered. Concept 6 started.
- [2026-07-01 00:00 Asia/Shanghai] Concept 6 progress: learner correctly identified that filter `[json]` runs tests tagged `[json]`, selecting tests 1 and 3.
- [2026-07-01 00:00 Asia/Shanghai] Concept 6 progress: learner correctly identified that filter `[parser][json]` selects only tests that have both tags, selecting test 1.
- [2026-07-01 00:00 Asia/Shanghai] Concept 6 progress: learner correctly identified that filter `[parser],[writer]` selects the union of parser and writer tests, selecting tests 1, 2, and 3.
- [2026-07-01 00:00 Asia/Shanghai] Concept 6 progress: learner correctly identified that `[json]~[writer]` selects json tests and excludes writer tests, leaving test 1.
