## Getting into Tosun Cluster

### Within campus
`ssh username@tosun`

### From outside of campus
`ssh username@flow.sabanciuniv.edu`  
Then  
`ssh username@tosun.sabanciuniv.edu`  

## Tosun Cluster Specifications
Tosun clusters consists of 1 login, 6 work and 1 GPU nodes. Which specified by:  

| Node  | CPU                                         | # Cores | # Threads | Memory     | GPU        |
|-------|---------------------------------------------|---------|-----------|------------|------------|
| login | Intel(R) Xeon(R) Gold 6140 CPU @ 2.30GHz X2 | 36      | 72        | 257366 MB  | -          |
| cn01  | Intel(R) Xeon(R) Gold 6140 CPU @ 2.30GHz X2 | 36      | 72        | 257366 MB  | -          |
| cn02  | Intel(R) Xeon(R) Gold 6140 CPU @ 2.30GHz X2 | 36      | 72        | 257366 MB  | -          |
| cn03  | Intel(R) Xeon(R) Gold 6140 CPU @ 2.30GHz X2 | 36      | 72        | 257366 MB  | -          |
| cn04  | Intel(R) Xeon(R) Gold 6140 CPU @ 2.30GHz X2 | 36      | 72        | 257366 MB  | -          |
| cn05  | Intel(R) Xeon(R) Gold 6140 CPU @ 2.30GHz X2 | 36      | 72        | 257366 MB  | -          |
| cn06  | Intel(R) Xeon(R) Gold 6140 CPU @ 2.30GHz X2 | 36      | 72        | 257366 MB  | -          |
| gpu01 | ??                                          | 8       | 16        | 251GiB     | Tesla V100 |
| mem01 | Intel(R) Xeon(R) Gold 6140 CPU @ 2.30GHz X4 | 72      | 144       | 1031504 MB | -          |
| Total |                                             | 294     | 588       | 2833066 MB |            |

  
Intel(R) Xeon(R) Gold 6140 CPU in worker have the following compute capabilities(flags):

fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid dca sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch epb invpcid_single intel_pt ssbd ibrs ibpb stibp kaiser tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm cqm mpx avx512f rdseed adx smap clflushopt clwb avx512cd xsaveopt xsavec xgetbv1 cqm_llc cqm_occup_llc cqm_mbm_total cqm_mbm_local dtherm ida arat pln pts pku flush_l1d

