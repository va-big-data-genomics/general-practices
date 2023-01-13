From the console:

1. Go to: [GCP Console](https://console.cloud.google.com)
2. From the navigation menu at the top of the left sidebar: [View all products](https://console.cloud.google.com/products) -> [Artificial Intelligence](https://console.cloud.google.com/products#artificial-intelligence) -> [Vertex AI](https://console.cloud.google.com/vertex-ai) ([docs](https://cloud.google.com/vertex-ai/docs)) – pin this so you can easily find it again
4. From the sidebar: Tools -> [Workbench](https://console.cloud.google.com/vertex-ai/workbench/list/managed)
5. From the menu at the top, click New Notebook and choose a basic programming environment (Python, R, etc.). In the dialog that opens, give the notebook a unique name and pick an appropriate region and zone. Click "Advanced Options" to choose operating system, machine type, disk size, memory size, etc. I used us-west1-b, Ubuntu 20.04, and an n1-highmem-4 machine, for example.
6. Once created, click **OPEN JUPYTERLAB** next to the notebook.
7. Update the system by running:
	```
	sudo apt update && sudo apt upgrade
	```