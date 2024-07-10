### Membuat Repication Set pada POD

### Langkah 1: Persiapan File YAML:

##### Pertama, anda dapat membuat direktori kerja dan beralih ke direktori tersebut:

```sh
mkdir ~/example
cd ~/example
``` 

##### Kemudian, anda membuat file konfigurasi YAML untuk Pod Nginx:

```sh
nano nginx-rs.yaml
``` 

##### Isi dari file `nginx-rs.yaml` adalah sebagai berikut:

```sh
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: nginx-rs
spec:
  replicas: 3
  selector:
    matchExpressions:
      - key: app
        operator: In
        values:
          - nginx
      - key: env
        operator: In
        values:
          - prod
          - sit
          - uat
  template:
    metadata:
      name: nginx-pod
      labels:
        app: nginx
        env: prod
    spec:
      containers:
      - name: nginx
        image: nginx
        ports:
        - containerPort: 80
```

## Langkah 2: Membuat Replica Set dari File YAML

##### Selanjutnya, saya membuat Pod berdasarkan konfigurasi YAML yang telah dibuat:

```sh
kubectl create -f nginx-rs-match-expression.yaml
``` 

### Langkah 3: Mengecek Status Replica set

##### Setelah Pod dibuat, saya mengecek statusnya untuk memastikan bahwa Pod sudah berjalan dengan baik:

```sh
kubectl get pods
kubectl get replicaset 
kubectl get pods --selector=app=nginx
kubectl get pods --show-labels
``` 

### Menghapus Replica Set 

```sh
kubectl delete rs nginx-rs --cascade=orphan
```

