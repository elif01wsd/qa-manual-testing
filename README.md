### QA Manual Testing

Bu repoda gerçek projeler üzerinde yaptığım manuel test çalışmalarını ve bug raporlarımı topluyorum.

**Ortam (Environment):**
**Test Ortamı:** Samsung Galaxy A26 / Chrome Mobile(Android)
**Teknoloji:** Super AMOLED
**Çözünürlük:** 2340 x 1080 piksel FHD+
**Test Türleri:** UI, Responsive, Form Validation
**URL:** Havayolu firmasına ait İK başvuru formu (live.peoplise.com - Pegasus Cost Control Operation Specialist ve Aircraft Maintenance Technician başvuru formu)
**Ön Koşul (Pre-condition):** Başvuru formunun açık olması


## Bulduğum Buglar

### Bug 01: 
Bir havayolu firmasına ait rezervasyon formunda telefon alanı ve KVKK checkbox arası boşluk hatası [Mobile UI]

**Test Adımları (Steps to Reproduce):**

1-Başvuru formunu mobilde aç
2-Ad, Soyad, E-posta alanlarını geçerli verilerle doldur
3-Telefon alanına odaklan
4-Telefon alanı ile altındaki KVKK onay checkbox'ı arasındaki alana bak
**Beklenen Sonuç (Expected Result):**

Telefon input alanı ile altındaki KVKK checkbox arasında en az 16-24px dikey boşluk olmalı. Görsel hiyerarşi korunmalı.
**Gerçekleşen Sonuç (Actual Result):**

Telefon alanı ile KVKK checkbox'ı birbirine yapışık duruyor. Boşluk (padding/margin) yok. Bu durum UX'i bozuyor ve formun okunabilirliğini düşürüyor.
**Öncelik / Şiddet (Priority / Severity):**

Priority: Low
Severity: Minor (Fonksiyonel hata değil, UI/UX hatası)
**Kanıt (Evidence):**

<img width="738" height="1461" alt="Bug_1" src="https://github.com/user-attachments/assets/26ecad41-630e-4820-9880-db953e059998" />

*Not:* CSS'te margin-bottom veya gap özelliği ile çözülebilir.


### Bug 02:

Aynı formda telefon alanında anlık karakter limiti olmaması [Mobile Validation]
  
**Ön Koşul (Pre-condition):**

Başvuru formunun açık olması
**Test Adımları (Steps to Reproduce):**

1-Başvuru formunu mobilde aç
2-Telefon alanına odaklan
3-Alana 20-25 karakterden uzun sayısal / metinsel veri girmeye çalış (örn: 55555555555555555555)
4-Formu göndermeyi dene
**Beklenen Sonuç (Expected Result):**

Telefon alanı max 11 karakter (veya 10 karakter) ile sınırlandırılmalı. Harf girişini engellemeli ve hatalı girişte "Geçerli bir telefon numarası giriniz" uyarısı vermeli.

**Gerçekleşen Sonuç (Actual Result):**

Telefon alanı karakter limiti yok, 20+ karakter alıyor. Herhangi bir validasyon mesajı göstermiyor. Bu durum DB'de hatalı veri tutulmasına neden olabilir.
**Öncelik / Şiddet (Priority / Severity):**

Priority: Medium
Severity: Major (Veri bütünlüğünü etkiliyor)
**Kanıt (Evidence):**

<img width="738" height="1451" alt="Bug_2" src="https://github.com/user-attachments/assets/05873350-bf67-4a49-a54f-03564ecc73ba" />
**Öneri:** Input için 'maxlength="11"', 'type="tel"' ve 'pattern="[0-9]*"' eklenebilir.







