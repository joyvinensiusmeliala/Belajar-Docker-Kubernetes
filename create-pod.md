# Membuat Deployment dan Pod di Kubernetes dengan Minikube


### Langkah 1: Membuat Deployment

##### anda dapat membuat POD pada kubernetes menggunakan command dibawah ini 

```sh
kubectl create deployment nginx --image=nginx
``` 

![Deskripsi Gambar](images/create-pod.png)

##### Setelah deployment dibuat, saya mengecek status deployment tersebut:

```sh
kubectl get deployment
``` 

![Deskripsi Gambar](images/k-get-deploy.png)

##### Hasilnya menunjukkan bahwa deployment sudah berhasil dibuat, tetapi pod masih dalam status ContainerCreating.

### Langkah 2: Mengecek Status Pod

##### Saya mengecek status pod yang baru saja dibuat menggunakan perintah:

```sh
kubectl get pod
``` 

![Deskripsi Gambar](images/k-get-pod.png)

### Langkah 3: Expose Deployment sebagai Service

#### Langkah berikutnya adalah mengekspos deployment sebagai sebuah service yang bisa diakses dari luar kluster Kubernetes:

```sh
kubectl expose deployment nginx --type=NodePort --port=80
``` 

![Deskripsi Gambar](images/k-expose.png)
