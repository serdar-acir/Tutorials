## Getting into TOSUN Cluster

### Within campus
`ssh username@10.3.5.102`

### From outside of campus
`ssh username@flow.sabanciuniv.edu`  
Then  
`ssh username@10.3.5.102`

## TOSUN Cluster Specifications
TOSUN clusters consists of 1 login, 7 work and 1 GPU nodes. Which specified by:  

| Node  | CPU                                         | # Cores | # Threads | Memory     | GPU          |
|-------|---------------------------------------------|---------|-----------|------------|--------------|
| login | Intel(R) Xeon(R) Gold 6140 CPU @ 2.30GHz X2 | 36      | 72        | 257366 MB  | -            |
| cn01  | Intel(R) Xeon(R) Gold 6140 CPU @ 2.30GHz X2 | 36      | 72        | 257366 MB  | -            |
| cn02  | Intel(R) Xeon(R) Gold 6140 CPU @ 2.30GHz X2 | 36      | 72        | 257366 MB  | -            |
| cn03  | Intel(R) Xeon(R) Gold 6140 CPU @ 2.30GHz X2 | 36      | 72        | 257366 MB  | -            |
| cn04  | Intel(R) Xeon(R) Gold 6140 CPU @ 2.30GHz X2 | 36      | 72        | 257366 MB  | -            |
| cn05  | Intel(R) Xeon(R) Gold 6140 CPU @ 2.30GHz X2 | 36      | 72        | 257366 MB  | -            |
| cn06  | Intel(R) Xeon(R) Gold 6140 CPU @ 2.30GHz X2 | 36      | 72        | 257366 MB  | -            |
| cn07  | Intel(R) Xeon(R) Gold 6140 CPU @ 2.30GHz X2 | 36      | 72        | 257366 MB  | -            |
| gpu01 | Intel(R) Xeon(R) Gold 5122 CPU @ 3.60GHz X2 | 8       | 16        | 257366 MB  | Tesla V100 x2|
| mem01 | Intel(R) Xeon(R) Gold 6140 CPU @ 2.30GHz X4 | 72      | 144       | 1031504 MB | -            |
| Total |                                             | 294     | 588       | 2833066 MB |              |

  
Intel(R) Xeon(R) Gold 6140 CPU in worker have the following compute capabilities(flags):

fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid dca sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch epb invpcid_single intel_pt ssbd ibrs ibpb stibp kaiser tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm cqm mpx avx512f rdseed adx smap clflushopt clwb avx512cd xsaveopt xsavec xgetbv1 cqm_llc cqm_occup_llc cqm_mbm_total cqm_mbm_local dtherm ida arat pln pts pku flush_l1d  

### Tesla V100

Tesla V100 GPU have the following specifications:

| Specifications | Tesla V100 |
| -------------- | ---------- |
| GPU | GV100 (Volta) |
| SMs| 80 |
| TPCs |  40 |
| FP32 Cores / SM | 64 |
| FP32 Cores / GPU | 5120 |
| FP64 Cores / SM | 32 |
| FP64 Cores / GPU | 2560 |
| Tensor Cores / SM | 8 |
| Tensor Cores / GPU | 640 |
| Peak FP32 TFLOPS | 15.7 |
| Peak FP64 TFLOPS | 7.8 |
| Peak Tensor TFLOPS | 125 |
| Memory Size | 32 GB |
| L2 Cache Size | 6144 KB |
| Shared Memory Size / SM | Configurable up to 96 KB |
| Register File Size / SM | 256KB |
| Register File Size / GPU | 20480 KB | 


To tune your GPU application for volta architecture, take a look at this guide: [Volta Tuning Guide](https://docs.nvidia.com/cuda/volta-tuning-guide/index.html)

