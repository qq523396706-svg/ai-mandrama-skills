# Isolated Rewrite Audit

Date: 2026-09-08

## Boundary

- Write target: this directory only.
- Existing production Skills: read-only and unchanged.
- Earlier publication candidate: read-only and unchanged.
- Local projects, customer files, research archives and media: excluded.
- Remote repository creation, push and public visibility: explicitly authorized by the repository owner after review.

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

- 27 publication files;
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

## Known remote source-corpus screening

The final source-corpus pass selected root README/license files and topical Skill, reference, template, prompt and workflow documents from 16 known public repositories. Generated `agents/openai.yaml` files were excluded from the release-text numerator after their generic UI metadata created the only initial long matches. The final comparison covered 13 authored release documents and 709 selected upstream text files.

| Public source | Audited commit | License signal | Release-text 20-character containment | Exact lines ≥16 |
|---|---|---|---:|---:|
| `0xadvait/ai-video-skill` | `79b1edf6be61` | MIT | 0.0000% | 0 |
| `62656456/ai-film-skills` | `678edc06d331` | Apache-2.0 | 0.0000% | 0 |
| `agentara/skills` | `dcb37f647711` | MIT | 0.0000% | 0 |
| `cyuanxv/ai-mandrama-skills` | `0142fc16742b` | MIT | 0.0000% | 0 |
| `gaojesse999/ai-scripts` | `0aa5732d50a6` | Apache-2.0 | 0.0000% | 0 |
| `HVision-NKU/StoryDiffusion` | `8de45e424887` | Apache-2.0 | 0.0000% | 0 |
| `lukasersil/seedance-25` | `aa5dfc56e89e` | MIT | 0.0000% | 0 |
| `nolanx-ai/nolanx.ai` | `595d86364377` | MIT | 0.0000% | 0 |
| `oiuv/ai-short-drama` | `4f318097c54a` | no standalone license found | 0.0000% | 0 |
| `OSideMedia/higgsfield-ai-prompt-skill` | `c0b73ab946df` | MIT | 0.0384% | 0 |
| `TateZhouSiu/create-storyboard-skill` | `4b8662e2fee5` | MIT | 0.0000% | 0 |
| `tianqing-Y/ai-short-drama-workflow` | `66847f2c12f0` | no standalone license found | 0.0000% | 0 |
| `weeduon/ai-short-drama-studio` | `b2e484a8d58d` | MIT | 0.0000% | 0 |
| `wuwangzhang1216/DirectorSKILL` | `c65ae0d14457` | MIT | 0.0000% | 0 |
| `xuanyustudio/LocalMiniDrama` | `7b6c1a748e9e` | MIT | 0.0000% | 0 |
| `zenstory-ai/drama-skills` | `84434570784b` | MIT | 0.0000% | 0 |

The four shared 20-character shingles behind the 0.0384% result are consecutive substrings of the required identifier `emotion-performance-director`; they are not copied prose. No authored release document shared a complete normalized line of at least 16 characters with any selected upstream file. This selection-based scan does not claim to enumerate the entire internet or prove legal independence.

## Decision

Current state: `PUBLIC_RELEASE_APPROVED`.

The rewrite is structurally ready for public version control. The automated evidence, manual classification of every non-zero source-corpus match, exclusion of unlicensed source material and explicit owner approval support publication under MIT. The repository continues to disclose that this was an isolated rewrite by an environment with prior source exposure, not a strict legal clean-room process.

## Release actions

- MIT license selected for the repository's own files;
- known remote source-corpus review completed and all matches classified;
- final security, link, structure and Skill validation passed on the publication tree;
- public remote creation and push may proceed under the owner's explicit approval.
