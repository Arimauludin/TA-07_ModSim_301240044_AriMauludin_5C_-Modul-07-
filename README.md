# Tugas Akhir 07 (TA-07) - Pemodelan dan Simulasi
## Simulasi Sistem Dinamik: Dinamika Suhu Ruangan ber-AC Menggunakan Metode Euler dan SciPy

Repositori ini berisi implementasi kode simulasi sistem dinamik untuk memodelkan perubahan suhu ruangan ber-AC terhadap waktu menggunakan **Ordinary Differential Equation (ODE)** orde satu dengan penyelesaian numerik **Metode Euler** dan validasi menggunakan **SciPy (`solve_ivp`)**.

---

### Identitas Mahasiswa
* **Nama:** Ari Mauludin
* **NIM:** 301240044
* **Kelas / Semester:** 5C / 5
* **Mata Kuliah:** Praktikum Pemodelan dan Simulasi (Modul 7)
* **Dosen Pengampu:** Mohammad Bayu Anggara, S.Kom., M.Kom.

---

### Deskripsi Model & Persamaan Matematika
Sistem dimodelkan berdasarkan neraca energi termal ruangan dengan mekanisme *balancing feedback loop* (umpan balik negatif):

$$C \cdot \frac{dT}{dt} = \frac{T_{\text{out}} - T}{R} + Q_{\text{int}} - Q_{\text{max}} \cdot u(t)$$

Sehingga laju perubahan suhu ruangan dinyatakan sebagai:

$$\frac{dT}{dt} = \frac{1}{C} \left( \frac{T_{\text{out}} - T}{R} + Q_{\text{int}} - Q_{\text{max}} \cdot u(t) \right)$$

#### Parameter Utama Sistem:
| Parameter | Simbol | Nilai | Satuan |
| :--- | :---: | :---: | :---: |
| Kapasitas panas ruangan | $C$ | 200.000 | $\text{J/K}$ |
| Resistansi termal dinding | $R$ | 0,01 | $\text{K/W}$ |
| Daya pendinginan maksimum AC | $Q_{\text{max}}$ | 1.000 | $\text{W}$ |
| Suhu lingkungan luar | $T_{\text{out}}$ | 32 | $^\circ\text{C}$ |
| Beban panas internal (orang & perangkat) | $Q_{\text{int}}$ | 300 | $\text{W}$ |
| Suhu awal ruangan | $T_0$ | 32 | $^\circ\text{C}$ |
| Step size Metode Euler | $\Delta t$ | 10 | $\text{detik}$ |
| Durasi simulasi | $t_{\text{end}}$ | 10.800 | $\text{detik (3 jam)}$ |

---

### Ringkasan Hasil Simulasi & Eksperimen *What-If*
1. **Kondisi Baseline (AC 100%, $Q_{\text{int}} = 300\text{ W}$):** Suhu turun secara eksponensial meluruh dari $32^\circ\text{C}$ menuju titik stabil (*steady state*) di **$25^\circ\text{C}$**.
2. **Skenario 1 - Mode Eco (AC 60%, $Q_{\text{int}} = 300\text{ W}$):** Penurunan suhu melambat dan mencapai keseimbangan baru pada suhu **$29^\circ\text{C}$**.
3. **Skenario 2 - Beban Tinggi (AC 100%, $Q_{\text{int}} = 600\text{ W}$):** Kapasitas AC 1.000 W tidak mencukupi untuk mencapai $25^\circ\text{C}$ sehingga suhu tertahan stabil di **$28^\circ\text{C}$**.

---

### Cara Menjalankan Program
1. Clone repositori ini:
   ```bash
   git clone [https://github.com/Arimauludin/TA-07_ModSim_301240044_AriMauludin_5C_-Modul-07-.git](https://github.com/Arimauludin/TA-07_ModSim_301240044_AriMauludin_5C_-Modul-07-.git)