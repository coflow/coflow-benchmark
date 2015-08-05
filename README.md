# Coflow-Benchmark README

The **Coflow-Benchmark** project aims to provide realistic workloads synthesized from real-world data-intensive applications for developing coflow-based solutions. 

## Traces
Currently, **Coflow-Benchmark** contains the following single-wave, single-stage coflow trace(s).

###FB2010-1Hr-150-0.txt
* The original trace is from a 3000-machine 150-rack MapReduce cluster at Facebook with 10:1 oversubscription ratio (circa 2010). 
* The synthesized one-hour trace contains 526 coflows that are scaled down to a 150-port fabric (i.e., to the rack-level) with exact inter-arrival times.
* All mappers in the same rack are combined into one rack-level mapper, and all reducers in the same rack are combined into one rack-level reducer.
* Rack-level communication patterns (i.e., coflow structures) are accurately captured and the amounts of data being shuffled (e.g., coflow size) are accurate to the nearest megabyte.

## Trace Format
```
Line 1: <Number of ports in the fabric> <Number of coflows below (one per line)>
Line i: <Coflow ID> <Arrival time (ms)> <Number of mappers> <Location of map-m> <Number of reducers> <Location of reduce-r:Shuffle megabytes of reduce-r>
```

## How to Use
* **Simulation**: The <a href="https://github.com/coflow/coflowsim">CoflowSim</a> projects takes **Coflow-Benchmark** traces as input through the `CoflowBenchmarkTraceProducer` class. 
* **Deployment**: Support for using **Coflow-Benchmark** in conjunction with <a href="https://github.com/coflow/varys">Varys and Aalo</a> (systems that schedule coflows in large clusters) are forthcoming. 

## Contribute
Please contribute new traces from your workload along with a short paragraph on details as <a href="https://github.com/coflow/coflow-benchmark/pulls">pull requests</a> to make **Coflow-Benchmark** more diverse.

## References
Please refer to/cite the following papers to know more about coflows, coflow scheduling, or just more details on the original traces these traces were synthesized from. 

1. <a href="http://www.mosharaf.com/wp-content/uploads/aalo-sigcomm15.pdf">Efficient Coflow Scheduling Without Prior Knowledge</a>, Mosharaf Chowdhury, Ion Stoica, ACM SIGCOMM, 2015.
2. <a href="http://www.mosharaf.com/wp-content/uploads/varys-sigcomm14.pdf">Efficient Coflow Scheduling with Varys</a>, Mosharaf Chowdhury, Yuan Zhong, Ion Stoica, ACM SIGCOMM, 2014.
