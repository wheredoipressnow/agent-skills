# In-house Elixir documentation style

These rules apply to proprietary application code, not to publishable
libraries. They sit alongside the shared rules in SKILL.md. Where this
file and the shared rules conflict, ask before proceeding.

## Audience

The reader is an internal developer with full access to the source and
more familiarity with the system than an outside consumer. Docs pulled
through tooling are a quick reference, not a tutorial. Write for someone
who can and will read the code.

## What to write

- Summarize what the function does.
- Document peculiarities: edge cases, side effects, ordering guarantees,
  nil and error handling, anything a reader would not expect from the
  signature alone.

## What to leave out

- No superfluous commentary.
- Do not restate what the function or variable names already make clear.
- No examples on internal functions. If one seems truly necessary, ask
  first.
- No marketing language, no filler.

## Form

- Simple English.
- Professional and friendly tone.
- Concise.
- No em-dashes.
- No lists with bold-label items.

## Typespecs

- `@spec` is allowed where it adds value to the contract.
- Omit `@spec` where it would add nothing.
- Never put `@spec` on `defp`.

## (Extend as needed)

Add team-specific conventions here, for example terminology, required
sections in `@moduledoc`, or how to reference internal modules.
