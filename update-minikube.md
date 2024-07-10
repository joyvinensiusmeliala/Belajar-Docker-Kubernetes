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
