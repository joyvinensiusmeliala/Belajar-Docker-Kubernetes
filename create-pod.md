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

##### Langkah berikutnya adalah mengekspos deployment sebagai sebuah service yang bisa diakses dari luar kluster Kubernetes:

```sh
kubectl expose deployment nginx --type=NodePort --port=80
``` 

![Deskripsi Gambar](images/k-expose.png)

##### Saya kemudian mengecek daftar service yang tersedia untuk memastikan service tersebut sudah terdaftar:

```sh
kubectl get services
```

![Deskripsi Gambar](images/k-get-service.png)

### Langkah 4: Mengakses Service

##### Terakhir, saya menggunakan Minikube untuk mendapatkan URL yang bisa digunakan untuk mengakses service Nginx:

```sh
minikube service nginx --url
```

![Deskripsi Gambar](images/m-service-nginx.png)

##### Hasilnya adalah URL yang bisa saya gunakan untuk mengakses server Nginx dari browser atau alat lain:

```sh
http://192.168.49.2:31727
```

![Service NGINX URL](images/nginx.jpg)

### Langkah 5: Menghapus Service dan Deployment

##### Setelah selesai menguji, saya menghapus service dan deployment yang telah dibuat untuk menjaga lingkungan tetap bersih. Langkah pertama adalah menghapus service:

```sh
kubectl delete service nginx
```

![Delete Service NGINX](images/k-delete-s-nginx.png)

##### Lalu, saya mengecek daftar service untuk memastikan service tersebut telah dihapus:

```sh
kubectl get service
```

![Delete Service NGINX](images/k-get-s-nginx.png)

##### Kemudian, saya menghapus deployment:

```sh
kubectl delete deployment nginx
```

![Delete Service NGINX](images/delete-deployment.png)

##### Dan mengecek kembali daftar deployment untuk memastikan tidak ada resource yang tersisa:

```sh
kubectl get deployment
```

![Delete Service NGINX](images/get-deployment.png)


##### Demikian langkah-langkah untuk membuat, mengakses, dan menghapus deployment serta service di Kubernetes menggunakan Minikube. Ini adalah dasar yang baik untuk memulai eksplorasi lebih lanjut dalam dunia orkestrasi container. Saya harap ini bisa membantu teman-teman yang baru memulai dengan Kubernetes!

##### #Kubernetes #Minikube #DevOps #ContainerOrchestration #Nginx #CloudComputing