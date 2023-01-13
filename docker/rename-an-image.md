### Renaming an image
Notice that a newly built image may not have a descriptive name (field `repository`):

```
tmp/telomere-test-1-dlc % docker image ls
REPOSITORY               TAG       IMAGE ID       CREATED          SIZE
<none>                   <none>    1c5f861dec75   57 minutes ago   435MB
docker/getting-started   latest    083d7564d904   18 months ago    28MB
```

In order to give it a descriptive name, we use the command `docker tag <image_id> <user/repo>`.:

```
tmp/telomere-test-1-dlc % docker tag 1c5f861dec75 dlcott2/telseq
```

Now it has a descriptive name, rather than just a meaningless image ID. I don't know whether the naming format I used is a hard and fast rule or just a convention. And I find it confusing that the `tag` command actually changes the `repository` field to whatever name you give it, but the `tag` field is set to `latest`.

```
tmp/telomere-test-1-dlc % docker image ls
REPOSITORY               TAG       IMAGE ID       CREATED             SIZE
dlcott2/telseq           latest    1c5f861dec75   About an hour ago   435MB
docker/getting-started   latest    083d7564d904   18 months ago       28MB
```

### Renaming in preparation for pushing to container registry
In order to push an image to a registry, the image name must be prefixed with the corresponding registry. I haven't seen an explanation why. The naming convention seems to be `<container_registry>/<project_name>/<image_name>`.

```
tmp/telomere-test-1-dlc % docker tag dlcott2/telseq gcr.io/gbsc-gcp-project-mvp-dev/telseq
tmp/telomere-test-1-dlc % docker image ls
REPOSITORY                               TAG       IMAGE ID       CREATED             SIZE
dlcott2/telseq                           latest    1c5f861dec75   About an hour ago   435MB
gcr.io/gbsc-gcp-project-mvp-dev/telseq   latest    1c5f861dec75   About an hour ago   435MB
docker/getting-started                   latest    083d7564d904   18 months ago       28MB
```

Notice it didn't seem to rename the image so much as create a second image with the new name. I don't understand why this is.
