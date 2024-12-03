# Kırmızı Renk Algılama Projesi

Bu proje, **OpenCV** kullanarak gerçek zamanlı olarak kamera görüntüsünde kırmızı renkleri algılamayı ve maskeleme yapmayı amaçlar. Kod, düşük ve yüksek HSV renk aralıkları kullanarak kırmızı tonlarını belirler ve maskelenmiş bir görüntü üretir.

---

## Özellikler

- **Kamera Görüntüsü Yakalama**: Bilgisayar kamerasından görüntü alır.
- **HSV Renk Uzayına Dönüşüm**: Renk algılama için BGR görüntüsünü HSV formatına dönüştürür.
- **Kırmızı Tonlarını Algılama**: Belirli bir HSV aralığında kırmızı tonlarını tespit eder.
- **Maskeleme**: Tespit edilen kırmızı bölgeleri maskeleyerek vurgular.
- **Gerçek Zamanlı Görüntüleme**: Hem orijinal hem de maskelenmiş görüntüyü canlı olarak gösterir.

---

## Gereksinimler

Bu projeyi çalıştırmak için aşağıdaki yazılımların ve kütüphanelerin sisteminizde kurulu olması gerekir:

- **Python 3.x**
- **OpenCV**
- **NumPy**

Kurulum için gerekli komutlar:
```bash
pip install opencv-python numpy

Kullanım

Kodu Çalıştırın:

python red_color_detection.py

Kameranızı Açın: Kod, bilgisayarınızın bağlı bir kamerasını kullanacaktır.

Kırmızı Renk Algılamasını İzleyin:
Canlı görüntü penceresi açılacaktır.
Maskelenmiş kırmızı bölgeler ayrı bir pencerede gösterilir.

Çıkış:
q veya Esc tuşuna basarak uygulamadan çıkabilirsiniz.

Kod Açıklaması
1. Giriş Kamerasını Açma
cap = cv2.VideoCapture(0)

2. HSV Renk Uzayına Dönüşüm
hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)

3. Kırmızı Renk Maskesi
Düşük ve yüksek kırmızı tonlarını tespit etmek için iki maske oluşturulur:

lower_red1 = np.array([0, 100, 100])
upper_red1 = np.array([10, 255, 255])
lower_red2 = np.array([170, 100, 100])
upper_red2 = np.array([180, 255, 255])
msk1 = cv2.inRange(hsv, lower_red1, upper_red1)
msk2 = cv2.inRange(hsv, lower_red2, upper_red2)

4. Maskelenmiş Görüntü Oluşturma

msk = cv2.bitwise_or(msk1, msk2)
res = cv2.bitwise_and(img, img, mask=msk)

5. Çıkış Tuşu Kontrolü
if k == 27 or k == ord('q'):
    break


DEMO

![Ekran görüntüsü 2024-12-03 115821](https://github.com/user-attachments/assets/7996a849-d6a4-4117-80b7-0e79e1c9de38)

