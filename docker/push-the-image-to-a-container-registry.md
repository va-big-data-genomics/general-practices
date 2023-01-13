```
tmp/telomere-test-1-dlc % docker push gcr.io/gbsc-gcp-project-mvp-dev/telseq
Using default tag: latest
The push refers to repository [gcr.io/gbsc-gcp-project-mvp-dev/telseq]
e6229561f8af: Pushed 
82a84a8dd1a6: Pushed 
da2b49324e40: Pushed 
5f70bf18a086: Pushed 
83109fa660b2: Layer already exists 
30d3c4334a23: Layer already exists 
f2fa9f4cf8fd: Layer already exists 
latest: digest: sha256:ee47256f94a0b1eb3ebc7174f98ee96528a87a1ce2a39eb633e2dc23d256f1bb size: 1785
```

And that does it. Now the image is [there](https://console.cloud.google.com/gcr/images/gbsc-gcp-project-mvp-dev/global/telseq?project=gbsc-gcp-project-mvp-dev).
