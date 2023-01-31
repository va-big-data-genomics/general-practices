1. Download the telseq Docker file:
```
wget https://raw.githubusercontent.com/zd1/telseq/master/Dockerfile
```
2. Build the image ([how to](build-an-image-from-a-dockerfile.md)):
```
docker build .
```
3. Rename the image to something more descriptive ([how to](rename-an-image.md)):
```
docker tag 1c5f861dec75 dlcott2/telseq
```
4. Run telseq in the container to test that it works ([how to](run-the-container.md)):
Note: Replace `test.bam` with the BAM file you intend to analyze:
```
docker run -v test.bam:/sample.bam 1c5f861dec75 /sample.bam
```
5. Add the container registry prefix to the image name ([how to](rename-an-image.md#renaming-in-preparation-for-pushing-to-container-registry)):
```
docker tag 1c5f861dec75 gcr.io/my-cloud-project/telseq
```
6. Authenticate Docker with Google's container registry ([how to](authenticate-docker-with-a-container-registry.md)):
```
gcloud auth configure-docker
```
7. Push the image to Google's container registry ([how to](push-the-image-to-a-container-registry.md)):
```
docker push gcr.io/my-cloud-project/telseq
```
8. Create a GCP Compute VM from the image from the cloud console ([how to](create-a-gcp-compute-vm-from-an-image-on-a-container.md)).

(optionally): SSH into the new VM (don't forget to connect to Stanford's VPN):
```
gcloud compute ssh my-cloud-vm
```
