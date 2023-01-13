I get an error when I try to push this image to Google Container Registry using `docker push gcr.io/gbsc-gcp-project-mvp-dev/telseq`, which makes sense, because it is a private project and I haven't authenticated Docker. The `gcloud` CLI tells me `gcloud docker` is deprecated and I should use `gcloud auth configure-docker`:

```
tmp/telomere-test-1-dlc % gcloud auth configure-docker
Adding credentials for all GCR repositories.
WARNING: A long list of credential helpers may cause delays running 'docker build'. We recommend passing the registry name to configure only the registry you are using.
After update, the following will be written to your Docker config file located at [/Users/dlcott2/.docker/config.json]:
 {
  "credHelpers": {
    "gcr.io": "gcloud",
    "us.gcr.io": "gcloud",
    "eu.gcr.io": "gcloud",
    "asia.gcr.io": "gcloud",
    "staging-k8s.gcr.io": "gcloud",
    "marketplace.gcr.io": "gcloud"
  }
}

Do you want to continue (Y/n)?  

Docker configuration file updated.
```
