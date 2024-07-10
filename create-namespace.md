### Membuat Namespace pada POD

### Membuat Namespacek pada POD

### Langkah 1: Persiapan File YAML:

##### Pertama, anda dapat membuat direktori kerja dan beralih ke direktori tersebut:

```sh
mkdir ~/nginx
cd ~/nginx
mkdir ~/example
cd ~/example
``` 

##### Kemudian, anda membuat file konfigurasi YAML untuk Pod Nginx:

```sh
nano finance-namespace.yaml
``` 

##### Isi dari file `finance-namespace.yaml` adalah sebagai berikut:

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
=======
nano finance-namespace.yaml 
``` 

##### Isi dari file `finance-namespace.yaml ` adalah sebagai berikut:

```sh
apiVersion: v1
kind: Namespac/.e
metadata:
  name: finance
```

## Langkah 2: Membuat Pod di Namespace

##### Selanjutnya, saya membuat Pod di Namespace :

```sh
kubectl create -f namafile.yaml --namespace nama_namespace
kubectl create -f nginx.yaml --namespace finance
``` 

### Langkah 3: Mengecek Namespace pada satu Pod

##### Setelah Namespace pada Pod dibuat, saya mengecek statusnya untuk memastikan bahwa Pod sudah berada dalam Namespace dengan baik:

```sh
kubectl get pod --namespace default
kubectl get pod --namespace finance
``` 

### Delete Namespace. 

```sh
kubectl delete namespace finance
```
>>>>>>> 8d200d3c9e3290ae5400fd450346cd6f5a988704
