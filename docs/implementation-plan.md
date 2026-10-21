# Implementation Plan

## Current state

- Repository bootstrap is complete.
- The README is committed to the `main` branch.
- Upstream Android source has not yet been imported.
- No APK has been built or released from this repository.

## Product requirements

- Keep the original Cryptomator Android interface wherever practical.
- Support local vaults and supported cloud-storage providers.
- Preserve Cryptomator Hub entitlement checks and behavior; do not bypass paid or server-side access controls.
- Use a distinct application ID for this community variant so it can coexist with the official app.
- Provide source code and APK distribution, with release artifacts produced from the documented build process.
- Keep the project free to use and be transparent about upstream and third-party licensing requirements.

## Phases

### Phase 1 — Source and license review

1. Identify the intended upstream repository and compatible branch/tag.
2. Review its license, copyright notices, dependency licenses, and contribution requirements.
3. Inspect Gradle/Android build configuration and required SDK/JDK versions.
4. Trace Hub entitlement checks and identify which functionality is available under the intended community distribution.

**Exit criteria:** a documented baseline build and a clear license/compliance checklist.

### Phase 2 — Import and baseline build

1. Import the upstream source with its history and license notices where practical.
2. Keep the imported upstream baseline identifiable.
3. Build the unmodified app first.
4. Record build commands and resolve environment issues before product changes.

**Exit criteria:** baseline build succeeds and its output is verified.

### Phase 3 — Community variant

1. Configure a unique application ID (for example, a `.community` suffix, after checking upstream conventions).
2. Preserve the familiar UI and supported storage integrations.
3. Keep Hub entitlement logic intact.
4. Make only changes needed for the community variant and document them clearly.
5. Add regression tests for vault creation/opening, storage flows, and entitlement-related behavior.

**Exit criteria:** debug build installs separately and core flows pass tests.

### Phase 4 — Automation and device testing

1. Add a CI workflow to build and run available tests.
2. Document required secrets; never commit signing keys, tokens, or credentials.
3. Test installation, upgrades, vault operations, local storage, and supported cloud providers on a physical Android device.
4. Confirm that build artifacts can be reproduced from source.

**Exit criteria:** CI succeeds and device-test results are recorded.

### Phase 5 — First release

1. Prepare release notes and attribution.
2. Produce a signed APK using a securely managed release key.
3. Publish the APK and matching source revision.
4. State clearly that this is an independent community project and not an official Cryptomator release.

**Exit criteria:** users can inspect the source, verify the release version, and follow installation instructions.

## Risks and constraints

- Upstream APIs, build tooling, and dependencies may change.
- Cloud storage behavior depends on upstream support and provider requirements.
- App branding and distribution must comply with trademark and license requirements.
- Hub-related restrictions must not be circumvented.
- No release should be described as ready until a real build and device testing succeed.

## Immediate next action

Import the appropriate upstream source into this repository, preserving its license and notices, then confirm that a clean baseline build succeeds before changing application behavior.
