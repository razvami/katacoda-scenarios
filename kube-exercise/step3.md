Check the rollout history of your deploy with the following command:``kubectl rollout history deploy web-deploy``

Rollout to the previous version: ``kubectl rollout undo deploy web-deploy --to-revision=1

You can see live how new pods are beeing created and old ones terminated one by one using this command:
``kubectl get pods --watch``

To check the status of the deploy rollback open a new terminal and run the following command: ``kubectl rollout status deploy web-deploy``