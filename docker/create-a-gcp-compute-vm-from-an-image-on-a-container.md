To create a GCP Compute VM from an image hosted on [Google Container Registry](https://cloud.google.com/container-registry/):
1. Go to the [Cloud Console](https://console.cloud.google.com)
2. Go to [Compute Engine](https://console.cloud.google.com/compute) from the navigation menu
3. Click [Create Instance](https://console.cloud.google.com/compute/instancesAdd?project=gbsc-gcp-project-mvp-dev)
   and provide a name for the instance.
4. Under the **Container** section, click **DEPLOY CONTAINER** and provide the
   URL to the image on Google Container Registry (should look like
   `gcr.io/my-cloud-project/telseq`). Click **Select** to save.
5. Change whatever other settings you need for your VM and click **Create**.
