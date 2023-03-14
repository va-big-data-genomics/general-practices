### Renaming an image
Notice that a newly built image may not have a descriptive name (field `REPOSITORY`):

```
% docker image ls
REPOSITORY               TAG       IMAGE ID       CREATED          SIZE
<none>                   <none>    1c5f861dec75   57 minutes ago   435MB
docker/getting-started   latest    083d7564d904   18 months ago    28MB
```

In order to give it a descriptive name, we use the command `docker tag <image_id> <user/repo>`.:

```
% docker tag 1c5f861dec75 dlcotter/telseq
```

Now it has a descriptive name, rather than just an arbitrary image ID. The
naming convention I used is `<user>/<repo>`. It is a bit counterintuitive that
the `tag` command actually changes the `repository` field, whereas the `tag`
field is set to `latest`, but that's how it works.

```
% docker image ls
REPOSITORY               TAG       IMAGE ID       CREATED             SIZE
dlcotter/telseq          latest    1c5f861dec75   About an hour ago   435MB
docker/getting-started   latest    083d7564d904   18 months ago       28MB
```

### Renaming in preparation for pushing to container registry
In order to push an image to a registry, the image name must be prefixed with
the corresponding registry. The naming convention is
`<container_registry>/<project_name>/<image_name>`.

```
% docker tag dlcotter/telseq gcr.io/my-cloud-project/telseq
% docker image ls
REPOSITORY                       TAG       IMAGE ID       CREATED             SIZE
dlcotter/telseq                  latest    1c5f861dec75   About an hour ago   435MB
gcr.io/my-cloud-project/telseq   latest    1c5f861dec75   About an hour ago   435MB
docker/getting-started           latest    083d7564d904   18 months ago       28MB
```

Notice it didn't actually rename the image; rather, it created a second image
with the new name and the same ID.
