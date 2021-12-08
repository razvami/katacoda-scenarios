Copy the following Deployment definition to the editor in *manifest.yaml* file.
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: web-deploy
  labels:
    app: web
spec:
  selector:
    matchLabels:
      app: web
  replicas: 5
  minReadySeconds: 5
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 0
      maxSurge: 1
  template:
    metadata:
      labels:
        app: web
    spec: 
      terminationGracePeriodSeconds: 1
      containers:
      - name: hello-pod
        image: razm/web-app:2.0
        imagePullPolicy: Always
        ports:
        - containerPort: 8080
```

Run the rollout with the following command: ``kubectl apply -f manifest.yaml``

You can see live how new pods are beeing created and old ones terminated one by one using this command:
``kubectl get pods --watch``

To check the status of the deploy open a new terminal and run the following command: ``kubectl rollout status deploy web-deploy``

You can check the details on the new pods of the Deployment (with desribe command), they should all be running web-app:2.0 now