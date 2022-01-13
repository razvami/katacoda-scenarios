Create the Chart: ``helm create mychart``

Cleanup all the unnecessary files
```
rm -r mychart/charts \ 
rm -r mychart/templates/tests \
rm mychart/templates/*yaml
```

Copy the following Deployment definition to the editor in *manifest.yaml* file.
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
 name: hello-deploy
spec:
 replicas: 1
 selector:
   matchLabels:
     app: webapp1
 template:
   metadata:
     labels:
       app: webapp1
   spec:
     containers:
     - name: webapp1
       image: razm/web-app:{{ .Chart.AppVersion }}.0
       ports:
       - containerPort: 8080
```
Create *deployment.yaml* file based on the manifest.yaml
``mv manifest.yaml mychart/templates/deployment.yaml``

Copy the service definition from step 2 to the editor in *manifest.yaml* file.

Create *service.yaml* file based on the manifest.yaml
``mv manifest.yaml mychart/templates/service.yaml``

Run helm install command: ``helm install mychart ./mychart``

To Check the status of the helm chart: ``helm list``

To check all the Kubernetes objects created by Helm run: ``kubectl get all``


Test the endpoint: ``curl host01:31111``