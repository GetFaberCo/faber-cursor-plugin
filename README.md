# Faber

Make AI work repeatable and auditable. Turn a workflow from your conversation
into a saved Faber task with a reviewable specification, a preview before
approval, and recorded actions and outputs each time it runs.

Use Faber when you want an external service to manage the approved workflow,
its connected accounts, and its run history across conversations. Approved
tasks run on Faber's servers on a schedule or trigger, without keeping Cursor,
Grok Bot, your chat, or your desktop app open. Come back to inspect what ran,
what it proposed or changed, and whether anything failed. These records cover
work executed by Faber; they do not audit every action your assistant takes
outside Faber.

## Installing

Add this repository directly in Cursor, or install from the marketplace once
the listing is available. Grok Bot uses Cursor's connector policy. Sign in to
Faber through OAuth when the assistant needs account-specific tools.

You need a Faber account for your tasks and run history. The task catalog works
without an account. Connect any third-party accounts the task needs within
Faber; an account connected to your assistant does not grant Faber access.

## Things to say, once it is connected

- **"What can Faber already do about invoices?"** Answers from the real catalog,
  and works before you have an account.
- **"Run this every Monday, even when I'm offline. Show me what it would do
  first, and keep a log of every run."** Use after describing the workflow.
- **"That worked. Save it so I can run it again next time."** Use after completing
  a workflow you want to repeat.
- **"Show me every time this ran, what it changed or sent, and whether anything
  failed."** Use when discussing a saved Faber task.

## Preview and approvals

A preview executes the task against connected data while capturing and
discarding proposed writes. Messages are not sent and proposed account changes
are not applied. Inspect its output and recorded actions before approving it.
A preview can sample data; skipped or excluded items limit what it demonstrates.

Creating or previewing a task does not approve it or enable its automation.
Approval of a task with a schedule or trigger enables it. Selected live writes
can have a separate approval hold. Your assistant may only pass on approval you
gave in the conversation. Every approval and arming records which assistant
carried it.

## Links

- [How Faber works in an assistant](https://getfaber.co/mcp)
- [Writing a task's code yourself](https://getfaber.co/mcp/authoring)

## License

MIT. This repository holds the plugin package only; Faber itself is a hosted
service and no product source is here.
