Edit the Chart.yaml file and change the appVersion property value to 2

Run the upgrade command: ``helm upgrade mychart ./mychart``

To Check the status of the helm chart: ``helm list``

To check all the Kubernetes objects created by Helm run: ``kubectl get all``

Test the endpoint: ``curl host01:31111``

Run the rollback command and check again: ``helm rollback mychart``