# LBE NCC Final Project

| Nama | NRP | 
| :--- | :--- |
| Khumaidy Syafiq El Maududy | 5025251012 |
| Agile Octa Agrakha Handrian | 5025251010 |
| Ahmad Farras Favian Al Efasi | 5025251005 |
| Hussein Mohammad Mahsun | 5025251170 |

* **Load Balancer Public IP:** `http://4.147.81.78`

## 1. Deskripsi Aplikasi
Aplikasi ini adalah website portofolio statis yang menampilkan profil dan informasi anggota tim. Aplikasi dikemas ke dalam kontainer Docker berbasis `nginx:alpine` dan didistribusikan melalui Azure Standard Load Balancer di atas Virtual Machine Ubuntu.

## 2. Arsitektur Teknis
* **Resource Group:** `RG-LBE-NCC`
* **Virtual Network:** `VN-LBE-NCC`
* **Virtual Machines:** Ubuntu Server 24.04 LTS (`Standard_B2ats_v2`)
* **Kontainerisasi:** Docker container berbasis `nginx:alpine` yang melayani file statis pada **port 80**.
* **Konfigurasi Load Balancer:**
  * **SKU:** Standard
  * **Backend Pool:** Mengikutsertakan VM (`lbe-backend-pool`)
  * **Health Probe:** TCP Port 80 (`lbe-health-probe`)
  * **Load Balancing Rule:** Frontend Port 80 $\rightarrow$ Backend Port 80 (`lbe-http-rule`)
  * **Session Persistence:** None

## 3. How to Build and Run Container

### Docker Build Command
Jalankan perintah ini dari folder paling luar (*root*) repositori:
```bash
docker build -t portfolio-app ./app
sudo docker run -d -p 80:80 --name portfolio --restart always portfolio-app
```

### Result

<img width="1013" height="566" alt="Screenshot 2026-09-23 at 5 25 17 PM" src="https://github.com/user-attachments/assets/fb215b38-2059-4d47-bbe2-ee0df35d4ab2" />

<img width="509" height="671" alt="WhatsApp Image 2026-09-23 at 3 53 20 PM" src="https://github.com/user-attachments/assets/db694a55-8b63-4b74-8e15-de42751357d9" />
