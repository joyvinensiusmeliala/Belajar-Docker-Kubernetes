### Membuat Label pada POD

### Langkah 1: Persiapan File YAML:

##### Pertama, anda dapat membuat direktori kerja dan beralih ke direktori tersebut:

```sh
mkdir ~/nginx
cd ~/nginx
``` 

##### Kemudian, anda membuat file konfigurasi YAML untuk Pod Nginx:

```sh
nano nginx-with-label.yaml
``` 

##### Isi dari file `nginx-with-label.yaml` adalah sebagai berikut:

```sh
apiVersion: v1
kind: Pod
metadata:
  name: nginx-with-label
  labels:
    team: frontend
    version: "1.0"
    environment: production
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
kubectl create -f nginx-with-label.yaml
``` 

### Langkah 3: Mengecek Status Pod

##### Setelah Pod dibuat, saya mengecek statusnya untuk memastikan bahwa Pod sudah berjalan dengan baik:

```sh
kubectl get pods --show-labels
``` 

### Langkah 4: Membuat Label pada POD secara manual

```sh
kubectl label pod <nama_pod> <label>
kubectl label pod nginx environment=development
``` 

##### update label

```sh
kubectl label pod <nama_pod> <label> --overwrite
kubectl label pod nginx environment=development --overwrite
``` 
