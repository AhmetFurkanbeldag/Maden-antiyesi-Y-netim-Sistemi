
# Projedeki Kişiler:

Ahmet Furkan Beldağ 225260032

Elif Bayır   240260138

Serhat Tamşen 225260020

# Proje Gereksinimleri:

Bu proje, iş yerinde çalışanların vardiya ve malzeme takibini dijital bir sistemle kolaylaştırmayı amaçlamaktadır. Çalışanların puantajları, sipariş işlemleri, malzeme stok durumu ve vardiya bilgileri gibi süreçlerin dijital ortamda izlenebilmesi hedeflenmiştir. Böylece işletme içindeki operasyonel süreçler hem daha düzenli olacak hem de bilgiye erişim daha kolay hale gelecektir.

# Varlıklar ve Nitelikler:
 Proje kapsamında veritabanında yer alacak ana varlıklar ve bu varlıklara ait nitelikler şöyle tanımlanmıştır:

1.	Çalışan:
   
İş yerinde çalışan kişilere ait bilgileri içerir.

Temel Bilgiler: id, ad, soyad, tc_no, sicil_no

İletişim ve Demografik Bilgiler:

telefon, e_posta, adres, dogum_tarihi

İş Bilgileri: mezuniyet, maas, meslek, gorev, gorev_2, giris_tarihi, cikis_tarihi

SGK ve Kurum Bilgileri: sgk_isyeri_sicil_no, iskolu, biriken_izin, kurum

Çalışan Türü: tur alanı ile çalışanlar "yönetici" veya "işçi" olarak ayrılmaktadır.

2.Yöneticiler:

Yöneticilere ait özel giriş kartı bilgilerini tutar.

Nitelikler: kart_id, calisan_id (Çalışan tablosuyla ilişkili), kart_no, kart_turu, verilme_tarihi


3.İşçiler:

İşçilerin kullandığı malzemelerin takibini sağlar.

Nitelikler: malzeme_id, calisan_id (Çalışan tablosuyla ilişkili), malzeme_adi, miktar


2.	Puantaj:
   
o	Temel bilgiler: id, calisan_id (Çalışan ile ilişki), tarih, mesai_tipi, mesai_saat, fazla_mesai.

o	Açıklama bilgisi: aciklama.

4.	Vardiya:
   
o	Temel bilgiler: id, tarih, vardiyaBaslangic, vardiyaBitis.

o	Çalışma alanı bilgileri: lokasyonAdi, kuyuNumarasi, egim, makinaNo, seriNo.

o	Diğer detaylar: toplamIlerleme, toplamKarot, matkapNo, havaDurumu, aciklama.

6.	Malzeme:
   
o	Temel bilgiler: malzeme_id, malzeme_adi, stok_miktar.

o	Açıklama: aciklama.

o	İlişkili sipariş bilgisi: siparis_no.

7.Hafif Malzemeler:

Malzeme tablosundan türetilmiş olup, hafif malzemelere ait bilgileri içerir.

Nitelikler: malzeme_id, malzeme_adi, stok_miktar, aciklama

8.Ağır Malzemeler:

Malzeme tablosundan türetilmiş olup, ağır malzemelere ait bilgileri içerir.

Nitelikler: malzeme_id, malzeme_adi, stok_miktar, aciklama

9.	Siparişler:

o	Temel bilgiler: siparis_no, kategori, malzeme, firma, adet_miktar.

o	Ek bilgiler: firma_adi, aciliyet, tarih, onay.

o	İlişkili çalışan bilgisi: calisan_id.

# Varlıklar Arasındaki İlişkiler ve Kısıtlamalar:

Projede varlıklar arasında çeşitli ilişkiler ve kısıtlamalar bulunmaktadır. Bu ilişkiler sayesinde sistemdeki verilerin birbiriyle uyumlu ve doğru şekilde yönetilmesi sağlanır.

Çalışan - Vardiya:

Bir çalışanın birden fazla vardiyası olabilir, fakat her vardiyada yalnızca bir çalışan yer alabilir. (1) ----> (N) ilişkisi vardır.

Çalışan – Puantaj İlişkisi:

 Bir çalışanın birden fazla puantaj kaydı olabilir. (1) ----> (N) ilişkisi vardır.
Vardiya – Malzeme İlişkisi:

 Bir vardiyada birden fazla malzeme kullanılabilir, ancak her malzeme yalnızca bir vardiyaya ait olur. (1) ----> (N) ilişkisi vardır.
 
Malzeme – Siparişler İlişkisi:

Bir malzeme birden fazla siparişle ilişkili olabilir, ancak her sipariş tek bir malzemeye ait olur. ilişkisi vardır. (1)---->(N) ilişkisi vardır.

Çalışan – Siparişler İlişkisi:

Bir çalışan birden fazla sipariş oluşturabilir, fakat her sipariş tek bir çalışan tarafından oluşturulmalıdır. (1) ----> (N) ilişkisi vardır.

Hafif ve Ağır Malzemeler-Malzemeler İlişkisi:

Hafif ve ağır malzemeler, malzeme tablosunda farklı özellikler ve kullanım alanlarına göre ayrılır. Malzeme tablosunda, her bir malzeme türü için ağırlık, dayanıklılık, maliyet ve kullanım amacına göre sınıflandırmalar bulunur. 

Malzeme tablosunda bu özelliklerin her biri belirli kriterler altında gösterilir. Hafif ve ağır malzemelerin seçimi projeye özel gereksinimlere göre yapılır.

# İş Kuralları ve Kısıtlamalar:

Bu projede verilerin tutarlılığını sağlamak için belirli iş kuralları ve kısıtlamalar bulunmaktadır:
•	Çalışan TC Kimlik Numarası benzersiz olmalı.
•	Malzeme stok miktarı, sıfırın altına düşmemeli. Stok yetersiz kaldığında uyarı sistemi devreye girebilir.
•	Sipariş aciliyet durumu, "Yüksek", "Orta" veya "Düşük" gibi belirli kategorilerde sınıflandırılmalı.
•	Puantaj tarihleri, çalışanın ilgili vardiya tarihleriyle uyumlu olmalı.
• Hafif ve ağır malzemeler, malzeme türlerine göre ayrılmalı, böylece malzeme yönetimi daha etkin yapılmalıdır.

# Kullanıcı Türleri ve Gereksinimleri:

Projede üç temel kullanıcı türü bulunmaktadır ve her birinin farklı gereksinimleri vardır:
1.	Yönetici: Tüm çalışan ve vardiya bilgilerini görebilir ve düzenleyebilir, malzeme ve sipariş durumunu kontrol edebilir, siparişleri onaylayabilir.
2.	Çalışan: Kendi vardiya ve puantaj bilgilerini görüntüleyebilir, kendi adına sipariş oluşturabilir.
3.	Depo Görevlisi: Malzeme stok durumunu takip eder, stok güncellemelerini yapar.

# Raporlama ve İzleme:

Bu sistem, işletmenin operasyonel süreçlerini daha etkili bir şekilde yönetebilmesi için çeşitli raporlama ve izleme özellikleri de içermelidir:
•	Vardiya Raporları: Vardiya başına görevli çalışanlar ve yapılan işler raporlanmalı.
•	Malzeme Stok Raporu: Stok durumu periyodik olarak raporlanmalı ve eksik malzemeler hakkında bilgilendirme yapılmalı.
• Sipariş Durumu Raporu: Siparişlerin onay durumu, teslim edilme durumu gibi bilgiler raporlanmalıdır.
• Hafif ve Ağır Malzemeler Raporu: Malzemelerin türlerine göre stok durumları ve kullanımları düzenli olarak raporlanmalıdır.

Bu gereksinimler doğrultusunda, sistemin tasarlanması ve geliştirilmesi projenin hedeflerine ulaşması için büyük önem taşır. Sistemin kapsamlı, kullanıcı dostu ve iş akışlarına uygun olması için bu gereksinimlere uyulmalıdır.

# E-R Diyagramı:

![whatsapp e-r diagrams](https://github.com/user-attachments/assets/c7882139-bbf2-47e8-8ad8-f1beafb0d413)


