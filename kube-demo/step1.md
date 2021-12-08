Copy the following Pod definition to the editor in *manifest.yaml* file.
```yaml
apiVersion: v1
kind: Pod
metadata:
 name: hello-pod
 labels:
   app: webapp1
spec:
 containers:
   - name: webapp1
     image: razm/web-app:1.0
     ports:
       - containerPort: 8080
```

Create the pod with the following command: ``kubectl apply -f manifest.yaml``

Check the status of the pod: ``kubectl get pod hello-pod``

Check the details of the pod: ``kubectl describe pod hello-pod``