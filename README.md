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

## Install Docker 

### Setup Repository 

#### 1. Perbarui indeks paket apt dan instal paket-paket yang memungkinkan apt menggunakan repositori melalui HTTPS:

```sh
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
```

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