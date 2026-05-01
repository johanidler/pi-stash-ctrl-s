# pi-stash-ctrl-s

## Quick handoff

**For humans:** if you want to use this, pass this to your Pi agent:

```text
Install git:github.com/johanidler/pi-stash-ctrl-s and set my Pi keybindings to:
{
  "pi-stash.shortcut": ["ctrl+s"],
  "app.session.toggleSort": ["alt+s"],
  "app.models.save": ["shift+ctrl+s"]
}
Then run /reload.
```

**If you are a Pi agent:** install it by doing this:

```bash
pi install git:github.com/johanidler/pi-stash-ctrl-s
```

Then make sure `~/.pi/agent/keybindings.json` contains:

```json
{
  "pi-stash.shortcut": ["ctrl+s"],
  "app.session.toggleSort": ["alt+s"],
  "app.models.save": ["shift+ctrl+s"]
}
```

Then run `/reload`.

> This extension makes `Ctrl+S` stash your current Pi prompt, and you should also rebind Pi's conflicting built-ins like this:
>
> ```json
> {
>   "pi-stash.shortcut": ["ctrl+s"],
>   "app.session.toggleSort": ["alt+s"],
>   "app.models.save": ["shift+ctrl+s"]
> }
> ```

A small [Pi](https://github.com/badlogic/pi-mono) extension package that lets you quickly stash the current editor draft with `Ctrl+S`, send another prompt, and automatically get the stashed draft restored right after that prompt is submitted.

## What it does

When you press `Ctrl+S`, this extension:

1. saves the current editor draft to `.pi/stash.md`
2. clears the editor
3. waits for your next prompt submission
4. restores the stashed draft into the editor right after that prompt is sent

If the editor is empty, pressing `Ctrl+S` restores the pending stash immediately.

## Why the extra keybindings?

Pi already uses `Ctrl+S` for built-in actions in some views, so if you want stash-on-`Ctrl+S` cleanly, rebind those built-ins too:

- `app.session.toggleSort` → `Alt+S`
- `app.models.save` → `Shift+Ctrl+S`

This package defaults the stash shortcut to `Ctrl+S`, while the README shows the companion keybindings you should set in `~/.pi/agent/keybindings.json`.

## Install

### From GitHub

```bash
pi install git:github.com/johanidler/pi-stash-ctrl-s
```

### Keybindings

Create or edit `~/.pi/agent/keybindings.json`:

```json
{
  "pi-stash.shortcut": ["ctrl+s"],
  "app.session.toggleSort": ["alt+s"],
  "app.models.save": ["shift+ctrl+s"]
}
```

Then run:

```text
/reload
```

## Files

- extension entry: `src/stash.ts`
- stash file: `.pi/stash.md`

## Credit

Based on the original `pi-stash` package by Max Petretta, adapted here with a `Ctrl+S`-first workflow.

## License

MIT
