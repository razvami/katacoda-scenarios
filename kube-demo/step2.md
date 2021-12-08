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
       image: razm/web-app:1.0
       ports:
       - containerPort: 8080
```

Create the Deployment with the following command: ``kubectl apply -f manifest.yaml``

Check the status of the Deployment: ``kubectl get deployment hello-deploy``

Check the details of the Deployment: ``kubectl describe deployment hello-deploy``