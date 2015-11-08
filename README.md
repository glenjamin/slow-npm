# Making npm@3 faster?

A bunch of files and stuff related to investiaging speeding up npm@3

See also https://github.com/npm/npm/issues/8826

## Files

### Install information

I ran the following, saving the output as `npm3-output.txt` and the v8 log as `isolate-0x101804c00-v8.log` (gzipped in the git repo).

```sh
> node -v
v4.2.2

> npm -v
3.3.12

> npm config set loglevel http

> node --prof `which npm` install
```

### Profiling output

```sh
node-tick-processor --mac isolate-0x101804c00-v8.log > profiling.txt
```

### Duplicated requests

```sh
grep 'request GET' npm3-output.txt  | sort | uniq -c > duplicate-requests.txt
```

