Execute the command `docker build .` in the directory containing the `Dockerfile`:

```
% docker build .         
[+] Building 97.0s (9/9) FINISHED                                                                                           
 => [internal] load build definition from Dockerfile                                                                   0.0s
 => => transferring dockerfile: 1.19kB                                                                                 0.0s
 => [internal] load .dockerignore                                                                                      0.0s
 => => transferring context: 2B                                                                                        0.0s
 => [internal] load metadata for docker.io/library/ubuntu:14.04                                                        1.8s
 => [1/5] FROM docker.io/library/ubuntu:14.04@sha256:64483f3496c1373bfd55348e88694d1c4d0c9b660dee6bfef5e12f43b9933b30  0.0s
 => CACHED [2/5] WORKDIR /tmp                                                                                          0.0s
 => [3/5] RUN apt-get update &&     apt-get install -y         automake         autotools-dev         build-essentia  44.0s
 => [4/5] RUN mkdir -p /deps &&     cd /deps &&     wget https://github.com/pezmaster31/bamtools/archive/v2.4.1.tar.  44.0s
 => [5/5] RUN mkdir -p /src &&     cd /src &&     wget https://github.com/zd1/telseq/archive/v0.0.1.tar.gz &&     tar  5.6s 
 => exporting to image                                                                                                 1.5s 
 => => exporting layers                                                                                                1.4s 
 => => writing image sha256:1c5f861dec75d321d36c06c63be5259b1ec22b560f897c9e556e54f34837e4d9
```

Notice the image ID `1c5f861dec75...` – it will be important later.
