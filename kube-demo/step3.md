Copy the following Deployment definition to the editor in *manifest.yaml* file.
```yaml
apiVersion: v1
kind: Service
metadata:
 name: hello-svc
spec:
 type: NodePort
 selector:
   app: webapp1
 ports:
 - port: 80
   targetPort: 8080
   nodePort: 31111
```

Create the Service with the following command: ``kubectl apply -f manifest.yaml``

Check the status of the Service: ``kubectl get deployment hello-svc``

Check the details of the Service: ``kubectl describe svc hello-svc``

Test the endpoint: ``curl host01:31111``