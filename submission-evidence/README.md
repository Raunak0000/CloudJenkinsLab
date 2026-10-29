# FestPass — Jenkins CI/CD Assignment

## 1. Project
FestPass is a Java 21 campus event registration application. Jenkins compiles, tests, packages, and smoke-tests the application.

## 2. Red-to-Green Evidence

### Build #6 — FAILURE
- Class code: `001`
- Challenge code: `00737`
- Commit: `ea15a57d9e57588ef4a1b1b71c317098d1ef0e3b`
- Cause: SCM change.
- Result: 28 tests executed; 3 failures.
- Failed test: `cancellationFreesSeat`.
- Additional failures: `cancellationsSurviveReload` and `cliWorkflowPersistsAcrossCommands`.
- Skipped stages: Build JAR, Smoke test JAR, and Save artifact.
- Diagnostic evidence CSV archived.

### Build #7 — SUCCESS
- Class code: `001`
- Challenge code: `00737`
- Commit: `4b02fa4a4550612f21d1547e82880417133e44ae`
- Cause: SCM change.
- Result: 28 tests passed, 0 failures.
- JAR packaging succeeded.
- Seven real-JAR smoke tests passed.
- Final JAR and submission evidence CSV archived.

## 3. Diagnosis and Fix
The booking cancellation logic did not correctly release a seat when an event was sold out. This also affected cancellation persistence and the CLI workflow. The fix restored cancellation, persistence, and seat-reuse behavior. Supplied tests were left unchanged.

## 4. Artifacts
- `build-6-red/submission-evidence.csv`
- `build-7-green/submission-evidence.csv`
- `build-7-green/festpass.jar`
- `build-7-green/build-info.txt`
- `build-7-green/smoke-test.txt`

## 5. Local Verification
Event creation, bookings, sold-out rejection, cancellation, seat reuse, and persisted event data were verified locally.

## 6. Repository
https://github.com/Raunak0000/CloudJenkinsLab
