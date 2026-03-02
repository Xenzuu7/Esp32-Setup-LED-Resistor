# 📌 ESP32 LED Toggle with Push Button

Project sederhana menggunakan ESP32 untuk mengontrol LED menggunakan tombol dengan sistem toggle  
(sekali tekan nyala, tekan lagi mati 😎).

---

## 🧠 Konsep

Project ini menggunakan:
- INPUT_PULLUP
- Deteksi perubahan status tombol (state change detection)
- Penyimpanan status sebelumnya (history)

Saat tombol ditekan:
- LED akan berubah status (ON → OFF / OFF → ON)
- Tidak terjadi kedap-kedip
- Toggle berjalan stabil

---

## 🔧 Alat & Komponen

- ESP32
- Resistor
- LED
- Push Button 6mm

---

## 📸 Tutorial Setup di Wokwi

1. Login / daftar akun di Wokwi  
2. Klik profil (pojok kanan atas) → pilih **My Projects**  
3. Klik **New Project**  
4. Pilih board **ESP32 (Arduino)**  
   > Akan ada opsi MicroPython dan Arduino — pilih Arduino
5. Klik ikon **+** di kanan atas
6. Tambahkan:
   - Resistor
   - LED
   - Pushbutton 6mm
7. Untuk LED:
   - Klik LED
   - Gunakan tombol **Mirror**
   - Posisikan kaki miring menghadap ESP32

---

## 📷 Preview

![Tutorial](assets/tutorial.png)

---

## 💻 Source Code

```cpp
int LED1 = 2;
int tombol1 = 4;

bool statusTombol;
bool statusLED = LOW;
bool terakhir = HIGH;

void setup() {
  pinMode(LED1, OUTPUT);
  pinMode(tombol1, INPUT_PULLUP);
}

void loop() {
  statusTombol = digitalRead(tombol1);

  if (statusTombol == LOW && terakhir == HIGH) {
    statusLED = !statusLED;
    digitalWrite(LED1, statusLED);
  }

  terakhir = statusTombol;
  delay(200);
}
