# Membuat Services


##### execute app

```sh
kubectl exec -it curl -- /bin/sh
```

```sh
curl http://10.105.246.95:8080
```

### Mengakses Service

```sh
kubectl exec -it curl -- /bin/sh
env
env | grep NGINX_SERVICE
```

### Mengakses Menggunakan DNS

```sh
nama-service.nama-namespace.svc.cluster.local
curl http://nginx-service.default.svc.cluster.local:8080
```

### Melihat Endpoints

```sh
kubectl get endpoints
```

### Melihat Service Endpoints

```sh
kubectl describe service namaservice
kubectl get endpoints nama service
```