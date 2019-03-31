vim k8s/client-deployment.yaml
vim k8s/lient-cluster-ip-service.yaml 

Zaibas-MacBook-Pro:complex Zaibu$ kubectl get deployments
NAME                READY   UP-TO-DATE   AVAILABLE   AGE
client-deployment   2/3     3            2           5s
Zaibas-MacBook-Pro:complex Zaibu$ kubectl get deployments
NAME                READY   UP-TO-DATE   AVAILABLE   AGE
client-deployment   3/3     3            3           11s
Zaibas-MacBook-Pro:complex Zaibu$ kubectl get pods
NAME                                 READY   STATUS    RESTARTS   AGE
client-deployment-549d66f468-2pxsn   1/1     Running   0          21s
client-deployment-549d66f468-56xmv   1/1     Running   0          21s
client-deployment-549d66f468-d2gzf   1/1     Running   0          21s
Zaibas-MacBook-Pro:complex Zaibu$ kubectl get services
NAME                        TYPE        CLUSTER-IP    EXTERNAL-IP   PORT(S)    AGE
client-cluster-ip-service   ClusterIP   10.99.30.90   <none>        3000/TCP   31s
kubernetes                  ClusterIP   10.96.0.1     <none>        443/TCP    33h

vim server-cluster-ip-service.yaml
vim worker-deployment.yaml
vim server-deployment.yaml

kubectl logs deployment.apps/server-deployment

kubectl get storageclass
kubectl describe storageclass

>>>
kubectl delete -f k8s

kubectl apply -f k8s

Zaibas-MacBook-Pro:complex Zaibu$ kubectl get pvc
NAME                               STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   AGE
database-persistent-volume-claim   Bound    pvc-09dc8475-5360-11e9-95d6-0800270280b6   2Gi        RWO            standard       2m2s
Zaibas-MacBook-Pro:complex Zaibu$ kubectl get pv
NAME                                       CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS   CLAIM                                      STORAGECLASS   REASON   AGE
pvc-09dc8475-5360-11e9-95d6-0800270280b6   2Gi        RWO            Delete           Bound    default/database-persistent-volume-claim   standard                2m6s
<<<

kubectl get pv -o=jsonpath='{.spec.hostPath.path}' pvc-09dc8475-5360-11e9-95d6-0800270280b6

kubectl create secret generic pgpassword --from-literal PGPASSWORD=12345asdf
kubectl get secrets

kubectl get secrets
kubectl get secrets pgpassword -o yaml


https://kubernetes.github.io/ingress-nginx/
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/master/deploy/mandatory.yaml
minikube addons enable ingress
