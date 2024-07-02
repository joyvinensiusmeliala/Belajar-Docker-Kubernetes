![Kubernetes setup Logo](images/logo.png) 

[![OS Ubuntu Download](https://img.shields.io/badge/ubuntu-v.22.04TLS-blue?style=flat)](https://releases.ubuntu.com/jammy/)
[![Docker ce Install Version](https://img.shields.io/badge/docker.ce-ubuntu-red?style=flat)](https://docs.docker.com/engine/install/ubuntu/)
[![Minikube Github Releases](https://img.shields.io/badge/minikube-installation-green?style=flat)](https://minikube.sigs.k8s.io/docs/)
[![OpenSSF Scorecard](https://api.securityscorecards.dev/projects/github.com/kubernetes/minikube/badge)](https://api.securityscorecards.dev/projects/github.com/kubernetes/minikube)
[![GitHub All Releases](https://img.shields.io/github/downloads/kubernetes/minikube/total.svg)](https://github.com/kubernetes/minikube/releases/latest)
[![Latest Release](https://img.shields.io/github/v/release/kubernetes/minikube?include_prereleases)](https://github.com/kubernetes/minikube/releases/latest)
[![OpenSSF Best Practices](https://www.bestpractices.dev/projects/5015/badge)](https://www.bestpractices.dev/en/projects/5015)
 
# Setup Kubernetes kubectl and Minikube on Ubuntu 22.04 LTS

#### Syarat Kebutuhan Minimum

##### CPU:
- **Minimum:** 2 core CPU
- **Disarankan:** 4 core CPU atau lebih

##### RAM:
- **Minimum:** 2 GB RAM
- **Disarankan:** 4 GB RAM atau lebih

##### Penyimpanan:
- **Minimum:** 20 GB penyimpanan kosong
- **Disarankan:** 40 GB penyimpanan kosong atau lebih

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
sudo cp /home/admin-minikube/minikube-linux-amd64 /usr/local/bin
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

![Deskripsi Gambar](images/m-version.png)

#### 3. Beri file tersebut izin eksekutif menggunakan perintah chmod:

```sh
sudo chmod 755 /usr/local/bin/minikube-linux-amd64
```

#### 4. Verifikasi bahwa Anda telah berhasil menginstal Minikube dengan memeriksa versi perangkat lunaknya:

```sh
minikube version
``` 

![Deskripsi Gambar](images/m-version.png)

## Install kubectl

### Langkah 1: Unduh kubectl

##### - Unduh binary kubectl dengan curl:

```sh
sudo curl -LO "https://dl.k8s.io/release/$(curl -Ls https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```

![Deskripsi Gambar](images/kube.png)

##### Perintah ini akan mengunduh binary kubectl terbaru sesuai dengan versi stabil Kubernetes untuk arsitektur AMD64.

### Langkah 2: Instalasi kubectl

##### - Pindahkan binary kubectl ke direktori /usr/local/bin/ dan beri izin eksekutif:

```sh
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```

##### Perintah ini akan mengunduh binary kubectl terbaru sesuai dengan versi stabil Kubernetes untuk arsitektur AMD64.

### Langkah 3: Verifikasi instalasi

##### - Verifikasi instalasi kubectl dengan memeriksa versi:

```sh
kubectl version
```

![Deskripsi Gambar](images/k-version.png)

##### Perintah di atas akan menampilkan versi kubectl yang diinstal. Jika instalasi berhasil, Anda seharusnya melihat output yang mencantumkan versi kubectl yang telah diinstal.

## Starting Minikube with Docker Driver

#### Sekarang kita akan memulai sebuah cluster Minikube menggunakan driver Docker. Berikut langkah-langkahnya:

### Langkah 1: Tambahkan pengguna Anda ke grup 'docker':

##### Jalankan perintah berikut untuk menambahkan pengguna Anda ke grup 'docker':

```sh
sudo usermod -aG docker $USER 
```

### Langkah 2: Penerapan perubahan group:

##### Jalankan newgrp docker untuk menerapkan perubahan grup tanpa logout:

```sh
newgrp docker 
```

### Langkah 3: Mulai Minikube dengan Docker Driver:

```sh
minikube start --driver=docker
```
![Deskripsi Gambar](images/mkube-start.png) 

##### Perintah di atas akan memulai Minikube dengan menggunakan Docker sebagai driver untuk menjalankan node Kubernetes di dalam container Docker.
##### Pastikan Docker sudah terinstal dan berjalan di sistem Anda sebelum memulai Minikube.

### Langkah 2: Verifikasi Status Minikube:

```sh
minikube verison
```

##### Perintah ini akan memberikan informasi tentang status dan konfigurasi dari cluster Minikube yang sedang berjalan.

![Deskripsi Gambar](images/mkube-version.png) 