# Update Minikube

Berikut adalah langkah-langkah untuk melakukan update Minikube ke versi terbaru.

## Langkah 1: Update Minikube Binary

1. **Download Binary Terbaru:**
   ##### Kunjungi halaman [releases Minikube](https://github.com/kubernetes/minikube/releases) untuk mendapatkan versi terbaru dari Minikube sesuai dengan sistem operasi Anda.

2. **Ganti Binary Lama:**
   ##### Ganti versi Minikube yang lama dengan yang baru. Misalnya, untuk macOS, Anda bisa men-download dan menimpa binary lama dengan yang baru:

```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-amd64
sudo mv minikube-darwin-amd64 /usr/local/bin/minikube
```

##### Pastikan memberikan izin eksekusi jika diperlukan:

```sh
sudo chmod +x /usr/local/bin/minikube
```

## Langkah 2: Update Minikube Profile

3. **Hentikan Minikube:**
   ##### Pastikan Minikube sedang tidak berjalan sebelum melakukan update:

```sh
minikube stop
```

4. **Mulai Minikube dengan Profil:**
   ##### Setelah mengganti binary, mulai kembali Minikube menggunakan profil yang sudah ada:

```sh
minikube start --driver=docker
```

## Langkah 3: Verifikasi Update
 
5. **Periksa Versi Terbaru:**
   ##### Untuk memastikan Minikube sudah diperbarui dengan versi terbaru:

```sh
minikube version
```

##### Hal ini akan menampilkan versi Minikube yang sedang berjalan saat ini.
