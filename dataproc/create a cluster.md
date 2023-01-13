From the GCP Console:
1. Go to: [GCP Console](https://console.cloud.google.com)
2. From the navigation menu at the top of the left sidebar: [View all products](https://console.cloud.google.com/products) -> [Analytics](https://console.cloud.google.com/products#analytics) -> [Dataproc](https://console.cloud.google.com/dataproc) ([docs](https://cloud.google.com/dataproc/docs)) – pin this so you can easily find it again
4. From the sidebar: Jobs on Clusters -> [Clusters](https://console.cloud.google.com/dataproc/clusters)
5. Click Create Cluster, then Cluster on Compute Engine. Follow the wizard, leaving the defaults in place if you don't have a reason to change them, and finish by clicking Create.

---

Alternatively, you can create clusters from the command line. The basic command is:
```
gcloud dataproc clusters create <cluster_name>
```

If it asks you if you'd like to enable the Dataproc API for your project, say Yes.