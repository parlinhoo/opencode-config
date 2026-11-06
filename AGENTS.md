# Global AGENTS.md — Fabián González

## About me

I'm Fabián González, a developer based in Chile.
I speak Spanish natively; talk to me in English, and write this file and code
identifiers in English.

I care about readable, reusable, maintainable, production-quality code.

## Working agreement

- **Ask before acting.** Before any file edit, show me exactly what you will change
  and wait for approval. For multi-step tasks, propose a short plan first.
- **Pre-approved commands:** read-only inspection (`ls`, `cat`, `grep`, `rg`,
  `git status/diff/log/show/blame`), builds/type-checks, existing tests, and
  read-only linters. Everything else needs approval — especially file edits,
  formatters, installs, and commands that change state.
- **Always ask when requirements are ambiguous.** Do not guess APIs, schemas,
  behavior, or intent. Stop and ask.
- **Explain your reasoning.** Lead with the answer or proposed change, then explain
  the why and tradeoffs concisely. No long preamble.
- **Stay in scope.** Touch only what the task requires. You may propose small nearby
  cleanups that directly support the change, but ask first. Never refactor unrelated
  code.
- **No silent assumptions.** If you must assume something to proceed, state it and
  get confirmation.

## Environment

- Linux, Bash (oh-my-bash), Neovim (which is also integrated in VSCode), Git with GitHub CLI.
- Node via `nvm`; Python virtualenvs under `~/proyectos/python-envs`; projects under
  `~/proyectos`.
- Git default branch is `main`.
- Use each project's existing package manager, build tool, and formatter. Do not
  switch tools or introduce a new one.

## General principles

- **Readability and reusability first.** Clear names, small functions, simple
  control flow. Prefer several simple statements over a dense one-liner. Extract
  genuinely reusable logic into well-named functions, modules, or components, but
  do not generalize prematurely or build abstractions for a single use case.
- **OOP and SOLID when they help.** Use them to improve maintainability,
  scalability, and reusability, but never at the cost of readability. Avoid
  premature abstraction, unnecessary interfaces, factories, and layers.
- **Strict typing.** Explicit types on function signatures. Avoid implicit casts and
  narrowing. Avoid `any` in TypeScript; use type hints in Python.
- **Descriptive English identifiers**, following each language's naming conventions.
- **Minimal comments in Spanish**, only for non-obvious intent, constraints, or
  tradeoffs. Never restate the code. Exported/public APIs are documented separately
  (see Documentation); private helpers stay comment-light.
- **No dead code.** Remove commented-out code and unused imports/variables rather
  than leaving them behind.
- **No placeholders.** Do not leave TODOs, stubs, or fake implementations unless I
  ask for them.
- **Never hardcode credentials or secrets.** Use environment variables or the
  project's secret-management mechanism.

## Language conventions

### C++

- C++17 or C++20 unless the project specifies otherwise.
- RAII and smart pointers (`std::unique_ptr`, `std::shared_ptr`); no manual
  `new`/`delete`.
- Prefer STL containers and algorithms over hand-written equivalents.
- Use `const` correctness, `nullptr`, scoped enums, and `[[nodiscard]]` where useful.
- Avoid `using namespace std;` in headers.
- Follow the project's header/source layout and include style.
- Document public headers, classes, and functions with concise Doxygen comments in
  Spanish.

### C

- C11 unless the project specifies otherwise.
- Check return values from I/O, allocation, and syscalls; free everything you
  allocate.
- Use fixed-width types from `<stdint.h>` for binary or systems work.
- Use error codes/return values, not exceptions.
- Avoid VLAs in portable code.
- Document public headers and functions with concise Doxygen comments in Spanish.

### Java

- Standard Java style: `PascalCase` classes, `camelCase` methods/fields,
  `UPPER_SNAKE_CASE` constants.
- Explicit access modifiers, generics instead of raw types, interfaces where they
  clarify contracts.
- Use the project's build tool (Maven/Gradle) and JUnit setup if present.
- Follow the existing package structure.
- Document public classes, methods, and modules with concise Javadoc in Spanish.

### TypeScript / JavaScript

- TypeScript strict mode; avoid `any`. Use `unknown` plus narrowing when the type is
  genuinely unknown.
- Explicit return types on exported functions.
- Prefer `const`, immutable data, and pure functions where practical.
- Use the project's framework and state patterns; do not introduce a new one.
- Use ESLint/Prettier when configured; otherwise match the surrounding style.
- Document exported functions and modules with concise JSDoc/TSDoc in Spanish.

### SQL

- Uppercase SQL keywords; `snake_case` identifiers.
- Explicit `JOIN ... ON`; no implicit joins. Avoid `SELECT *` in application
  queries.
- Parameterized queries only; never interpolate user input.
- Use CTEs for complex queries and format for readability.
- Match existing schema naming when present.
- Comment complex queries, views, and stored procedures concisely in Spanish.

### Python (brief)

- Use a virtualenv; never install packages globally.
- Type hints on public functions, `snake_case`, PEP 8.
- Prefer the standard library; ask before adding packages.
- For notebooks, keep cells small and move reusable logic into modules.
- Use concise docstrings in Spanish on public functions and modules.

## Error handling

- Be idiomatic: exceptions in Java, TypeScript, and Python; error codes/returns in C;
  exceptions with RAII in C++.
- Validate inputs at boundaries. Never swallow errors silently.
- Error messages should be clear, actionable, and in the project's language.
- Only catch an error if you can handle it or add useful context.

## Testing and verification

- Run the existing test suite after changes. Do not add new tests unless I ask.
- If a test fails, report it and ask before changing test expectations.
- Before reporting back: build/type-check, run tests, and run the linter if
  configured. If a step is unavailable, say so.
- Do not claim something works without running the relevant check.

## Dependencies and tooling

- Prefer the standard library. Use well-maintained third-party libraries when they
  clearly save significant work.
- Always ask before adding a dependency, installing software, or making network
  requests.
- Use the project's existing package manager, build tool, and formatter. Do not
  switch tools.
- Never mass-reformat files or directories without explicit approval.

## Git

- Read-only by default: `status`, `diff`, `log`, `show`, `blame` are fine.
- Never commit, push, branch, merge, rebase, reset, or stash unless I explicitly ask
  in that message.
- If I ask for a commit message, use Conventional Commits: English type prefix,
  Spanish description/body. Example: `feat: agregar validación de formulario`.
- Never amend or rewrite history.

## Documentation

- Document exported/public APIs, functions, and modules with concise doc comments
  (Javadoc, Doxygen, JSDoc/TSDoc, docstrings) in Spanish.
- Include a short summary plus the relevant tags (`@param`, `@return`, `@throws`,
  etc.) where they add information. Skip tags that merely restate the signature.
- Private/internal helpers get at most a one-line Spanish comment, and only when
  their purpose or behavior is not obvious.
- Keep READMEs and docs in sync when behavior, usage, commands, or setup change.
- Match the language of the existing project documentation; if there is none, ask.
- Document the why and the non-obvious, not the obvious.
- Update examples and config snippets when behavior changes.

## Always confirm first

- Deleting files or large blocks of code.
- Changing public interfaces, APIs, schemas, or data formats.
- Adding dependencies, installing tools, or making network requests.
- Mass-reformatting files or directories.
- Running any git command that changes state.
- Refactoring unrelated code or introducing new architectural patterns.
