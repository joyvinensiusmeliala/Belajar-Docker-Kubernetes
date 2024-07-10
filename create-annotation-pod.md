### Membuat Annotation pada POD

### Langkah 1: Persiapan File YAML:

##### Pertama, anda dapat membuat direktori kerja dan beralih ke direktori tersebut:

```sh
mkdir ~/nginx
cd ~/nginx
``` 

##### Kemudian, anda membuat file konfigurasi YAML untuk Pod Nginx:

```sh
nano nginx-with-annotation.yaml
``` 

##### Isi dari file `nginx-with-annotation.yaml` adalah sebagai berikut:

```sh
apiVersion: v1
kind: Pod
metadata:
  name: nginx-with-annotation
  labels:
    team: frontend
    version: "1.0"
    environment: production
  annotations:
    description: Aplikasi Tim Product
    penjelasan: production untuk product 
spec:
  containers:
    - name: nginx-container
      image: nginx
      ports:
        - containerPort: 80
```

## Langkah 2: Membuat Pod dari File YAML

##### Selanjutnya, saya membuat Pod berdasarkan konfigurasi YAML yang telah dibuat:

```sh
kubectl create -f nginx-with-annotation.yaml
``` 

### Langkah 3: Mengecek Status Pod

##### Setelah Pod dibuat, saya mengecek statusnya untuk memastikan bahwa Pod sudah berjalan dengan baik:

```sh
kubectl get pods --show-labels
``` 

##### Untuk melihat detail Annotation pada POD

```sh
kubectl describe pod nginx-with-annotation
``` 


### Langkah 4: Membuat Annotation pada POD secara manual

```sh
kubectl annotate pod <nama_pod> <annotate>
kubectl annotate pod nginx-with-label description="ini adalah aplikasi tim finance"
``` 

##### update label

```sh
kubectl annotate pod <nama_pod> <annotate> --overwrite
kubectl annotate pod nginx description="ini adalah aplikasi tim finance" --overwrite
``` 

##### Untuk melihat detail Annotation pada POD

```sh
kubectl describe pod nginx
``` 