# MiniF2F Acorn Formalization Progress

## 2026-05-23

- Considered MiniF2F Lean source `miniF2F/lean/src/valid.lean`.
- Added initial Acorn MiniF2F file `acornlib/src/minif2f/valid/algebra.ac`.
- Translated `mathd_algebra_462`, a rational arithmetic identity from the valid split.
- Verification status: `./acorn-0.1.84-linux-x64 verify --lib ./acornlib src/minif2f/valid/algebra.ac --timeout 20 --fail-fast` succeeded.
- Added compact agent guidance in top-level `AGENTS.md` and updated `acornlib/AGENTS.md` so future work uses the local Acorn verifier and records MiniF2F translation progress here.
- Considered valid-split problem `amc12a_2009_p2` from `miniF2F/lean/src/valid.lean`.
- Translated and proved `amc12a_2009_p2` in `acornlib/src/minif2f/valid/algebra.ac` as a rational continued-fraction identity.
- Added nearby rational helper lemmas for `1 + 1/2`, the reciprocal of `3/2`, `1 + 2/3`, and `5/3` in reduced form.
- Verification status: `./acorn-0.1.84-linux-x64 verify --lib ./acornlib src/minif2f/valid/algebra.ac --timeout 20 --fail-fast` succeeded.
- Strict replay status: `./acorn-0.1.84-linux-x64 check --lib ./acornlib --strict src/minif2f/valid/algebra.ac` succeeded with `0 searches performed`.
- Attempted valid-split problem `mathd_numbertheory_81`; proof search could not verify the decimal arithmetic bridge `Nat.23 * Nat.3 + Nat.2 = Nat.71`, so the unverified source file was removed rather than leaving a failing theorem under `acornlib/src`.
- Attempted valid-split problem `mathd_algebra_190`; a direct Real translation using `from_nat[Real]` timed out, so it was not kept in `acornlib/src`.
- Considered valid-split problem `mathd_algebra_182` from `miniF2F/lean/src/valid.lean`.
- Translated and proved `mathd_algebra_182` in `acornlib/src/minif2f/valid/algebra.ac` over `Complex`, using `from_nat[Complex]` and existing small Nat multiplication facts.
- Verification status: `./acorn-0.1.84-linux-x64 verify --lib ./acornlib src/minif2f/valid/algebra.ac --timeout 20 --fail-fast` succeeded.
- Strict replay status: `./acorn-0.1.84-linux-x64 check --lib ./acornlib --strict src/minif2f/valid/algebra.ac` succeeded with `0 searches performed`.
- Considered valid-split problem `algebra_2rootspoly_apatapbeq2asqp2ab` from `miniF2F/lean/src/valid.lean`.
- Translated and proved `algebra_2rootspoly_apatapbeq2asqp2ab` in `acornlib/src/minif2f/valid/algebra.ac` over `Complex`, writing `a^2` as `a * a` and expanding `2 * x` through `from_nat[Complex](Nat.2)`.
- Verification status: `./acorn-0.1.84-linux-x64 verify --lib ./acornlib src/minif2f/valid/algebra.ac --timeout 20 --fail-fast` succeeded.
- Strict replay status: `./acorn-0.1.84-linux-x64 check --lib ./acornlib --strict src/minif2f/valid/algebra.ac` succeeded with `0 searches performed`.
- Attempted valid-split problem `algebra_manipexpr_2erprsqpesqeqnrpnesq`; the direct Complex translation timed out on negated-product normalization (`-r * -r = r * r`), so the unverified theorem was removed from `acornlib/src`.
- Considered test-split problem `mathd_algebra_171` from `miniF2F/lean/src/test.lean`.
- Added initial test-split Acorn file `acornlib/src/minif2f/test/algebra.ac`.
- Translated and proved `mathd_algebra_171` over `Real`, using `from_nat[Real]`, `from_nat_add`, and the existing `five_plus_four` Nat arithmetic fact.
- Verification status: `./acorn-0.1.84-linux-x64 verify --lib ./acornlib src/minif2f/test/algebra.ac --timeout 20 --fail-fast` succeeded.
- Strict replay status: `./acorn-0.1.84-linux-x64 check --lib ./acornlib --strict src/minif2f/test/algebra.ac` succeeded with `0 searches performed`.
- Final stop check requested by the user: all newly written MiniF2F Acorn files verified successfully.
- Final verification commands: `./acorn-0.1.84-linux-x64 verify --lib ./acornlib src/minif2f/valid/algebra.ac --timeout 20 --fail-fast` and `./acorn-0.1.84-linux-x64 verify --lib ./acornlib src/minif2f/test/algebra.ac --timeout 20 --fail-fast` both succeeded from cache with `0 searches performed`.
- Final strict replay commands: `./acorn-0.1.84-linux-x64 check --lib ./acornlib --strict src/minif2f/valid/algebra.ac` and `./acorn-0.1.84-linux-x64 check --lib ./acornlib --strict src/minif2f/test/algebra.ac` both succeeded with `0 searches performed`.

## 2026-05-24

- Kept this progress log under `acornlib/projects/minif2f/progress.md` for benchmark tracking.
- The MiniF2F Acorn translations live in reusable source modules under `acornlib/src/minif2f/`.
- Removed committed project sidecar certificates; generated verifier artifacts are not part of the benchmark source tree.
- Current focused verification commands: `./acorn-0.1.84-linux-x64 verify --lib ./acornlib src/minif2f/valid/algebra.ac --timeout 20 --fail-fast` and `./acorn-0.1.84-linux-x64 verify --lib ./acornlib src/minif2f/test/algebra.ac --timeout 20 --fail-fast`.

## 2026-05-27

- Considered MiniF2F inequality problems from `miniF2F/lean/src/valid.lean` and `miniF2F/lean/src/test.lean`.
- Added `acornlib/projects/minif2f/valid/inequalities.ac` with valid-split problem `algebra_sqineq_2at2pclta2c2p41pc`.
- Proved it by reducing to the existing doubled-product bound `double_mul_le_square_sum(a, 2 + c)` and then expanding `(2 + c)^2` into the MiniF2F target form.
- Added `acornlib/projects/minif2f/test/inequalities.ac` with test-split problem `algebra_sqineq_at2malt1`.
- Proved it from `double_mul_le_square_sum(a, 1)`, converting `2a <= a^2 + 1` into `a(2-a) <= 1` by ordered addition and distributivity.
- Attempted valid-split problem `amc12a_2021_p7`; the natural proof reduces to `((xy)-1)^2 + (x+y)^2 - 1 = (xy)^2 + x^2 + y^2`, but the pure additive cancellation step timed out, so no failing theorem was kept.
- Verification status: `./acorn-0.1.84-linux-x64 verify --lib ./acornlib projects/minif2f/valid/inequalities.ac --timeout 20 --fail-fast` succeeded.
- Verification status: `./acorn-0.1.84-linux-x64 verify --lib ./acornlib projects/minif2f/test/inequalities.ac --timeout 20 --fail-fast` succeeded.

## 2026-05-27

- Created MiniF2F project number theory files `acornlib/projects/minif2f/valid/number_theory.ac` and `acornlib/projects/minif2f/test/number_theory.ac`.
- Translated and proved valid-split problem `mathd_numbertheory_301`, using `mod_add_mul` and a local `nine_mod_seven` helper.
- Translated and proved valid-split problem `mathd_numbertheory_458`, using the quotient-remainder form from `add_mod` and a local `seven_mod_four` helper.
- Translated and proved test-split problem `mathd_numbertheory_342`, using the existing `nat_mul_9_6` arithmetic fact and `mod_mul`.
- library-needed: Attempted valid-split problem `mathd_numbertheory_81` (`71 % 3 = 2`); direct proof search still times out on the Nat arithmetic/mod bridge, specifically the quotient-remainder arithmetic around `Nat.23 * Nat.3 + Nat.2 = Nat.71`, so no theorem was kept.
- Failed/not kept: Attempted test-split problem `mathd_numbertheory_247`; the premise `(3 * n) % 2 = 11` is contradictory, and Acorn verifier reports `prover found inconsistent assumptions` rather than accepting the vacuous implication.
- Verification status: `./acorn-0.1.84-linux-x64 verify --lib ./acornlib projects/minif2f/valid/number_theory.ac --timeout 20 --fail-fast` succeeded.
- Verification status: `./acorn-0.1.84-linux-x64 verify --lib ./acornlib projects/minif2f/test/number_theory.ac --timeout 20 --fail-fast` succeeded.

## 2026-05-27 Algebra

- domain=algebra status=proved split=test theorem=`mathd_algebra_176` path=`acornlib/projects/minif2f/test/algebra.ac`; translated powers explicitly as multiplication and proved the polynomial identity over `Real`.
- domain=algebra status=proved split=test theorem=`mathd_algebra_346` path=`acornlib/projects/minif2f/test/algebra.ac`; translated the two function hypotheses as a pointwise conjunction and proved the composition value.
- domain=algebra status=proved split=test theorem=`mathd_algebra_432` path=`acornlib/projects/minif2f/test/algebra.ac`; proved the binomial product identity using distributivity and additive cancellation.
- domain=algebra status=proved split=test theorem=`mathd_algebra_143` path=`acornlib/projects/minif2f/test/algebra.ac`; translated the two function hypotheses as a pointwise conjunction and proved the composition value.
- domain=algebra status=blocked/not-kept split=test theorem=`mathd_algebra_419`; a direct Real constant-normalization proof timed out, so no failing theorem was kept.
- domain=algebra status=blocked/not-kept split=test theorem=`mathd_algebra_478`; direct Real division normalization timed out, so no failing theorem was kept.
- Added reusable library lemma `sub_add_sub_cancel` to `acornlib/src/add_group.ac` for `(a - b) + (b - c) = a - c` in additive groups.
- Verification status: `./acorn-0.1.84-linux-x64 verify --lib ./acornlib projects/minif2f/test/algebra.ac --timeout 20 --fail-fast` succeeded.
- Verification status: `./acorn-0.1.84-linux-x64 verify --lib ./acornlib src/add_group.ac --timeout 20 --fail-fast` succeeded.
- Strict replay status: `./acorn-0.1.84-linux-x64 check --lib ./acornlib --strict src/add_group.ac` succeeded with `0 searches performed`.
- Copied the verified test algebra project file to `acornlib/projects/minif2f/valid/algebra.ac` as requested, so the valid directory now has a matching algebra project file and sidecar certificate.
- Verification status: `./acorn-0.1.84-linux-x64 verify --lib ./acornlib projects/minif2f/valid/algebra.ac --timeout 20 --fail-fast` succeeded and generated `acornlib/projects/minif2f/valid/algebra.jsonl`.
