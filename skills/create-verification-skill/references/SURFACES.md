# Surface recipes

Read the common contract, then only the branch matching the selected endpoint. These are selection criteria, not prescribed tools: reuse the repository's harness and vocabulary.

## Common contract

The endpoint is the public surface a real user or consumer depends on. Launch an isolated target where possible, identify it before driving, and observe both the returned/visible result and material side effects. Keep concurrency bounded and give every process, session, emulator, or consumer run an owner and teardown handle.

Choose stable semantic handles already present in the product. Record unreachable prerequisites rather than substituting a different entry point and calling it verified.

## Web

- **Launch:** use the repository's dev, preview, or packaged-server command with an isolated port/profile/data directory.
- **Doctor:** verify URL, build identity, expected route, and ownership of the target instance.
- **Drive:** prefer the existing browser harness and accessible names, roles, labels, or deliberate test IDs over coordinates or DOM position.
- **Evidence:** retain action traces plus rendered result; confirm durable effects through a second user-facing read when possible.
- **Cleanup:** close only the run-owned browser context and server, then remove its profile and data.

Driving a real browser requires explicit authorization, even against a local target.

## API

- **Launch:** use the normal service command with isolated ports and non-production dependencies.
- **Doctor:** query a read-only health/version endpoint and confirm target identity, auth scope, and dependency readiness.
- **Drive:** call the public protocol with the repository's existing client, contract runner, or structured HTTP/RPC tooling.
- **Evidence:** capture redacted request shape, status/protocol result, response body, and externally observable state transition.
- **Cleanup:** remove run-owned resources through supported public cleanup operations and stop the owned service.

Do not treat a test-only endpoint or direct storage mutation as endpoint proof. Remote APIs and resource mutations are external effects and require authorization.

## CLI

- **Launch:** build or resolve the same executable users run. A short-lived command launches per drive; an interactive CLI/TUI uses an isolated PTY/session owned by the run.
- **Doctor:** record executable path/version plus required local dependency and fixture readiness.
- **Drive:** invoke literal commands or stable prompt text through the repository's existing CLI harness.
- **Evidence:** capture command/input, stdout, stderr, exit code, and resulting files or state visible through a public command.
- **Cleanup:** close the owned PTY/session and remove only run-specific files and configuration.

## Library

- **Launch:** build or resolve the distributable artifact and create an isolated consumer outside private source modules.
- **Doctor:** prove the consumer resolves the intended artifact/version and compatible runtime.
- **Drive:** compile/run a minimal consumer through the public import, package, ABI, or documented entry point.
- **Evidence:** retain consumer source, build/run command, public return/output/error, and any documented side effect.
- **Cleanup:** remove the temporary consumer and caches owned by the run while keeping copied proof artifacts.

A direct call to a private module is a local seam test, not library endpoint proof.

## Desktop

- **Launch:** use the repository's packaged or development app command with an isolated profile/data directory.
- **Doctor:** identify app build, window/process ownership, profile, and required local services.
- **Drive:** prefer an existing accessibility, application-driver, or protocol harness; use semantic controls rather than screen coordinates.
- **Evidence:** capture action trace and visible application state, then confirm persisted effects through the app where possible.
- **Cleanup:** close the owned app instance and its profile without touching the user's session.

If the driver operates a real browser engine or causes external effects, obtain the corresponding authorization.

## Mobile

- **Launch:** use the repository's existing simulator, emulator, device, or application-test harness with an isolated app/data identity where supported.
- **Doctor:** confirm app build, target device/runtime, install identity, permissions, and backend target.
- **Drive:** use semantic accessibility identifiers or the project's established mobile driver.
- **Evidence:** capture actions, rendered state, lifecycle-relevant logs, and user-visible persistence after navigation or relaunch when material.
- **Cleanup:** uninstall/reset only the run-owned app data and stop only a run-owned simulator/emulator.

Physical devices, remote device farms, account changes, notifications, purchases, and network mutations are external effects and require explicit authorization.
