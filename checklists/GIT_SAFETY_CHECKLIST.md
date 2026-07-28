# Git Safety Checklist

Verifies the ten topics in `core/GIT_STANDARD.md` before a risky operation or
release. Answer every item Yes / No / N/A.

| # | Topic | Item | Y / N / N-A |
|---|---|---|---|
| 1 | Repository Integrity | No undocumented destructive operation performed on a shared branch | |
| 2 | Branch Strategy | Strategy is documented and actual practice matches it | |
| 3 | Commit Quality | Commits are coherent; messages match their diffs | |
| 4 | Tagging | Release tagged per the documented naming scheme | |
| 5 | Release Management | Release matches a verified, documented state | |
| 6 | Recovery | Recovery path identified and confirmed to work before any risky operation | |
| 7 | Rollback | Changes structured so any one change can be reverted independently | |
| 8 | Lowest-Risk Decision Making | Lower-risk alternative was explicitly considered for any destructive operation | |
| 9 | History Preservation | History not rewritten in a way that loses traceability | |
| 10 | Repository Verification | Fresh checkout of the tagged state confirmed to match Quality Gate | |
