---
name: elixir-docs
description: >
  Augment, audit, and revise Elixir documentation (@moduledoc, @doc,
  @typedoc, and @spec). Use when asked to add missing docs, review or
  improve existing docs, or check documentation quality in an Elixir
  project. Distinguishes between publishable libraries and proprietary
  applications and applies the correct ruleset to each.
---

# Elixir documentation skill

This skill helps add and improve documentation in Elixir code. It works
through findings one at a time and asks for approval before changing
anything. It never invents intent: when the purpose of a function is not
clear from the code and its surrounding context, it stops and asks.

## Step 1: Determine the project type

Read `mix.exs` before doing anything else.

Treat the project as a publishable LIBRARY when `project/0` defines a
`package` key, or otherwise shows clear signs of being published (for
example a `description` paired with package metadata, or a `source_url`
and hex-style config). Otherwise treat it as an APPLICATION (proprietary
or closed source).

Print the conclusion and the evidence before continuing, for example:

  Project type: LIBRARY
  Evidence: mix.exs defines a `package` block with `licenses` and `links`.

  Project type: APPLICATION
  Evidence: mix.exs has no `package` block; no publish metadata found.

The user can override this conclusion. Wait for confirmation if the
signal is weak or mixed.

## Step 2: Load the right ruleset

Shared rules apply to both project types. Then apply the type-specific
rules below.

For APPLICATION projects, also read `house-style.md` from this skill
folder and follow it. If `house-style.md` and the shared rules ever
conflict, ask the user which wins rather than guessing.

## Shared rules (both project types)

- Make no assumptions. If a function's purpose is not clear from its
  code and surrounding context, stop and ask the user, then continue.
- Use simple English. Keep a professional and friendly tone.
- Be concise. No verbose or marketing language.
- Do not use em-dashes.
- Do not use lists whose items begin with bold labels.
- Summarize what the function does, and document peculiarities
  (surprising behavior, edge cases, side effects, ordering, nil
  handling, and similar).
- Do not add superfluous commentary. If variable and function names
  already convey the meaning, do not restate it.
- Assume the reader is a developer with full access to the code who
  pulls docs through tooling (h/1, hexdocs, mix docs). Documentation
  supplements the code, it does not narrate it.
- Never attach examples to private functions (`defp`).
- Never attach `@spec` to private functions (`defp`).

## Library rules (public surface)

- Follow general Elixir community documentation norms.
- The public surface may include examples. Prefer executable doctests
  where they add value and stay readable.
- Add `@spec` to public functions where it clarifies the contract.
- Internal functions: keep documentation minimal. Do not add examples
  to internal functions unless absolutely necessary, and in that case
  check with the user first.

## Application rules (proprietary)

- Follow `house-style.md`.
- `@spec` is allowed where it adds value and may be omitted where it
  does not.
- Do not add examples to internal functions. If an example seems
  genuinely necessary for an internal function, check with the user
  first.

## Step 3: Walk through findings one at a time

Audit and revise both proceed function by function (and module by
module for `@moduledoc`).

For each finding:

1. Show the location (module and function or arity).
2. State the issue (missing docs, weak summary, undocumented
   peculiarity, missing or misleading `@spec`, stale example, and so
   on).
3. Show the proposed change.
4. Wait for approval before editing. Apply the change only after the
   user approves.

When purpose is unclear, pause and ask in the same pass, then continue
once answered.

## Step 4: Validate

After edits are applied, offer to run `mix test`. This catches broken
doctests and confirms examples still hold. Do not run it without
asking.
