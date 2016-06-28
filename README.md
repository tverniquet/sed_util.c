# sed_util.c

These are changes I made to sed util.c while exploring limits to streaming the input/output.

I was very suprised since I had always understood that the limit with streaming languages like sed was the disk io, not CPU.

Even with my changes I didn't manage to reach the 500MB/s of my hard disk.. so CPU is still the limiting factor.

**NOTE: This is potentially buggy and not suitable for actually using to run sed commands..**

Note: When compiling, sse4.2 is required, so I used:

```
CFLAGS="-O3 -march=native" ./configure
make
```

Running:
```
# normal sed
time sed '' <seq.1e8 >/dev/null # 7.2 seconds 117 MB/s

# with changes
time ./sed '' <seq.1e8 >/dev/null # 2.99 seconds 283 MB/s
```
