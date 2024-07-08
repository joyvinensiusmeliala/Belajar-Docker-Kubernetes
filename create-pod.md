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

![Deskripsi Gambar](images/create-pod.png)

##### Hasilnya menunjukkan bahwa deployment sudah berhasil dibuat, tetapi pod masih dalam status ContainerCreating.