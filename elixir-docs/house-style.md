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
- Keep peculiarities caller-actionable. Document what the caller must
  handle (return shape, what raises, side effects on disk or state), not
  how the function works internally. The reader has the code for the how.

## What to leave out

- No superfluous commentary.
- Do not restate what the function or variable names already make clear.
- No examples on internal functions. If one seems truly necessary, ask
  first.
- No marketing language, no filler.
- No provenance or lineage notes. Do not write "port of X", "mirrors
  `foo.ts`", "based on", or cross-repo file paths. They carry no value to
  a reader and rot when the source moves or disappears.

## Auditing existing docs

- Bias toward cutting. When the code is already documented, look first
  for text to delete, not text to add.
- Prefer the shortest doc that still names the surprising behavior. When
  in doubt, cut.

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
