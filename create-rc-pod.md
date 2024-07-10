### Membuat Repication Controller pada POD

### Langkah 1: Persiapan File YAML:

##### Pertama, anda dapat membuat direktori kerja dan beralih ke direktori tersebut:

```sh
mkdir ~/nginx
cd ~/nginx
``` 

##### Kemudian, anda membuat file konfigurasi YAML untuk Pod Nginx:

```sh
nano nginx-rc.yaml
``` 

##### Isi dari file `nginx-rc.yaml` adalah sebagai berikut:

```sh
apiVersion: v1
kind: ReplicationController
metadata:
  name: nginx-rc
spec:
  replicas: 3
  selector:
    app: nginx-finance
  template:
    metadata:
      name: pod-nginx-finance
      labels:
        app: nginx-finance
    spec:
      containers:
        - name: nginx
          image: nginx
          ports:
            - containerPort: 80
```

## Langkah 2: Membuat Pod dari File YAML

##### Selanjutnya, saya membuat Pod berdasarkan konfigurasi YAML yang telah dibuat:

```sh
kubectl create -f nginx-rc.yaml
``` 

### Langkah 3: Mengecek Status Pod

##### Setelah Pod dibuat, saya mengecek statusnya untuk memastikan bahwa Pod sudah berjalan dengan baik:

```sh
kubectl get pods 
``` 
