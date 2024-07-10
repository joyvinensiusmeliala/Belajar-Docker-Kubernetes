### Membuat Namespacek pada POD

### Langkah 1: Persiapan File YAML:

##### Pertama, anda dapat membuat direktori kerja dan beralih ke direktori tersebut:

```sh
mkdir ~/example
cd ~/example
``` 

##### Kemudian, anda membuat file konfigurasi YAML untuk Pod Nginx:

```sh
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
