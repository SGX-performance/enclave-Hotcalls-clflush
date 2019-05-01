```
----------------------------------------
enclave-Hotcalls-clFlush
Copyright 2019 Tõnis Lusmägi
Copyright 2019 TalTech

HotCalls
Copyright 2017 The Regents of the University of Michigan
Ofir Weisse, Valeria Bertacco and Todd Austin
https://github.com/oweisse/hot-calls
---------------------------------------------
```

# HotCalls
## A fast alternative interface for SGX secure enclaves

Based on ISCA 2017 HotCalls paper, that can be found at (http://www.ofirweisse.com/previous_work.html).

# HotCalls-clFlush
## cold cache results by flushing cache lines

clflush() buffer before each measurment

### Build and run tests
`make SGX_MODE=HW SGX_PRERELEASE=1; ./test_hotcalls_clflush`

`./run.sh` to run the full benchmark.

The main benchmark function is at App/App.cpp: HotCallsTester::Run().

Measurements of different type of calls are in `measurements/<timestamp>` directory:

- HotEcall_latencies_in_cycles.csv
- HotOcall_latencies_in_cycles.csv
- SDKEcall_latencies_in_cycles.csv
- SDKOcall_latencies_in_cycles.csv

The number of iterations is defined by `PERFORMANCE_MEASUREMENT_NUM_REPEATS` at `App/App.cpp`.

The round trip time of calls is measured in cycles, using RDTSCP insturction. The overhead of the RDTSCP insturction is roughly 30 cylces, which should be substructed from the numbers in the `csv` files. Different machines may have different overheads for RDTSCP.  

NOTE: the file `spinlock.c` is taken from Intel's SGX SDK repository at (https://github.com/01org/linux-sgx)
