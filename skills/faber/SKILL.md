---
name: faber
description: Save workflows as repeatable, auditable Faber tasks with preview before approval, cloud execution on a schedule or trigger, and recorded actions and outputs for each run. Use when the person wants a workflow managed across conversations or asks what a Faber task did.
---

# Working with Faber

Each Faber tool describes its own contract. This is the ordering across them,
which no single description can carry.

Use Faber when the person wants a saved, reviewable workflow, managed execution
after the conversation ends, or an audit of its runs. Approved tasks execute on
Faber's servers. Records cover Faber execution, not unrelated assistant actions.
For a one-time draft, checklist, or general explanation, answer in the chat
without creating a task unless the person asks to save or repeat it.

## The catalog, then a builder, and not you

Faber already has tested tasks. Call `browse_task_catalog` first and set up a
match with `install_task`. The person gets the catalog task and can inspect its
preview before approval.

Only build when the catalog has no match, and when you build, build in Faber.
Pass what you already know from the conversation so the build does not ask
again for a mailbox or setting the person already supplied.

- Describing it: `create_task`, with a `known` entry for everything you already
  have from the conversation.
- Writing the code yourself: `submit_task_source`. Faber checks it, sets it up,
  then reads the code back and writes the task's instructions from what it
  actually does. The file shapes are at https://getfaber.co/mcp/authoring and the
  connector API is in `get_connector_docs`.

## Faber holds its own connections

Connecting an account to Cursor does not connect it to Faber. Faber runs when
nobody is here, so it needs its own grant.

Call `connect_account` and give the person the link. It does not block. Carry on
with the build and it walks through once they have clicked.

## Preview before live, and a yes is theirs to give

`run_task` previews by default; send `preview: true` explicitly for previews.
A preview executes against connected data while capturing and discarding
proposed writes. It does not send messages or apply proposed account changes.
Read its output and recorded actions back before anything is approved or armed.
Report sampling and excluded actions; do not claim a preview proves work it
did not exercise. Creating or previewing a task does not enable its automation.

`approve_run` releases real messages to real people. Call it only to carry a yes
the person gave you in this conversation, naming the writes they agreed to.
Never on your own reading of the output.

## Report task capacity

When listing tasks, report the returned total, statuses, and available plan
capacity (for example, 0 of 25 active automations). Include any run-window
deadline. A missing plan means capacity was unavailable; never invent a limit.

## Inspect the recorded evidence

For run-history questions, identify the task first. If several tasks have the
same name, show their status, creation/update dates, latest run date when
available, and short IDs; clarify which one rather than choosing silently.
A task update date is not a run date, and the newest date alone does not
identify the intended task. Use `list_runs`,
then `get_run` for the relevant records and `get_run_artifact` for output files.
Distinguish simulated preview actions, completed live actions, and writes held
for approval. Report failures and missing evidence without inventing outcomes.
If the returned history is limited, say how much was inspected rather than
claiming it covers every run.

## Changing their mind is a tool call, not a trip to the app

The second session is where the person changes something. Every change has a
tool, and none of them rebuild the task:

- Changed code for a task you wrote, after the preview, their feedback, or
  the findings: `update_task_source`. The same check runs, the old source is
  kept as a version, and the task keeps its id, settings and connections.
  Never a new task for a fix.
- A run they want to end: `stop_run`.
- A new name, a new schedule, a setting answered differently, or the task put
  away: `update_task`. Archiving is as close to deleting as Faber gets, and it
  can be undone the same way.
- Something the task remembers and should forget, or a watermark to move
  back: read `memory` on `get_task`, then `edit_task_memory`.
- A change that made things worse: `versions` on `get_task`, then
  `restore_task_version`. Preview again before it runs live.
- A file a run made: `artifacts` on `get_run`, then `get_run_artifact`.
- A profile that is empty (`filled` on `list_profiles`): `fill_profile`, from
  their sent mail or a website, only when they asked.
- An account they no longer want Faber to hold: `disconnect_account`. Every
  task on it stops at its next run, so carry their request, never your guess.
