Copy the following Deployment definition to the editor in *manifest.yaml* file.
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: web-deploy
  labels:
    app: web
spec:
  replicas: 5
  selector:
    matchLabels:
      app: web
  template:
    metadata:
      labels:
        app: web
    spec: 
      terminationGracePeriodSeconds: 1
      containers:
      - name: hello-pod
        image: razm/web-app:1.0
        ports:
        - containerPort: 8080
```
Create the Deployment with the following command: ``kubectl apply -f manifest.yaml``

Check the status of the Deployment: ``kubectl get deployment web-deploy``

Check the details of the Deployment: ``kubectl describe deployment web-deploy``