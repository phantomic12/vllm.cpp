ID: ISSUE-LOCAL-01M448WBTEGX4587Z37FPEN4H7
Title: PR #361 stale-base clobber reverted bench flags + block-size fix
Row: -
State: CLOSED
Kind: bug
GitHub: -
Mirror: PENDING
Availability: FULL
Created: 2026-10-04
Updated: 2026-10-04
Closed: 2026-10-04

## Problem

Merge 096e805bb (PR #361, Pi5 runs) carried an older copy of examples/bench/ and silently reverted the --kv-cache-dtype/--ignore-eos/--skip-chat-template/--chat-template/--enable-thinking flags, the requested-vs-resolved report lines, and the block_size %16 alignment fix, while the ctests expecting them stayed. test_bench, test_bench_kv_cache_dtype and test_bench_eos_chat_template are red on main. Restore the features onto current main, keeping the blocking-C1 output-wait machinery the intervening commits added.

## Resolution

Restored the clobbered bench feature set on current main; 3/3 bench ctests pass (test_bench, test_bench_kv_cache_dtype, test_bench_eos_chat_template).
