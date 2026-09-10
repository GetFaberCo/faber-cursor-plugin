# Faber

Faber runs automations on a schedule or a trigger, when nobody is in the chat.

Install this plugin and your assistant can set one up from work it just did with
you. It has the real mail, the real sheet and the way you write in front of it,
which is a better description of the task than anything you would type into a
setup form. Faber adds the part a chat cannot do: running on Monday.

## Installing

Install from the Cursor marketplace, or add the repository directly. There is
no API token to paste and nothing to configure. The first tool call opens a
consent screen where you sign in to Faber and approve what the assistant may
do.

You need a Faber account for most of it. One tool, the task catalog, answers
before you have one.

## Three things to say, once it is connected

- **"What can Faber already do about invoices?"** Answers from the real catalog,
  and works before you have an account.
- **"That reply you just drafted, I write one like it every morning. Set it up in
  Faber to run at 8am and show me a preview."** Sets the task up and shows you a
  preview run.
- **"What is waiting on me in Faber?"** Reads back anything a run is holding for
  your approval.

## Approvals

A preview run discards every write, so you see what a task would do before
anything happens. When a live run reaches something you flagged, it stops and
holds it. Your assistant may only pass on a yes you gave it in the conversation.
Every approval and arming records which assistant carried it.

## Links

- [How Faber works in an assistant](https://getfaber.co/mcp)
- [Writing a task's code yourself](https://getfaber.co/mcp/authoring)

## License

MIT. This repository holds the plugin manifest only; Faber itself is a hosted
service and no product source is here.
