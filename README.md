# aion RCCL perf numbers

##  Single Node Collective Communication	RCCL - AllReduce Performance


```
sudo docker pull prasadnairamd/rccl-tests:latest


docker run --rm   --device=/dev/kfd   --device=/dev/dri   --group-add video   --ipc=host   --network=host   --cap-add=SYS_PTRACE   --security-opt  seccomp=unconfined prasadnairamd/rccl-tests   ./build/all_reduce_perf -f 2 -g 8 -b 4 -e 1G

amd@gpu-3:~$ docker run --rm   --device=/dev/kfd   --device=/dev/dri   --group-add video   --ipc=host   --network=host   --cap-add=SYS_PTRACE   --security-opt  seccomp=unconfined prasadnairamd/rccl-tests   ./build/all_reduce_perf -f 2 -g 8 -b 4 -e 1G
# rccl-tests version 2.17.9-develop:2596ca5f71 rccl-headers=22803 rccl-library=22707
# Collective test starting: all_reduce_perf
# nThread 1 nGpus 8 minBytes 4 maxBytes 1073741824 step: 2(factor) warmup iters: 1 iters: 20 agg iters: 1 validation: 1 graph: 0
#
# Using devices
#  Rank  0 Group  0 Pid      1 on      gpu-3 device  0 [0000:75:00] AMD Radeon Graphics
#  Rank  1 Group  0 Pid      1 on      gpu-3 device  1 [0000:05:00] AMD Radeon Graphics
#  Rank  2 Group  0 Pid      1 on      gpu-3 device  2 [0000:65:00] AMD Radeon Graphics
#  Rank  3 Group  0 Pid      1 on      gpu-3 device  3 [0000:15:00] AMD Radeon Graphics
#  Rank  4 Group  0 Pid      1 on      gpu-3 device  4 [0000:f5:00] AMD Radeon Graphics
#  Rank  5 Group  0 Pid      1 on      gpu-3 device  5 [0000:85:00] AMD Radeon Graphics
#  Rank  6 Group  0 Pid      1 on      gpu-3 device  6 [0000:e5:00] AMD Radeon Graphics
#  Rank  7 Group  0 Pid      1 on      gpu-3 device  7 [0000:95:00] AMD Radeon Graphics
#
#                                                              out-of-place                       in-place
#       size         count      type   redop    root     time   algbw   busbw  #wrong     time   algbw   busbw  #wrong
#        (B)    (elements)                               (us)  (GB/s)  (GB/s)             (us)  (GB/s)  (GB/s)
           4             1     float     sum      -1    45.99    0.00    0.00       0    43.01    0.00    0.00       0
           8             2     float     sum      -1    45.21    0.00    0.00       0    44.76    0.00    0.00       0
          16             4     float     sum      -1    46.45    0.00    0.00       0    44.27    0.00    0.00       0
          32             8     float     sum      -1    44.26    0.00    0.00       0    43.11    0.00    0.00       0
          64            16     float     sum      -1    45.67    0.00    0.00       0    43.19    0.00    0.00       0
         128            32     float     sum      -1    44.23    0.00    0.01       0    42.94    0.00    0.01       0
         256            64     float     sum      -1    43.80    0.01    0.01       0    42.15    0.01    0.01       0
         512           128     float     sum      -1    42.69    0.01    0.02       0    43.28    0.01    0.02       0
        1024           256     float     sum      -1    39.67    0.03    0.05       0    42.11    0.02    0.04       0
        2048           512     float     sum      -1    43.89    0.05    0.08       0    45.01    0.05    0.08       0
        4096          1024     float     sum      -1    44.08    0.09    0.16       0    43.14    0.09    0.17       0
        8192          2048     float     sum      -1    43.00    0.19    0.33       0    43.56    0.19    0.33       0
       16384          4096     float     sum      -1    44.43    0.37    0.65       0    43.39    0.38    0.66       0
       32768          8192     float     sum      -1    45.04    0.73    1.27       0    45.09    0.73    1.27       0
       65536         16384     float     sum      -1    44.50    1.47    2.58       0    42.61    1.54    2.69       0
      131072         32768     float     sum      -1    48.69    2.69    4.71       0    50.44    2.60    4.55       0
      262144         65536     float     sum      -1    50.49    5.19    9.09       0    49.13    5.34    9.34       0
      524288        131072     float     sum      -1    51.42   10.20   17.84       0    52.01   10.08   17.64       0
     1048576        262144     float     sum      -1    49.49   21.19   37.08       0    49.51   21.18   37.07       0
     2097152        524288     float     sum      -1    51.49   40.73   71.27       0    51.72   40.55   70.96       0
     4194304       1048576     float     sum      -1    58.10   72.19  126.33       0    60.78   69.01  120.76       0
     8388608       2097152     float     sum      -1    89.76   93.46  163.55       0    90.92   92.26  161.46       0
    16777216       4194304     float     sum      -1   152.89  109.74  192.04       0   153.83  109.07  190.86       0
    33554432       8388608     float     sum      -1   222.70  150.67  263.67       0   231.36  145.03  253.80       0
    67108864      16777216     float     sum      -1   403.13  166.47  291.32       0   406.27  165.18  289.07       0
   134217728      33554432     float     sum      -1   761.37  176.28  308.50       0   765.92  175.24  306.66       0
   268435456      67108864     float     sum      -1  1491.59  179.97  314.94       0  1501.14  178.82  312.94       0
   536870912     134217728     float     sum      -1  2956.13  181.61  317.82       0  2965.00  181.07  316.87       0
  1073741824     268435456     float     sum      -1  5829.09  184.20  322.36       0  5838.22  183.92  321.85       0
# Out of bounds values : 0 OK
# Avg bus bandwidth    : 83.8755
#
# Collective test concluded: all_reduce_perf
#

```
##  Single Node Collective Communication	RCCL - All2All Performance

```
amd@gpu-3:~$ docker run --rm   --device=/dev/kfd   --device=/dev/dri   --group-add video   --ipc=host   --network=host   --cap-add=SYS_PTRACE   --security-opt  seccomp=unconfined prasadnairamd/rccl-tests   ./build/alltoall_perf -b 8 -e 128M -f 2 -g 8
# rccl-tests version 2.17.9-develop:2596ca5f71 rccl-headers=22803 rccl-library=22707
# Collective test starting: alltoall_perf
# nThread 1 nGpus 8 minBytes 8 maxBytes 134217728 step: 2(factor) warmup iters: 1 iters: 20 agg iters: 1 validation: 1 graph: 0
#
# Using devices
#  Rank  0 Group  0 Pid      1 on      gpu-3 device  0 [0000:75:00] AMD Radeon Graphics
#  Rank  1 Group  0 Pid      1 on      gpu-3 device  1 [0000:05:00] AMD Radeon Graphics
#  Rank  2 Group  0 Pid      1 on      gpu-3 device  2 [0000:65:00] AMD Radeon Graphics
#  Rank  3 Group  0 Pid      1 on      gpu-3 device  3 [0000:15:00] AMD Radeon Graphics
#  Rank  4 Group  0 Pid      1 on      gpu-3 device  4 [0000:f5:00] AMD Radeon Graphics
#  Rank  5 Group  0 Pid      1 on      gpu-3 device  5 [0000:85:00] AMD Radeon Graphics
#  Rank  6 Group  0 Pid      1 on      gpu-3 device  6 [0000:e5:00] AMD Radeon Graphics
#  Rank  7 Group  0 Pid      1 on      gpu-3 device  7 [0000:95:00] AMD Radeon Graphics
#
#                                                              out-of-place                       in-place
#       size         count      type   redop    root     time   algbw   busbw  #wrong     time   algbw   busbw  #wrong
#        (B)    (elements)                               (us)  (GB/s)  (GB/s)             (us)  (GB/s)  (GB/s)
           0             0     float    none      -1     1.08    0.00    0.00       0     0.90    0.00    0.00    N/A
           0             0     float    none      -1     1.02    0.00    0.00       0     0.76    0.00    0.00    N/A
           0             0     float    none      -1     0.69    0.00    0.00       0     0.73    0.00    0.00    N/A
           0             0     float    none      -1     0.69    0.00    0.00       0     0.69    0.00    0.00    N/A
         128             4     float    none      -1    38.24    0.00    0.00       0    60.91    0.00    0.00    N/A
         256             8     float    none      -1    40.21    0.01    0.01       0    57.69    0.00    0.00    N/A
         512            16     float    none      -1    41.85    0.01    0.01       0    58.97    0.01    0.01    N/A
        1024            32     float    none      -1    38.90    0.03    0.02       0    57.16    0.02    0.02    N/A
        2048            64     float    none      -1    39.21    0.05    0.05       0    59.03    0.03    0.03    N/A
        4096           128     float    none      -1    41.44    0.10    0.09       0    57.26    0.07    0.06    N/A
        8192           256     float    none      -1    39.02    0.21    0.18       0    57.81    0.14    0.12    N/A
       16384           512     float    none      -1    41.61    0.39    0.34       0    58.22    0.28    0.25    N/A
       32768          1024     float    none      -1    42.07    0.78    0.68       0    57.59    0.57    0.50    N/A
       65536          2048     float    none      -1    42.20    1.55    1.36       0    60.07    1.09    0.95    N/A
      131072          4096     float    none      -1    40.26    3.26    2.85       0    61.50    2.13    1.86    N/A
      262144          8192     float    none      -1    46.86    5.59    4.90       0    67.19    3.90    3.41    N/A
      524288         16384     float    none      -1    46.95   11.17    9.77       0    67.22    7.80    6.82    N/A
     1048576         32768     float    none      -1    46.56   22.52   19.70       0    59.13   17.73   15.52    N/A
     2097152         65536     float    none      -1    47.73   43.94   38.45       0    63.64   32.95   28.84    N/A
     4194304        131072     float    none      -1    46.23   90.72   79.38       0    67.35   62.28   54.49    N/A
     8388608        262144     float    none      -1    48.55  172.77  151.18       0    68.04  123.29  107.88    N/A
    16777216        524288     float    none      -1    74.88  224.04  196.04       0    80.86  207.49  181.55    N/A
    33554432       1048576     float    none      -1   133.94  250.52  219.20       0   141.43  237.26  207.60    N/A
    67108864       2097152     float    none      -1   238.82  281.00  245.88       0   239.87  279.77  244.80    N/A
   134217728       4194304     float    none      -1   437.78  306.59  268.26       0   439.01  305.73  267.51    N/A
# Out of bounds values : 0 OK
# Avg bus bandwidth    : 47.2116
#
# Collective test concluded: alltoall_perf
#

```
