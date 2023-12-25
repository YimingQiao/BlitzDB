BlitzDB
=====

BlitzDB is an in-memory database prototype of using Blitzcrank for storage, it is based on [Silo](http://people.csail.mit.edu/stephentu/papers/silo.pdf). 

Build
-----

The build requirements are given in the file `BUILD`. 

There are several options to build. `MODE` is an important variable
governing the type of build. The default is `MODE=perf`, see the
Makefile for more options. `DEBUG=1` triggers a debug build (off by
default). Examples:

    MODE=perf make -j dbtest

Each different combination of `MODE`, `DEBUG` triggers
a unique output directory; for example, the first command above builds to
`out-perf.debug.check.masstree`.

Running
-------

To run the tests, an example invocation for TPC-C is:

    ./out-perf.masstree/benchmarks/tpcc_blitz --verbose --bench tpcc --num-threads 4 --mem-limit 8 --scale-factor 4 --runtime 10

    <outdir>/benchmarks/tpcc_blitz \
        --verbose \
        --bench tpcc \
        --num-threads 28 \
        --scale-factor 28 \
        --runtime 30 \
        --numa-memory 112G 
