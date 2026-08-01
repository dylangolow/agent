# AGENTS.md

- Favor immutability, `const` over `let`.
- Avoid unnecessary complexity.
- Avoid over-engineering.
- Prefer upgrading runtimes and tooling over pinning older versions for compatibility; only keep an old version when the upgrade is blocked and call out why.
- Pin runtime and tooling majors explicitly; do not use floating aliases like `latest`, `current`, or `lts/*`.
- Avoid configurable Terraform modules unless current usage requires it; no unused knobs.
- Favor existing, battle-tested libraries and tooling over custom implementations unless the task explicitly demands bespoke behavior.
- Group all constants at the top of the module or scope, but only when reused; inline single-use values and one-off helper consts.
- If a value is used once (e.g., base objects for spreads), inline it unless reuse is needed.
- Avoid duplication and keep sources of truth single to reduce maintenance overhead.
- When updating the Codex CLI version, update both `CODEX_VERSION` in `src/agents/codex/codex.ts` and `scripts/bootstrap-codex-auth.sh`.
- Avoid defensive code; write only what requirements or evidence justify.
- Avoid scope creep; no extra changes or state tweaks unless required or asked.
- When changing behavior, check for existing tests covering it; add or update tests to cover the new behavior if missing.
- In all interactions and commit messages, be extremely concise and sacrifice grammar for the sake of concision.
- Name mocks with a `Mock` suffix (e.g., `userMock`, not `mockUser`/`mockedUser`), to stay consistent across tests.
- Avoid `any`/type assertions; only use them as a last resort and keep them out of non-test code whenever possible.

## Release Operability and Project Bootstrap

- When bootstrapping a repository, ask whether a trusted, less-technical person must be able to ship changes when maintainers are unavailable.
- If yes, propose a plain-language release-operator runbook and link it from the repository `AGENTS.md`.
- Base the runbook on the repository's real branch flow, checks, approvals, deployment workflows, smoke tests, SHA verification, and stop conditions.
- Keep secrets and destructive recovery steps out of operator runbooks. Require technical escalation after a failed release.
- Before committing, pushing, or handing off completed work for merge, check whether the change affects operator release guidance.
- Propose a runbook update when release steps, migrations, configuration, workflow names, smoke coverage, rollback needs, or operator decisions changed.
- Ask the user to define or confirm the release process before writing instructions for a repository that does not have one.
