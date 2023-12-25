BlitzDB
=====

BlitzDB the prototype of an in-memory OLTP database containing Blitzcrank, it is based on [Silo](http://people.csail.mit.edu/stephentu/papers/silo.pdf). 

Build
-----

There are several options to build. `MODE` is an important variable
governing the type of build. The default is `MODE=perf`, see the
Makefile for more options. `DEBUG=1` triggers a debug build (off by
default). There are two targets: the default target which builds the test suite, and
`dbtest` which builds the benchmark suite. Examples:

    MODE=perf make -j dbtest

Each different combination of `MODE`, `DEBUG` triggers
a unique output directory; for example, the first command above builds to
`out-perf.debug.check.masstree`.

Running
-------

To run the tests, simply invoke `<outdir>/test` with no arguments. To run the
benchmark suite, invoke `<outdir>/benchmarks/dbtest`. For now, look in
`benchmarks/dbtest.cc` for documentation on the command line arguments. An
example invocation for TPC-C is:

    <outdir>/benchmarks/dbtest --verbose --bench tpcc --num-threads 4 --mem-limit 8 --scale-factor 4 --runtime 10

    <outdir>/benchmarks/dbtest \
        --verbose \
        --bench tpcc \
        --num-threads 28 \
        --scale-factor 28 \
        --runtime 30 \
        --numa-memory 112G 
