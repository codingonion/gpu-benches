# cuda-roofline

Short CUDA code that scans a range of Computational Intensities, by varying the amount of inner loop trips. The shell script series.sh builds an executable for each value, and executes them one afer another after finishing building.

The Code runs simultaneously on all available devices.


# cuda-memcpy

Measures the host-to-device transfer rate of the cudaMemcpy function over a range of transfer sizes


# um-stream

Measures CUDA Unified Memory transfer rate using a STREAM triad kernel. A range of data set sizes is used, both smaller and larger than the device memory. Example output:

```console
 buffer size      time   spread   bandwidth
       24 MB     0.1ms     3.2%   426.2GB/s
       48 MB     0.1ms    24.2%   511.6GB/s
       96 MB     0.1ms     0.8%   688.0GB/s
      192 MB     0.3ms     1.8%   700.0GB/s
      384 MB     0.5ms     0.5%   764.6GB/s
      768 MB     1.0ms     0.2%   801.8GB/s
     1536 MB     2.0ms     0.0%   816.9GB/s
     3072 MB     3.9ms     0.1%   822.9GB/s
     6144 MB     7.8ms     0.2%   823.8GB/s
    12288 MB    15.7ms     0.1%   822.1GB/s
    24576 MB  5108.3ms     0.5%     5.0GB/s
    49152 MB 10284.7ms     0.8%     5.0GB/s
```


# cuda-cache

Measures bandwidths of different cache levels. Launches one thread block per SM. Each thread block reads the contents of the same buffer. Varying buffer sizes changes the targeted cache level. Example output
```console
     data set   exec time     spread        Eff. bw      DRAM read     DRAM write        L2 Read       L2 Write      Tex Read
         4 kB         1ms       0.2%    5559.0 GB/s       0.0 GB/s       0.0 GB/s       0.8 GB/s       0.0 GB/s   11217.9 GB/s
         8 kB         1ms       3.9%   10983.3 GB/s       0.0 GB/s       0.0 GB/s       1.1 GB/s       0.0 GB/s   11272.8 GB/s
        16 kB         1ms       0.1%   12374.0 GB/s       0.0 GB/s       0.0 GB/s       1.3 GB/s       0.0 GB/s   12501.7 GB/s
        32 kB         2ms       0.1%   13219.3 GB/s       0.0 GB/s       0.0 GB/s       1.3 GB/s       0.0 GB/s   13297.7 GB/s
        64 kB         4ms       0.1%   13667.4 GB/s       0.0 GB/s       0.0 GB/s       1.4 GB/s       0.0 GB/s   13708.2 GB/s
       128 kB         8ms       4.8%   13271.6 GB/s       0.0 GB/s       0.0 GB/s    1380.6 GB/s       0.0 GB/s   13706.6 GB/s
       256 kB        91ms       4.7%    2310.2 GB/s       0.0 GB/s       0.0 GB/s    2520.3 GB/s       0.0 GB/s    2521.9 GB/s
       512 kB       176ms       6.8%    2383.2 GB/s       0.0 GB/s       0.0 GB/s    2544.9 GB/s       0.0 GB/s    2544.4 GB/s
      1024 kB       338ms       4.3%    2482.0 GB/s       0.0 GB/s       0.0 GB/s    2544.2 GB/s       0.0 GB/s    2544.0 GB/s
```