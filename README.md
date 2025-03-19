# Yüz Tanıma ve Devam Takip Sistemi | Face Recognition & Attendance Tracking System

Bu proje, OpenCV ve PostgreSQL kullanarak bir yüz tanıma tabanlı çalışan devam takip sistemidir. Kamera aracılığıyla çalışan yüzlerini algılar, veritabanına kaydeder ve giriş saatlerini kayıt altına alır.

This project is a face recognition-based employee attendance tracking system using OpenCV and PostgreSQL. It detects employee faces via a camera, records them in the database, and logs their check-in times.

## Özellikler | Features
- OpenCV kullanarak yüz algılama ve tanıma | Face detection and recognition using OpenCV
- PostgreSQL veritabanı entegrasyonu | PostgreSQL database integration
- Çalışan bilgilerini kaydetme ve doğrulama | Storing and verifying employee information
- Geç kalan çalışanları tespit etme | Identifying late employees
- Gerçek zamanlı kamera akışı ile yüz tanıma | Real-time face recognition with live camera feed

## Gereksinimler | Requirements
Bu projeyi çalıştırmak için aşağıdaki bileşenlerin sisteminizde yüklü olması gerekmektedir:

To run this project, the following components must be installed on your system:

- Python 3.x
- OpenCV
- NumPy
- psycopg2 (PostgreSQL için | for PostgreSQL)
- PostgreSQL Veritabanı | PostgreSQL Database

Gerekli Python kütüphanelerini aşağıdaki komutla yükleyebilirsiniz:

You can install the required Python libraries using the following command:

```sh
pip install opencv-python numpy psycopg2
```

## Kurulum | Setup
1. PostgreSQL veritabanınızda aşağıdaki tabloyu oluşturun:

   Create the following table in your PostgreSQL database:

```sql
CREATE TABLE calisanlar (
    id SERIAL PRIMARY KEY,
    ad VARCHAR(50),
    soyad VARCHAR(50),
    yuz_verisi BYTEA,
    son_giris TIMESTAMP
);
```

2. `attendance.py` ve `face_recognition.py` dosyalarındaki veritabanı bağlantı bilgilerini kendi sisteminize göre güncelleyin.
   Update the database connection details in `attendance.py` and `face_recognition.py` according to your system.

3. Projeyi çalıştırmak için terminal veya komut satırından aşağıdaki komutları kullanabilirsiniz.
   Run the project using the following commands in the terminal or command prompt.

## Kullanım | Usage

### 1. Yeni Çalışan Kaydetme | Register a New Employee
Yeni bir çalışanı sisteme kaydetmek için aşağıdaki komutu çalıştırın:
Run the following command to register a new employee:

```sh
python face_recognition.py
```
Bu komut kamera aracılığıyla bir çalışanın yüzünü algılayacak ve ad-soyad bilgisi ile birlikte veritabanına kaydedecektir.
This command detects an employee’s face through the camera and saves it in the database along with their name and surname.

### 2. Devam Takibi | Attendance Tracking
Kamera aracılığıyla çalışanların giriş saatlerini kaydetmek için aşağıdaki komutu çalıştırın:
Run the following command to log employees' check-in times via face recognition:

```sh
python attendance.py
```
Bu komut yüz tanıma yaparak çalışanların giriş saatlerini kayıt altına alacak ve saat 09:00'dan sonra girenleri "geç kaldı" olarak işaretleyecektir.
This command recognizes faces and logs check-in times, marking employees as "late" if they arrive after 09:00 AM.

## Katkıda Bulunma | Contributing
Bu projeye katkıda bulunmak isterseniz, pull request oluşturabilir veya hata bildiriminde bulunabilirsiniz.
If you'd like to contribute to this project, feel free to submit a pull request or report issues.

## Lisans | License
Bu proje MIT lisansı altında sunulmuştur.
This project is licensed under the MIT License.
