# Belajar-Kubernetes

##### Sebelum menginstal perangkat lunak apa pun, Anda perlu memperbarui dan meningkatkan sistem yang Anda gunakan. Untuk melakukannya, jalankan perintah berikut:

```sh
sudo apt-get update -y
sudo apt-get upgrade -y
```

##### Pastikan juga untuk menginstal (atau memeriksa apakah Anda sudah memiliki) paket-paket yang diperlukan berikut ini:

```sh
sudo apt-get install curl
sudo apt-get install apt-transport-https
```

## Install Menggunakan `apt` repository

##### Sebelum Anda menginstal Docker Engine untuk pertama kalinya pada mesin baru, Anda perlu mengatur repositori Docker. Setelah itu, Anda dapat menginstal dan memperbarui Docker dari repositori tersebut.

### Setup Repository 

#### 1. Perbarui indeks paket apt dan instal paket-paket yang memungkinkan apt menggunakan repositori melalui HTTPS:

```sh
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
```
![Deskripsi Gambar](images/ss_ca-cert.png)

#### 2. Tambahkan kunci GPG resmi Docker:

```sh
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```

#### 3. Gunakan perintah berikut untuk mengatur repositori:

```sh
echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
$(. /etc/os-release && echo $VERSION_CODENAME) stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

## Install Docker Engine

#### 1. Perbarui indeks paket apt:

```sh
sudo apt-get update
```

#### 2. Instal Docker Engine, containerd, dan Docker Compose:

```sh
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

#### 3. Verifikasi bahwa instalasi Docker Engine berhasil dengan menjalankan gambar hello-world:

```sh
sudo docker run hello-world
```

![Deskripsi Gambar](images/h-world.png)

## Install Docker Engine

#### 1. Unduh binary Minikube terbaru menggunakan perintah wget:

```sh
wget https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 -P ~/
```

#### 2. Salin file yang diunduh dan simpan ke direktori /usr/local/bin/minikube:

```sh
sudo cp minikube-linux-amd64 /usr/local/bin/minikube
```

#### 3. Beri file tersebut izin eksekutif menggunakan perintah chmod:

```sh
sudo chmod 755 /usr/local/bin/minikube
```

#### 4. Verifikasi bahwa Anda telah berhasil menginstal Minikube dengan memeriksa versi perangkat lunaknya:

```sh
minikube version
``` 
