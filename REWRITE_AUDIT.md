# Isolated Rewrite Audit

Date: 2026-09-08

## Boundary

- Write target: this directory only.
- Existing production Skills: read-only and unchanged.
- Earlier publication candidate: read-only and unchanged.
- Local projects, customer files, research archives and media: excluded.
- Remote repository creation, push and public visibility: not authorized in this phase.

## Method

1. Defined the required behavior in `FUNCTIONAL_SPEC.md`.
2. Used the official `skill-creator` initializer to create blank Skill directories.
3. Wrote six new 2.0.0 entrypoints with a different workflow vocabulary, data contract, performance model, task state system and diagnostic codes.
4. Added only the references and starter assets needed by the new coordinator.
5. Kept all external capabilities as interfaces rather than copied dependencies.

The process does not claim strict clean-room independence because the execution environment had previously seen the old materials.

## Scaffold test incident

The first initializer run created five specialist `SKILL.md` files but rejected their UI metadata because the supplied short descriptions were 21–24 characters, below the official 25-character minimum. The directories were preserved. After writing the Skill entrypoints, the official `generate_openai_yaml.py` tool generated valid metadata with longer descriptions. No source directory was deleted or overwritten.

## Initial validation

After the six entrypoints and metadata were written, official `quick_validate.py` returned `Skill is valid!` for all six Skill directories under UTF-8.

## Completed structural checks

- 27 publication files totaling 58,383 bytes;
- six frontmatter names match their directory names;
- eight relative Markdown links resolve;
- the coordinator routes to all five bundled specialist Skills;
- static decisions for authorization waits, partial final checks, wrong-speaker diagnosis and physical-task preservation are present;
- no TODO scaffold markers remain;
- no credential pattern, private key, personal email, phone number, local absolute path, known private-project name, media, archive, file over 1 MiB or reparse point was found;
- the installed source set remains 27 files and 103,119 bytes;
- the earlier publication candidate remains clean at commit `50e8d548a13d`.

## Similarity screening

The audit removed YAML frontmatter before comparing Skill bodies, normalized case, whitespace and punctuation, and used unique 20-character shingles. It also checked exact normalized body lines with at least 12 characters and the longest contiguous normalized match.

| New Skill vs corresponding old Skill | New-body 20-character containment | Exact body lines ≥12 | Longest normalized run |
|---|---:|---:|---:|
| `ai-mandrama-production` | 0.71% | 0 | 26 |
| `emotion-performance-director` | 0.00% | 0 | 12 |
| `mandrama-voice-director` | 0.00% | 0 | 19 |
| `mandrama-lipsync-qc` | 0.00% | 0 | 13 |
| `seedance-batch-ops` | 0.38% | 0 | 23 |
| `mandrama-final-qc` | 0.71% | 0 | 26 |

The rewritten performance Skill compared with the unlicensed local performance archive produced 0.00% 20-character containment, zero exact normalized body lines of at least 12 characters, and a longest normalized run of 12 characters.

The remaining longest matches were required Skill invocation identifiers or short generic domain language. No old wording was copied as a complete body line. These metrics are screening evidence only; they do not determine copyright status or replace human review.

## Decision

Current state: `PUBLIC_REVIEW`.

The rewrite is structurally and operationally ready for private version control. It is not yet approved for a public open-source license because the same execution environment had prior source exposure and the complete remote source corpus has not received final human comparison.

## Remaining release checks

- review the known remote source corpus for any distinctive match not present in the old local versions;
- obtain a human rights decision for the remaining concepts influenced by the unlicensed local archive;
- choose and add an open-source license only after ownership is confirmed;
- repeat security, link and structure checks on the exact release commit;
- obtain explicit approval before remote creation, push or public visibility.
