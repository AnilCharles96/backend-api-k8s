# Backend API 

### Apply manifests 
```
kubectl apply -f k8-manifests/deploy.yml
```
### Check if pods are running
```
kubectl get pods -l=app=helloworld
```

### Test if pod outputs hello world
```
kubectl run helloworld-test --image=curlimages/curl:latest --restart=Never --rm -it -- curl http://helloworld

# output 
<html><head><title>HTTP Hello World</title></head><body><h1>Hello from helloworld-77ccf9b964-m54pg</h1></body></html
```

# Cronjob that print "Hello SRE"

### Apply manifest 
```
kubectl apply -f k8s-manifests/cronjob.yml
```

### Check status after 30 min
```
# check status
kubectl get pods -l=app=hello-sre

# Get most recent pod
POD_NAME=$(kubectl get pods -l=app=hello-sre --sort-by=.metadata.creationTimestamp -o jsonpath='{.items[-1].metadata.name}')

# Check if pod name is set
echo $POD_NAME

# Check if pod output "Hello SRE"
kubectl logs $POD_NAME
```




