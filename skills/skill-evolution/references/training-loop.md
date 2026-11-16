# Training Loop — rollout → reflect → aggregate → select → update → evaluate

A skill is trained the way a neural network is trained — except the weights are words. The skill document is the trainable state; the model is frozen. One epoch is one pass through the loop below. Run it until validation stops improving, then stop.

## The six stages
1. **Rollout.** The target agent executes tasks with the current skill. Collect trajectories (what it did, what it said, what the judge scored). No editing here — only observation.
2. **Reflect.** A separate optimizer model reads the scored rollouts and proposes edit patches — what to add, delete, or replace in the skill. It does not rewrite the whole skill; it proposes bounded patches.
3. **Aggregate.** Merge the patches from many rollouts into one candidate edit set. Duplicates collapse. Contradictory patches are resolved (the one backed by more evidence wins); if they truly conflict, keep neither.
4. **Select.** Rank the patches and clip to the learning-rate budget (see `references/edit-budget.md`). The learning rate is a max-edit count, not a feeling. Over-budget patches wait for the next epoch.
5. **Update.** Apply the selected patches to the skill document. One update per epoch, not a patch per rollout.
6. **Evaluate (gate).** Score the updated skill on the held-out validation split. The candidate ships only if it strictly improves validation (see `references/validation-gate.md`). Otherwise the epoch is discarded and the rejected edits go to the buffer.

## Epochs
- **Multi-epoch.** Repeat the loop. Each epoch starts from the best skill so far, never from a rejected candidate.
- **Epoch boundary: slow update + meta skill.** At the end of an epoch, a slow update consolidates what the epoch learned, and a meta-skill memory records what worked (which kinds of edits helped, which didn't). The next epoch starts smarter.
- **Stop rule.** When validation stops improving for two consecutive epochs, stop. More epochs after that is overfitting to the validation split.

## The deep-learning analogy (use it to reason, not to impress)
| Deep learning | Skill training |
|---|---|
| Model weights | Skill document (Markdown) |
| Forward pass | Rollout (target executes tasks) |
| Loss / gradient | Reflect (optimizer produces edit patches) |
| Gradient clipping | Edit selection (learning rate = max edits) |
| SGD step | Patch application to the skill |
| Validation set | Gated evaluation on the held-out split |
| LR schedule | cosine / linear / constant |
| Epochs | Multi-epoch with slow update + meta skill |

## Roles (keep them separate)
- **Target.** Executes tasks with the skill. Never proposes edits to its own skill.
- **Optimizer.** Reads rollouts, proposes patches. Never executes tasks, never scores itself.
- **Verifier.** Runs the gate on held-out validation. Never proposes edits. The optimizer's work is judged by the verifier, never by the optimizer.

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | Baseline measured before training starts | Training with no "before" number |
| 2 | Every stage runs, in order, every epoch | A stage skipped (e.g. update without a gate) |
| 3 | One update per epoch, from the best skill so far | Patching after every rollout |
| 4 | Optimizer, target, and verifier are separate | The same agent proposing and verifying its own edits |
| 5 | Slow update + meta skill run at every epoch boundary | Epochs that don't consolidate |
| 6 | Stop rule honored (2 flat epochs = stop) | Training until the validation split is memorized |
