<h1>Minio Object Deployment through Kubernetes:</h1>
<br>
MinIO is an object storage solution that provides an Amazon Web Services S3-compatible API and supports all core S3 features. MinIO is built to deploy anywhere - public or private cloud, baremetal infrastructure, orchestrated environments, and edge infrastructure.<br><br>

<h2>1.Download minio-dev.yaml to your host machine by following command on Terminal</h2>

curl https://raw.githubusercontent.com/minio/docs/master/source/extra/examples/minio-dev.yaml -O<br>

<h2>2.Apply the MinIO Object Definition:</h2>
<br>
kubectl apply -f minio-dev.yaml<br>
kubectl get pods -n minio-dev<br>
kubectl describe pod/minio -n minio-dev<br>

<h2>3.Temporarily Access the MinIO S3 API and Console</h2><br>

kubectl port-forward pod/minio 9000 9090 -n minio-dev<br>

he command forwards the pod ports 9000 and 9090 to the matching port on the local machine while active in the shell. The kubectl port-forward command only functions while active in the shell session. Terminating the session closes the ports on the local machine.<br>

<h2>4.Connect your Browser to the MinIO Server</h2><br>
<br>
Access the MinIO Console by opening a browser on the local machine and navigating to http://127.0.0.1:9001.

Log in to the Console with the credentials minioadmin | minioadmin. These are the default root user credentials.<br>

<h2>5.(Optional) Connect the MinIO Client</h2><br>

If your local machine has mc installed, use the mc alias set command to authenticate and connect to the MinIO deployment:

mc alias set k8s-minio-dev http://127.0.0.1:9000 minioadmin minioadmin
mc admin info k8s-minio-dev

-The name of the alias
-The hostname or IP address and port of the MinIO server
-The Access Key for a MinIO user
-The Secret Key for a MinIO user
