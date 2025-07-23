# 🌿 IoT Greenhouse Monitoring System

Proyek ini adalah sistem monitoring suhu, kelembaban udara, dan kelembaban tanah otomatis untuk **rumah kaca (greenhouse)** berbasis **ESP32 (Wemos D1 R32)**. Sistem ini mampu menampilkan data secara lokal melalui **LCD 20x4 I2C** dan mengirimkan data ke **ThingSpeak** untuk pemantauan jarak jauh. Terdapat fitur **alarm otomatis dan manual** menggunakan buzzer serta **kontrol MQTT** melalui web dashboard.

## 🔧 Fitur Utama

- Monitoring **suhu dan kelembaban udara** menggunakan sensor **DHT22**
- Monitoring **kelembaban tanah** menggunakan sensor analog
- Tampilan data real-time di **LCD 20x4 I2C**
- Pengiriman data ke **cloud (ThingSpeak)**
- **Kontrol buzzer** otomatis (berdasarkan suhu/kelembaban) dan manual via MQTT
- **Web dashboard** lokal untuk kontrol buzzer (menggunakan Node-RED)
- Mendukung komunikasi **ESP-NOW multi-node** (jika digunakan lebih dari satu node sensor)

## 🧰 Komponen yang Digunakan

| Komponen         | Jumlah | Keterangan                        |
|------------------|--------|------------------------------------|
| ESP32 Wemos D1 R32 | 2–3    | Node sensor & node penerima        |
| Sensor DHT22     | 2–3    | Untuk mengukur suhu dan kelembaban|
| Sensor kelembaban tanah | 2–3 | Sensor analog                     |
| LCD 20x4 I2C     | 1      | Menampilkan data secara lokal     |
| Buzzer aktif     | 1      | Alarm untuk suhu/kelembaban       |
| Relay modul      | 2      | Kontrol pompa air & kipas         |
| Pompa & Kipas    | 1-2    | Otomatis menyala sesuai kondisi   |
| Koneksi WiFi     | -      | Untuk MQTT & ThingSpeak           |

## 🧠 Teknologi & Protokol

- **Bahasa**: Arduino C++
- **Platform**: Arduino IDE
- **Komunikasi Nirkabel**: WiFi & ESP-NOW
- **Cloud**: [ThingSpeak](https://thingspeak.com/)
- **MQTT Broker**: HiveMQ (`broker.hivemq.com`)
- **Web Interface**: Node-RED (dashboard lokal)

## ⚙️ Alur Kerja Sistem

1. Node sensor membaca suhu, kelembaban udara, dan kelembaban tanah.
2. Data ditampilkan di LCD dan dikirim ke ThingSpeak melalui WiFi.
3. Node penerima atau sensor mengontrol relay dan buzzer berdasarkan ambang batas.
4. Kontrol buzzer juga bisa dilakukan manual via MQTT dengan topic:
