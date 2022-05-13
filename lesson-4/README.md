# 4th: secrets, volumes and environment variables

## Secrets
1) minikube start
2) deploy deployment: kubectl apply -f deployment
3) deploy secret
  3.1) kubectl apply -f secret
  3.2) kubectl create secret generic mysecondsecret --from-literal=password=my_great_team
4) attach secret as volume;: kubectl apply -f secret_as_volume
  4.1) get inside the pod: kubectl exec -ti nginx-with-secret-volume-55b5ff678d-bsls2 -- sh
  4.2) check mounted: mount | grep -i something
  4.3) check folder: ls -l /something
  4.4) check your secret: cat /something/password
5) secret as env var: kubectl apply -f secret_as_env_var
  5.1) get inside the pod: kubectl exec -ti nginx-with-secret-env-54fc4d5586-q87qp -- sh
  5.2) verify env var: env | grep my_secret

## Persistant volumes
1) Verify storage classes available in your cluster: kubectl get sc
2) deploy a persistant volume claim: kubectl apply -f pvc
3) check the pvc: kubectl get pvc
4) use the PVC in a deployment: kubectl apply -f volumes/dep_with_pvc
