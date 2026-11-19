# {{PROJECT_TITLE}}

This project uses Lean to verify {{THEOREM_LABELS_AND_NUMBERS_FROM_THE_PAPERS}}.

> {{AUTHORS}}, *{{PAPER_TITLE}}*, [{{REFERENCE}}]({{PAPER_URL}}).

{{ADDITIONAL_PAPER_CITATIONS_IF_NEEDED}}

## Mathematical statements

<!-- Replace the placeholders with the papers’ original labels and numbers, wording, and mathematical notation. State only the definitions necessary to state the theorems. Use one block per theorem and identify its source when citing multiple papers. Remove this comment from the finished README. -->

{{DEFINITIONS_IN_THE_PAPERS_WORDING_AND_NOTATION}}

<a name="{{THEOREM_ANCHOR}}"></a>

**{{ORIGINAL_THEOREM_LABEL_AND_NUMBER}}.** {{ORIGINAL_THEOREM_STATEMENT}}

{{ADDITIONAL_THEOREM_BLOCKS_IF_NEEDED}}

## Verification

To verify the correctness of the {{THEOREM_OR_THEOREMS}} in Lean, one only needs to check that the {{STATEMENT_OR_STATEMENTS}} and definitions in [Challenge.lean](Challenge.lean) match {{VERIFIED_THEOREM_LINKS}} stated above, and confirm that `lake comparator` succeeds.

The results of `lake comparator` can be checked through the GitHub workflow provided by this project as follows:

1. Sign in to GitHub, open the “Actions” tab, then open the first workflow run listed there.
2. Click “Verify the Challenge against Solution”, then expand “Run Comparator with Lean, NanoDa, and con-ron”.
3. Check that the log (lines 198–203) reports acceptance by con-ron, NanoDa, and Lean, followed by `Your solution is okay!`.


Note: Here, we use the [“gold standard”](https://lean-lang.org/doc/reference/latest/ValidatingProofs/#validating-comparator) for validating proofs in Lean, and we refer readers to [“Challenges and External Checkers”](https://lean-lang.org/doc/reference/latest/Build-Tools-and-Distribution/Lake/#lake-comparator) for details on how it works.
