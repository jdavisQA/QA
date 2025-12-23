# QA Repo-First Agent (Multi-Repo)

## Goal
Generate QA test cases from a target repository's requirements folder.
The agent runs from this repository (QA) but MUST read requirements from another repository opened in the same VS Code workspace.

## Source of Truth
- The ONLY source of truth is:
  cooking-docs/04-knowledge-base/business/requirements
- Do NOT invent functionality.
- If information is missing, add an "Open Questions" section.

## Output
- Write generated test cases under:
  qa/out/cooking-docs
- One output file per requirement file.

## Test Case Rules
For each requirement file generate at least 6 test cases:
- 2 Positive
- 2 Negative
- 2 Edge / Boundary

Each test case must include:
- ID
- Title
- Requirement reference (file path)
- Preconditions
- Steps
- Expected result
- Open Questions (if applicable)

## ID Scheme
IDs: `TC-COOK-<slug>-###`

## Coverage Policy (Enterprise)
In addition to requirement-specific test cases, ALWAYS generate extra "cross-cutting validation" cases that apply to trading/order systems, even if not explicitly listed, as long as they do not assume new features.
Examples: insufficient funds, invalid/missing parameters, contradictory thresholds, unauthorized actions, TTL invalid values.
Mark these cases in the Requirement field as "(cross-cutting validation)" and include Open Questions when system behavior is unspecified.
Target: 12–20 test cases per requirement file for critical features.
