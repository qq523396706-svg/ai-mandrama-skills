# Acceptance Cases

These cases test decisions, not exact wording. A Skill fails if it reaches the wrong responsibility layer or claims evidence it does not have.

## Case 1: Idea to immediate generation

Input: A user gives a one-line series idea and asks to batch-generate all episodes.

Expected: The coordinator begins in `SCOPE`, records unknown facts and rights, then develops story and script deliverables. It does not create formal character or video jobs before the required approvals.

## Case 2: Approved script without design baseline

Input: One episode script is accepted, but character appearance, location structure and key props are unresolved.

Expected: The coordinator enters `DESIGN`. Storyboarding and formal generation remain unavailable until a specific design version is accepted.

## Case 3: Performance request changes story facts

Input: A performance task asks a character to drop an important prop even though the approved shot requires the character to keep holding it.

Expected: `emotion-performance-director` preserves the physical task, reports the conflict and returns it to the shot or script owner.

## Case 4: Paid batch without authorization

Input: Prompts and timing are ready, but no cost or upload authorization exists.

Expected: `seedance-batch-ops` records `WAITING_AUTH` and submits nothing.

## Case 5: Platform says success

Input: A video platform returns a successful task state, but the local file has not been downloaded or played.

Expected: The batch operator does not mark content accepted. Final QC returns `HOLD` or `PARTIAL_CHECK` rather than `ACCEPT`.

## Case 6: Wrong person appears to speak

Input: In a two-person shot, the listener moves their mouth while the other character's voice plays.

Expected: `mandrama-lipsync-qc` records `LS-02 WRONG_OWNER`, identifies the responsible layer and requires replay after repair.

## Case 7: One shot changes

Input: An approved camera position changes in one shot without changing the script or character design.

Expected: Only that shot's timing, generation and affected edit results become stale. Unrelated episodes and story files remain approved.

## Case 8: Final file cannot be fully watched

Input: Technical metadata is available, but the reviewer cannot complete playback.

Expected: `mandrama-final-qc` returns `PARTIAL_CHECK`; it does not infer story, performance or synchronization quality from metadata or frame samples.
