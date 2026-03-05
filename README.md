# 📌 ESP32 LED Toggle with Push Button

Project sederhana menggunakan ESP32 buat mengontrol LED menggunakan tombol dengan sistem toggle  
(sekali tekan nyala, tekan lagi mati wkwkwk).

![alt text](https://github.com/Xenzuu7/Esp32-Setup-LED-Resistor/blob/main/Public/finally.png
?raw=true)

---

## 🧠 Konsep

Pas tombol diteken:
- LED bakalan berubah status (ON → OFF / OFF → ON)
- Nggak terjadi kedap-kedip
- Toggle berjalan stabil

---

## 🔧 Alat & Komponen

- ESP32
- Resistor
- LED
- Push Button 6mm

---

## 📸 Tutorial Setup di Wokwi

1. Login / daftar akun di Wokwi.com 
2. Klik profil (pojok kanan atas) → pilih **My Projects**
3. Klik **New Project**
   
   ![alt text](https://github.com/Xenzuu7/Esp32-Setup-LED-Resistor/blob/main/Public/Dasboardd.png?raw=true)

    ---  
6. Pilih board **ESP32 (Arduino)**  
   > bakalan ada opsi tuh MicroPython dan Arduino — pilih Arduino

   ![alt text](https://github.com/Xenzuu7/Esp32-Setup-LED-Resistor/blob/main/Public/Opsi.png?raw=true)

   ---
7. Klik ikon **+** di kanan atas
8. Tambahin:
   - Resistor
   - LED
   - Pushbutton 6mm
9. Buat LED:
   - Klik LED
   - Gunakan tombol **Mirror**
   - Posisikan kaki miring menghadap ESP32

---

## 📷 Preview

![alt text](https://github.com/Xenzuu7/Esp32-Setup-LED-Resistor/blob/main/Public/Dasboardd.png?raw=true)

---

## 💻 Source Code

```cpp
int LED1=2;
int tombol1=4;
bool statusTombol;
bool statusLED;
bool terakhirnyala;
void setup() {
  Serial.begin(115200);
  pinMode(LED1, OUTPUT);
  pinMode(tombol1, INPUT_PULLUP);
}

void loop() {
  statusTombol = digitalRead(tombol1);
  if(statusTombol == HIGH && terakhirnyala == LOW){
  statusLED = !statusLED;
  digitalWrite(LED1, statusLED);
  }
  terakhirnyala = statusTombol;
  delay(200);

}
