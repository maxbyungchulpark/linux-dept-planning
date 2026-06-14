# DEPT Planning

> ### Collect Multiple Acked-by Tags
> ### Build Community Consensus on False Positives (via Conferences/Summits)
> ### Collect Useful DEPT Reports Through Various Testing
> ### Trigger Hang Issues Using RT & Syzkaller Fuzzing to Test DEPT
> ### Search for Existing 'task hung/hang' Issues to Validate DEPT
> ### Submit DEPT Reports to LKML

## DO IT NOW

### [Yunseong DL 6/28] Create repo for testing DEPT and share the url
### [Yunseong DL 6/28] Add RT Hang Annotation for DEPT (Yunseong)
* `cfs` (un)throttling.
* Locking priority inheritance.
* Review Paran's patch.
* Make able to handle throttling wait in irq (Byungchul).

### [Yeoreum DL 6/21] Handle Folio Migration Nested Locks (Byungchul, Yeoreum)
* Acquire consecutive locks for `src` and `dst` using the same class.
* Modify DEPT engine to properly handle folio nested locks (Byungchul).
* Add the `folio_lock_nested()` API (Byungchul).
* Implement the use of `folio_lock_nested()` (`fs` by Yeoreum, `migration` by Byungchul).

### [Byungchul DL 6/21] Rebase DEPT on 7.0 via github
### [Byungchul DL 6/21] Configure Classes Using the Folio Class Configuration API (Yeoreum, Byungchul)
* Set default, block file, and regular file classes at appropriate locations.
* Resolve false positives caused by block-file-use folios and regular-file-use folios.

## DO IT SOON

### Performance optimization using rcu onto DEPT core (Yeoreum)

### Contribute `dept.md` for AI md to github.com/masoncl/review-prompts

### Prepare for LPC: Discuss Direction for DEPT False Positives (Byungchul)
* Reach a consensus with the community on the future direction of handling false positives.

### Support `rw_sem` Released Across Contexts (Byungchul)

### Add Deadlocks to Unit Tests (Yunseong)
* Work on `kunit` and `lkdtm`.
* Add `pg flags` to `lkdtm`.
* Add `folio_lock` vs `wait_for_completion` to `lkdtm`.
* Add `rw_sem` to `lkdtm`.

### Resolve LLVM `THIS_IP` Complain Issue (Byungchul)
* A workaround or fix is required to enable DEPT under LLVM.
* Receive `THIS_IP` as a stack variable and pass it as a function argument.
* Disable LLVM indirect goto warnings when DEPT is enabled (Yunseong).
* Introduce `ARCH_THIS_IP` (Paran) — *Needs review: Is this too much?*
* Investigate the root cause of the binary size increase resulting from Yeoreum's `THIS_IP` implementation.
* Raise an issue on LKML: `arch THIS_IP` implementation vs. disabling warnings (Byungchul).
---
## DO IT LATER

### Detection in Distributed Machine Environments (Yeoreum, Post-Merge)
* Collect data locally on each kernel as currently done.
* Aggregate the collected dependency information onto a single machine.
* Recheck the dependency graph at the user level on the aggregating machine.
* Implement user-level reporting capabilities.

### Leverage DEPT's Resilience to Missing Data for User-Level Processing (Yeoreum, Post-Merge)
* Ultimately offload processing from the kernel to the user space.

### Implement Module DEPT (Yeoreum, Post-Merge)

### Implement Class Filter Functionality (Yeoreum, Paran)
* Feature to exclude unwanted classes.
* Requires review of dynamic debugging.
* Apply a simple filter (Paran).
* Operate based on string matching:
* `all`: Same as current behavior.
* `default`: Print nothing.
