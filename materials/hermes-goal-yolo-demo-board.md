# Hermes Goal and YOLO Demo Board

## Goal

Teach learners how to use `/goal` and `/yolo` as advanced Hermes Agent controls without treating autonomy as permission to ignore safety boundaries.

## Advanced Workflow

```text
Readiness check
-> goal contract
-> controlled /goal run
-> goal debug review
-> yolo risk classification
-> yolo toggle demo
-> combined scenario design
-> optional combined execution
-> safety gate
```

## Current State

- Learners should already be comfortable with normal Hermes chat.
- Learners should understand tool inspection and human approval.
- `/goal` should be introduced before `/yolo`.
- `/yolo` should be demonstrated only in a disposable or tightly constrained environment.
- Combining `/goal` and `/yolo` is optional and should require an explicit Go decision.

## Acceptance Criteria

- The learner can explain what `/goal` changes.
- The learner can write a goal with scope, verification, and stop conditions.
- The learner can use `/goal status`, `/goal pause`, `/goal resume`, and `/goal clear`.
- The learner can explain what `/yolo` bypasses.
- The learner can name at least three cases where `/yolo` is forbidden.
- The learner can design a safe combined `/goal` + `/yolo` lab.
- The workflow ends with a documented Go/No-Go decision.

## Command Focus

| Command | What it teaches | Main risk |
| --- | --- | --- |
| `/goal <text>` | Persistent objective across turns | vague goals cause runaway or wrong completion |
| `/goal status` | Inspect current objective and progress | false confidence if status is not reviewed |
| `/goal pause` | Stop auto-continuation without deleting the goal | paused goals may be forgotten |
| `/goal resume` | Continue the goal loop | continuing without fixing the goal text |
| `/goal clear` | Remove the standing goal | clearing before recording lessons learned |
| `/yolo` | Toggle dangerous command approval bypass | commands run without normal approval prompts |
| `hermes --yolo` | Start a session with approval bypass enabled | unsafe default for real workspaces |

## Goal Contract Template

```text
Outcome:
Scope:
Allowed tools:
Forbidden actions:
Verification:
Stop condition:
Rollback:
```

## YOLO Decision Template

```text
Task:
Environment:
Is it disposable?
Are secrets present?
Could commands affect external systems?
Is rollback available?
Is /yolo needed, or only convenient?
Decision: Go / Go only in sandbox / No-Go
```

## Risk Ladder

| Level | Pattern | Recommendation |
| --- | --- | --- |
| 1 | `/goal` with read-only task | good classroom demo |
| 2 | `/goal` with Markdown edits and git diff review | acceptable with clear scope |
| 3 | `/yolo` with read-only commands | demo only, toggle off immediately |
| 4 | `/goal` + `/yolo` in disposable worktree | advanced lab with rollback |
| 5 | `/goal` + `/yolo` in production or secret-bearing workspace | forbidden |

## Demo Checklist

- [ ] Learners completed the base Day 2 workflow.
- [ ] Current workspace classified as disposable or not disposable.
- [ ] Git status or equivalent rollback context reviewed.
- [ ] Goal contract written before `/goal`.
- [ ] `/goal status` checked during the run.
- [ ] `/goal pause` demonstrated.
- [ ] `/goal clear` demonstrated or explained.
- [ ] `/yolo` risk classifier completed before toggling.
- [ ] `/yolo` toggle demo ended with YOLO off.
- [ ] Combined scenario has explicit Go/No-Go.
- [ ] Final diff or output is reviewable.
- [ ] Rollback or cleanup path is known.

## Safety Notes

Use these questions during discussion:

1. Does the goal define done clearly?
2. What happens if the judge says done too early?
3. What happens if the judge keeps continuing?
4. Which approval prompts does `/yolo` remove?
5. What remains blocked even in YOLO mode?
6. Is the workspace disposable?
7. Are secrets, credentials, or production files reachable?
8. What evidence proves the result is correct?
9. How do we stop the loop?
10. How do we undo the changes?

## Final Review Questions

Ask learners:

1. When is `/goal` better than a normal prompt?
2. What makes a goal safe enough to run?
3. Why is `/yolo` different from trusting the agent?
4. What would make `/goal` + `/yolo` unacceptable?
5. What policy should your team use before enabling autonomous loops?
