Copy the following Pod definition to the editor in *pod.yaml* file.
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

Create the pod with the following command: ``kubectl create -f pod.yaml``

Check the status of the pod: ``kubectl get pod webapp1``

Check the details of the pod: ``kubectl describe pod webapp1``