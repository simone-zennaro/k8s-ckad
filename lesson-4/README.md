# 4th: secrets, volumes and environment variables

## Secrets
1) minikube start
2) deploy deployment: kubectl apply -f deployment
3) deploy secret: kubectl apply -f secret
4) Create secret without yaml: kubectl create secret generic mysecondsecret --from-literal=password=my_great_team
5) attach secret as volume: kubectl apply -f secret_as_volume
6) get inside the pod: kubectl exec -ti nginx-with-secret-volume-55b5ff678d-bsls2 -- sh
7) check mounted volumes: mount | grep -i something
8) check folder: ls -l /something
9) check your secret: cat /something/password
10) secret as env var: kubectl apply -f secret_as_env_var
11) get inside the pod: kubectl exec -ti nginx-with-secret-env-54fc4d5586-q87qp -- sh
12) verify env var: env | grep my_secret

## Persistant volumes
1) Verify storage classes available in your cluster: kubectl get sc
2) deploy a persistant volume claim: kubectl apply -f pvc
3) check the pvc: kubectl get pvc
4) use the PVC in a deployment: kubectl apply -f volumes/dep_with_pvc
