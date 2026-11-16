# Edit Budget — textual learning rate

In deep learning, the learning rate bounds how much the weights move per step. In skill training, the learning rate bounds how much the words move per epoch. Same idea, same discipline: too big and the skill thrashes; too small and it never improves.

## The rules
- **Learning rate = max edits per update.** A number, set before training starts (e.g. 5 edits per epoch). The optimizer may propose more; only the top N (by evidence) are applied. The rest wait.
- **Bounded edits only.** Every edit is one of three operations: **add** (new rule / example), **delete** (remove a rule / example), **replace** (rewrite a rule / example). No full rewrites. A patch that rewrites the whole skill is not an edit — it's a new skill, and it goes through the full loop as one.
- **LR schedule.** The budget changes over epochs, on a schedule set before training:
  - **Cosine:** starts high, decays smoothly — big moves early, fine-tuning late.
  - **Linear:** decays evenly.
  - **Constant:** same budget every epoch — simplest, use it unless you have a reason not to.
- **Slow update at the epoch boundary.** After the gate accepts an epoch, a slow update consolidates: it merges the epoch's accepted edits into the skill's stable form and updates the meta-skill memory (which edit kinds helped, which didn't). The next epoch starts from the consolidated skill, not from a pile of patches.
- **Meta skill.** A short memory of what works for this skill: "adding examples helped twice, deleting rules hurt once". The optimizer reads it before proposing patches. It is updated only at epoch boundaries, never mid-epoch.
- **Zero inference-time cost at deploy.** The trained artifact is a compact skill document (typically 300–2,000 tokens). It runs against the unchanged target model with no extra model calls. If your "improved" skill needs a second model call at runtime, it isn't an improvement — it's a different system.

## Sizing the budget
- **Too big:** the skill changes so much per epoch that you can't tell which edit helped. Validation swings wildly. Cut the budget in half.
- **Too small:** validation creeps up by nothing for epochs. Double it (once), and check the stop rule — the skill may already be at its ceiling.
- **Default when unsure:** 5 edits per epoch, constant schedule. Adjust from evidence, not from a guess.

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | Learning rate set as a number before training | A budget decided mid-epoch, or no budget at all |
| 2 | Every edit is add / delete / replace (bounded) | A full rewrite passed off as an edit |
| 3 | LR schedule chosen before training (cosine / linear / constant) | Schedule changed to fit the result |
| 4 | Slow update + meta skill run at every epoch boundary | Epochs that don't consolidate |
| 5 | Deployed artifact is a compact skill doc, no extra runtime calls | An "improvement" that needs a second model at runtime |
| 6 | Budget sized from evidence (too big = thrash, too small = flat) | A budget that never changes despite flat or wild validation |
