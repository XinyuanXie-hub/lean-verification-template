# Lean verification

## 1. Write the challenge and ask for review

If the paper and the theorem to formalize have not been supplied, ask the user for them. Translate the theorem as stated in the paper into `Challenge.lean`, with only the definitions it depends on. Keep the file clean and concise, and use `sorry` for the theorem proofs. List the fully qualified theorem names in `comparator.json`.

Ask the user to check that the definitions and statements are correct. Where useful, propose equivalent, simpler definitions or statements to make the challenge easier to read. Wait for explicit approval before starting the proof; leave `Solution.lean` empty until then.

## 2. Find the solution

After approval, keep `Challenge.lean` and the approved comparator targets unchanged, and dedicate the work to finding the proof in `Solution.lean`.

Use the papers, divide and conquer, and parallel agents where useful. Split the proof into small pieces. Expand compressed mathematical arguments into detailed subproofs, then translate them into Lean; for easier tasks, do both together or translate directly into Lean. Mathematical simplification needed to find the initial proof does not require another approval.

Use ordinary Lean compilation for local tests. Use the same fully qualified theorem names in both modules, and do not import `Challenge` into `Solution`. Run the full comparator with Lean, NanoDa, and con-ron for final verification. Do not weaken its checks or leave `sorry` or extra axioms in the completed solution.

## 3. Offer simplification after verification

After the proof passes final verification, ask whether the user wants it simplified. If so, start at the root of the proof and work iteratively through the subsequent levels. Simplify the mathematics first and formalize the changes in parallel, or simplify directly in Lean where feasible. Keep the approved challenge unchanged and run the full comparator again after the changes.

## Commands

With the pinned Lean toolchain installed, run these commands from the project root:

```sh
lake exe cache get
lake build Challenge
lake build Solution
bash scripts/verify-comparator.sh
```

Compilation alone does not establish that the solution matches the challenge. The final script also requests the dependency cache before running comparator. Final verification requires Linux, Python 3, bubblewrap, and working sandbox user namespaces.

## GitHub configuration

The repository name used here is `lean-verification-template`. Before publishing under another owner or project name, replace:

- `XinyuanXie-hub/lean-verification-template` in `.github/workflows/lean.yml` and `site/latest-run/index.html` with the actual `OWNER/REPOSITORY`. In the HTML file, update the link, API URL, and run-URL regular expression.
- `https://xinyuanxie-hub.github.io/lean-verification-template/latest-run/` in the workflow with the actual Pages URL.

The workflow runs the full comparator on branch pushes, pull requests, and manual runs. Both Lean files start empty and `theorem_names` starts as `[]`, so verification fails until the project-specific challenge, targets, and proof are filled.

The workflow also deploys the included `site/` files on pushes or manual runs on `main` in the named repository. Enable GitHub Pages with GitHub Actions as its source and allow the required Pages permissions. The Pages job runs independently of comparator; its latest-run link points to the newest run, not necessarily a successful one. If the repository condition is not updated, that job is skipped.

The script, workflow, and Pages files are adapted from [König constant](https://github.com/XinyuanXie-hub/Konig-constant/tree/165a31717d8084e6df9a7c8f745059af0e2ed40a), under the included Apache-2.0 license.
