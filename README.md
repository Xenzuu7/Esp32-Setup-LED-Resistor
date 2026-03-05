# 📌 ESP32 LED Toggle with Push Button

Project sederhana menggunakan ESP32 buat mengontrol LED menggunakan tombol dengan sistem toggle  
(sekali tekan nyala, tekan lagi mati wkwkwk).

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
4. Pilih board **ESP32 (Arduino)**  
   > bakalan ada opsi tuh MicroPython dan Arduino — pilih Arduino
5. Klik ikon **+** di kanan atas
6. Tambahin:
   - Resistor
   - LED
   - Pushbutton 6mm
7. Buat LED:
   - Klik LED
   - Gunakan tombol **Mirror**
   - Posisikan kaki miring menghadap ESP32

---

## 📷 Preview

![alt text](https://github.com/Xenzuu7/Esp32-Setup-LED-Resistor/blob/main/Public/Screenshot%20(850).png?raw=true)

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
