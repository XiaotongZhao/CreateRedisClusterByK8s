kubectl create ns redis
kubectl get ns


kubectl apply -f sc.yaml
kubectl get sc

kubectl apply -f pv.yaml
kubectl get pv

kubectl apply -n redis -f redis-config.yaml
kubectl get configmap -n redis

kubectl apply -n redis -f redis-statefulset.yaml
kubectl get pods -n redis

kubectl apply -n redis -f redis-service.yaml
kubectl get service -n redis

------Test  redis cluster-------

kubectl -n redis logs redis-0
kubectl -n redis describe pod redis-0


kubectl -n redis exec -it redis-0 -- sh
redis-cli 
auth a-very-complex-password-here
info replication



kubectl -n redis exec -it redis-1 -- sh
redis-cli 
auth a-very-complex-password-here
info replication



kubectl -n redis exec -it redis-0 -- sh
redis-cli 
auth a-very-complex-password-here

SET emp1 raja
SET emp2 mano
SET emp3 ram
KEYS *

kubectl -n redis exec -it redis-1 -- sh
redis-cli 
auth a-very-complex-password-here

SET emp1 raja
SET emp2 mano
SET emp3 ram
KEYS *