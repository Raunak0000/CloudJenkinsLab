# FestPass — Jenkins CI/CD Assignment

## 1. Project
FestPass is a Java 21 campus event registration application. Jenkins compiles, tests, packages, and smoke-tests the application.

## 2. Red-to-Green Evidence

### Build #2 — FAILURE
- Commit: `082633f31768c81e9fa988cdabef70b74f789f3b`
- Cause: SCM change.
- Result: 28 tests executed; 3 failures.
- Failed assertion: `cancellationFreesSeat` — cancellation did not free a seat when the event was full.
- Additional failures: `cancellationsSurviveReload` and `cliWorkflowPersistsAcrossCommands`.
- Gated stages: Build JAR, Smoke test JAR, and Save artifact were skipped.
- Diagnostic evidence CSV was archived.

### Build #3 — SUCCESS
- Commit: `2e6a5e8044ca0840e87edbc4da210623eab4136a`
- Cause: SCM change.
- Result: 28 tests passed, 0 failures.
- JAR packaging succeeded.
- Seven real-JAR smoke tests passed.
- Final JAR and submission evidence CSV were archived.

## 3. Diagnosis and Fix
The booking cancellation logic did not correctly handle seat availability when an event was sold out. This also affected cancellation persistence and the CLI workflow. The application fix restored the expected cancellation and seat-reuse behavior. The supplied tests were left unchanged.

## 4. Artifacts
- `build-2-red/submission-evidence.csv`
- `build-3-green/submission-evidence.csv`
- `build-3-green/festpass.jar`
- `build-3-green/build-info.txt`
- `build-3-green/smoke-test.txt`

## 5. Local Verification
The application was executed locally. Event creation, successful bookings, sold-out rejection, cancellation, seat reuse, and persisted event data were verified.

## 6. Repository
https://github.com/Raunak0000/CloudJenkinsLab
