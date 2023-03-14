According to the [telseq docs](https://github.com/zd1/telseq#run-telseq-1):
> Note that the sample path "/path/to/bam/sample.bam" in the machine that the
> container is run needs to be specified. "/sample.bam" doesn't need to be
> changed.
> `docker run -v /path/to/bam/sample.bam:/sample.bam telseq-docker /sample.bam`

The usage for `docker run` is `docker run [OPTIONS] IMAGE [COMMAND] [ARG...]`,
which is a bit counterintuitive, because *containers* *run*, not images, right?
But it expects the image. I use the ID because it's a bit more precise than the
name:

```
# List the images:
dlcott2@telomere-test-dlc ~ $ docker image ls
REPOSITORY                       TAG             IMAGE ID       CREATED       SIZE
gcr.io/my-cloud-project/telseq   <none>          f12e5862481f   2 hours ago   435MB
gcr.io/gce-containers/konlet     v.0.11-latest   73e140dc33e1   2 years ago   74.8MB
d
```

And run the one with `telseq` on it:
```
$ docker run -v test.bam:/sample.bam f12e5862481f /sample.bam
Start analysing BAM /sample.bam
[/sample.bam]
1 BAMs
Warning: can't find RG tag in the BAM header
Warning: treat all reads in BAM as if they were from a same sample
[scan] total reads in BAM scanned 1
Completed scanning BAM
ReadGroup	Library	Sample	Total	Mapped	Duplicates	LENGTH_ESTIMATE	TEL0	TEL1	TEL2	TEL3	TEL4	TELTEL6	TEL7	TEL8	TEL9	TEL10	TEL11	TEL12	TEL13	TEL14	TEL15	TEL16	GC0	GC1	GC2	GC3	GC4GC5	GC6	GC7	GC8	GC9	
UNKNOWN	UNKNOWN	UNKNOWN	1	1	0	UNKNOWN	1	0	0	0	0	0	0	0	0	0
Telomere length estimate unknown. No read was found with telomeric GC composition.
Completed writing results
[timer - scan BAM] wall clock: 0.00s CPU: 0.00s
```

Note that `-v` stands for "volume", because Docker is mounting the file
`/path/to/bam/sample.bam` from the host environment to `sample.bam` in the VM's
file system so that the code running in the VM can access it.
