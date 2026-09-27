# Agent Guidelines & Engineering Conventions

## Architecture

Follow clean architecture:
- Ports define contracts/interfaces.
- Adapters implement external systems and dependencies.
- Core business logic remains decoupled from frameworks and external orchestrators.

## Extend, don't edit

Add behaviour by writing a new implementation of an existing port and composing it in. Don't teach a working class a second job.

- **New behaviour**: write a new class implementing the relevant port interface, wired through its factory or composition root.
- **Fixing defects**: edit existing code directly. A bug fix is not an extension; don't build wrappers to avoid fixing the bug.
- **Missing port**: extract one when needed—explicitly declare it in your plan first.
- **No duplicate classes**: never clone a class into `FooV2` or `EnhancedFoo`. When two implementations share logic, extract a shared helper.

> **Code smell**: if a test has to monkeypatch third-party internals to reach a new branch, move the behaviour into its own class and test it against a stub.

## Error Handling & Contracts

- Adapters must honour their port's contract: degrade gracefully rather than raise unexpectedly when a fallback value makes sense.
- Avoid broad `except Exception:` catches. Catch specific exceptions and log with actionable context.
