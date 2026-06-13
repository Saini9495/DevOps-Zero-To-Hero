# Create Headless Service
kubectl apply -f headless-service.yml

# Create StatefulSet
kubectl apply -f statefulset.yml

# Check StatefulSets
kubectl get statefulsets

# Check Pods
kubectl get pods

# Check PVC
kubectl get pvc

# Check PV
kubectl get pv

# Describe StatefulSet
kubectl describe statefulset mysql

# Scale StatefulSet
kubectl scale statefulset mysql --replicas=5

# Delete StatefulSet
kubectl delete statefulset mysql

# Delete Service
kubectl delete service mysql