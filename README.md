# bodrum-gezi-bte-planlama
Ege Üniversitesi                                                                                              TESLİM    TARİHİ                      Tire Kutsan Meslek Yüksekokulu                                                              23.10.2026
Bilgisayar Programcılığı
Proje Dersi Raporu




PROJE ADI :GEZİ VE BÜTÇE PLANLAMA SİSTEMİ
GITHUB REPO URL: 	https://github.com/isiktanis40-gif/bodrum-gezi-bte-planlama
ÖĞRENCİ BİLGİLERİ:
1.	Öğrenci Numara - Adı Soyadı
60250000054
MELTEM IŞIK TANIŞ
2.	Öğrenci Numara - Adı Soyadı
İNCİSU TEPE
60250000028
 
A. Sistem Gereksinimleri
1. Projenin Amacı ve Kapsamı (Scope)
•	Bu sistem hangi problemi çözüyor?
Günümüzde tatil ve seyahat planlaması yaparken kullanıcılar; yüzlerce mekan arasından bütçelerine, kısıtlı zamanlarına ve ilgi alanlarına uygun seçenekleri bulmakta zorlanmaktadır. Özellikle Muğla’nın gözde turizm merkezi olan Bodrum gibi popüler bir bölgede, yüzlerce restoran, plaj, eğlence mekanı ve tarihi alan arasından bütçe dostu tercihler yapabilmek ciddi bir bilgi kirliliği ve zaman kaybına yol açmaktadır. Bu proje; kullanıcıların karmaşık ve maliyetli rota/harita uygulamalarında vakit kaybetmeden, bütçelerine ve seçtikleri kategoriye uygun mekanlara en kısa yoldan ulaşmasını sağlayarak bu problemi ortadan kaldırmayı amaçlamaktadır.
•	Sistem ne yapacak?
o	Kullanıcılara Bodrum bölgesindeki restoran, büfe, plaj/beach, aktivite, eğlence mekanları ve tarihi yerler arasından filtreleme yapma imkânı sunacaktır.
o	Kullanıcının sisteme girdiği bütçe üst limiti ve tercih ettiği kategori(ler) doğrultusunda veritabanından anlık sorgulama yaparak uygun mekanları listeleyecektir.
o	Listelenen her mekanın yanında, kullanıcıyı doğrudan ilgili konumun harita servisine yönlendiren birer harita bağlantısı ("Haritada Göster" linki) bulunduracaktır.
o	Sistem yöneticilerine (Admin) veritabanındaki mekanları yönetme (yeni mekan ekleme, mevcut mekanların bütçe/fiyat aralığını veya kategorisini güncelleme, silme) yetkisi sağlayacaktır.
o	Hem masaüstü hem de mobil cihazlardan sorunsuz erişilebilmesi için duyarlı (responsive) bir arayüze sahip olacaktır.

•	Sistem ne yapmayacak (kapsam dışı olan konular)?
o	Proje bütününde yapay zekâ tabanlı doğal dil işleme, akıllı asistan veya otomatik rota optimizasyonu özellikleri yer almayacaktır.
o	Uygulama içinde harita servislerinin (Google Maps API vb.) canlı entegrasyonu ve harita içi rota çizimi yapılmayacak; bunun yerine harita bilgisi yalnızca dış bağlantı linki olarak sunulacaktır.
o	(ŞİMDİLİK) Sistem, Muğla’nın Bodrum ilçesi dışındaki hiçbir bölgeyi, şehri veya tatil beldesini kapsamayacaktır.
o	Uygulama üzerinden herhangi bir online ödeme, rezervasyon, sepet veya e-ticaret finansal işlemi gerçekleştirilmeyecektir.
Bu şekilde detaylandırdığımızda metin hem akademik olarak çok daha dolgun duruyor hem de raporun genel sayfa sayısını ve kalitesini doğrudan artırıyor.

 
2. Kullanıcı Profilleri / Aktörler (User Classes & Roles)
Sistemde üç farklı kullanıcı rolü (aktör) bulunmaktadır: 

•	1. Ziyaretçi (Kayıtsız Kullanıcı):
o	Tanım: Uygulamaya henüz kaydolmamış veya giriş yapmamış genel kullanıcıdır. 
o	Sistemdeki Yetki Seviyesi:
	Sistemdeki bütçe ve kategori filtreleme ekranına erişebilir.
	Bodrum mekanlarını listeleyebilir ve mekanların "Haritada Göster" linkine tıklayabilir.
	Kayıt Ol (Sign Up) ve Giriş Yap (Login) sayfalarını kullanabilir.
•	2. Kayıtlı Kullanıcı (Gezgin):
o	Tanım: Sisteme üye olmuş ve kendi hesabıyla giriş yapmış son kullanıcıdır. 
o	Sistemdeki Yetki Seviyesi:
	Ziyaretçinin sahip olduğu tüm filtreleme ve listeleme yetkilerine sahiptir.
	Kendi profili üzerinden hesaba giriş yapabilir ve çıkış yapabilir.
	Beğendiği Bodrum mekanlarını kendi profilinde "Favorilerim" listesine ekleyebilir veya çıkarabilir.
	Kendi profil bilgilerini ve şifresini güncelleyebilir.
•	3. Sistem Yöneticisi (Admin):
o	Tanım: Sistemin teknik yönetimini ve içerik kontrolünü sağlayan yetkili yöneticidir. 
Sistemdeki Yetki Seviyesi:
•	Özel admin girişi ile sisteme erişir.
•	Veritabanına yeni Bodrum mekanları ekleyebilir, mevcut mekanların bütçe/fiyat, kategori ve harita linki bilgilerini güncelleyebilir veya silebilir (Mekan Veri Yönetimi). 
•	Sistemdeki kayıtlı kullanıcıların listesini (kullanıcı adı, e-posta vb.) denetim amacıyla görüntüleyebilir; ancak kullanıcıların kişisel profillerine veya özel favori listelerine erişemez / müdahale edemez.

 
3. Fonksiyonel Gereksinimler (Functional Requirements)
A. Ziyaretçi & Kayıtlı Kullanıcı (Gezgin) Hikayeleri
1.	Üyelik ve Hesap Yönetimi:
o	Bir Ziyaretçi olarak, sisteme kayıt olmak ve var olan hesabımla giriş yapmak istiyorum, böylece kişisel profilime erişip beğendiğim mekanları kaydedebileyim. 
2.	Bütçe ve Kategori Filtreleme:
o	Bir Kullanıcı olarak, harcamak istediğim bütçe miktarını (TL) girmek ve gitmek istediğim kategorileri (Plaj/Beach, Restoran, Büfe, Aktivite, Eğlence, Tarihi Yerler) seçmek istiyorum, böylece Bodrum'da sadece bütçeme ve ilgi alanıma uygun yerleri listeleyebileyim. 
3.	Sonuç Listeleme:
o	Bir Kullanıcı olarak, filtreleme sonucunda bütçeme uyan mekanları isim, kategori ve ortalama fiyat detaylarıyla görmek istiyorum, böylece aralarından seçim yapabileyim. 
4.	Harita Bağlantısı (Dış Link):
o	Bir Kullanıcı olarak, beğendiğim bir mekanın kartındaki "Haritada Göster" butonuna tıklayabilmek istiyorum, böylece harita servisleriyle zaman kaybetmeden doğrudan Google Maps üzerinde mekanın konumunu açabileyim. 
5.	Favorilere Ekleme ve Yönetme:
o	Bir Kayıtlı Kullanıcı olarak, beğendiğim Bodrum mekanlarını tek tıkla favorilerime eklemek veya çıkarmak istiyorum, böylece daha sonra tekrar arama yapmadan favori mekanlarıma kolayca erişebileyim. 
     6. Kullanıcı Kaydı ve SMS Doğrulama:
o	Bir Ziyaretçi olarak, sisteme kayıt olurken telefon numaramı girmek ve telefonuma gelen SMS doğrulama kodunu (OTP) sisteme girmek istiyorum, böylece hesabımı güvenli bir şekilde oluşturup aktif hale getirebileyim. 
B. Sistem Yöneticisi (Admin) Hikayeleri
Yönetici Girişi ve Güvenlik:
o	Bir Admin olarak, özel admin giriş paneli üzerinden yetkili bilgilerimle sisteme güvenli bir şekilde giriş yapmak ve oturumumu sonlandırabilmek istiyorum, böylece yönetim paneline yetkisiz kişilerin erişmesini engelleyebileyim. 

Mekan Ekleme (Create):
o	Bir Admin olarak, Bodrum bölgesine ait yeni mekanları isim, kategori, ortalama fiyat/bütçe, detaylı açıklama ve Google Maps konum linki bilgileriyle sisteme ekleyebilmek istiyorum, böylece veritabanındaki mekan çeşitliliğini sürekli artırabileyim. 

Mekan Bilgilerini Güncelleme (Update):
o	Bir Admin olarak, mevcut bir mekanın değişen fiyat seviyesini, kategorisini veya konum linkini güncelleyebilmek istiyorum, böylece kullanıcılara sunulan bilgilerin güncelliğini ve doğruluğunukoruyabileyim. 
      Mekan Silme ve Pasife Alma (Delete):
o	Bir Admin olarak, faaliyetine son verilen, kapanan veya hatalı girilen mekan kayıtlarını veritabanından silebilmek veya geçici olarak pasife alabilmek istiyorum, böylece kullanıcıların geçerliliğini yitirmiş mekanlarla karşılaşmasını önleyebileyim. 
Kullanıcı Hesap Denetimi:
o	Bir Admin olarak, sisteme kayıtlı kullanıcıların listesini (kullanıcı adı, kayıt tarihi, e-posta/telefon) görüntüleyebilmek ve gerektiğinde kurallara uymayan hesapları askıya alabilmek/silebilmek istiyorum, böylece sistemdeki kullanıcı güvenliğini sağlarken kişisel verilere (özel favori listeleri vb.) müdahale etmeden genel denetimi yürütebileyim. 
Kategori ve İçerik Yönetimi:
o	Bir Admin olarak, sistemde yer alan kategorileri (Restoran, Plaj/Beach, Tarihi Yer vb.) yönetebilmek ve yeni kategori başlıkları tanımlayabilmek istiyorum, böylece gelecekte yeni mekan türleri eklendiğinde filtreleme seçeneklerini esnek bir şekilde genişletebileyim. 














4. Fonksiyonel Olmayan Gereksinimler (Non-Functional Requirements)
Sistemin performans, güvenlik, kullanılabilirlik ve uyumluluk gibi kalite standartları şunlardır: 
•	Performans ve Hız: Kullanıcı bütçe ve kategori kriterlerini seçip "Filtrele" butonuna bastığında, veritabanından çekilen sonuçlar ekranda en fazla 1-2 saniye içerisinde listelenmelidir. 
•	Veri Güvenliği ve Gizlilik:
o	Kullanıcıların ve adminlerin hesap şifreleri veritabanında kesinlikle açık metin (plain text) olarak tutulmayacak; gibi güvenli şifreleme algoritmaları (hash) ile saklanacaktır. 
o	Yetkisiz kullanıcıların admin paneline veya başka bir kullanıcının özel favori listesine erişmesi engellenecektir. 
•	Erişilebilirlik ve Duyarlılık (Responsive Design): Kullanıcı arayüzü; masaüstü bilgisayarlar, tabletler ve akıllı telefonlar gibi farklı ekran boyutlarına sahip tüm cihazlarda bozulma yaşanmadan, uyumlu ve okunabilir bir şekilde çalışmalıdır. 
•	Kullanılabilirlik (UI/UX): Arayüz karmaşık detaylardan uzak, sade ve anlaşılır olacaktır. Kullanıcı ana sayfaya girdikten sonra en fazla 2-3 adımla bütçesine uygun mekana ve harita linkine ulaşabilmelidir. 
•	Veri Doğruluğu ve Güvenilirlik: Veritabanına eklenen mekanların ortalama bütçe/fiyat seviyeleri ve harita konum URL'leri düzenli olarak kontrol edilmeli, yönlendirme linklerinin doğru çalışması sağlanmalıdır. 
Güvenlik ve Doğrulama:
•	Kullanıcı kayıtlarında SMS doğrulama kodu kullanılarak sahte/bot hesap oluşturulması engellenecektir. 
•	SMS doğrulama kodları belirli bir süreye (ör. 3 dakika) tabi tutulacak ve veritabanında güvenli bir şekilde saklanacaktır. 

 
5. Harici Arayüz Gereksinimleri (External Interfaces)
Projenin teknik mimarisinde yer alan donanım, yazılım ve dış sistem arayüz gereksinimleri aşağıda detaylandırılmıştır: 
•	1. Harici Konum ve Harita Servisleri Arayüzü:
o	Uygulama bünyesinde canlı harita işlemleri (harita çizimi, canlı konum takibi veya rota hesaplama) için karmaşık Harita API'leri (Google Maps JavaScript API, Mapbox vb.) ya da ücretli web servisleri entegre edilmeyerek proje maliyeti ve karmaşıklığı optimize edilmiştir. 
o	Bunun yerine veritabanında her mekan için saklanan özelleştirilmiş Google Maps URL yapıları kullanılmaktadır.
o	Kullanıcı arayüzünde "Haritada Göster" bağlantısına tıklandığında, sistem işletim sisteminin varsayılan web tarayıcısı üzerinden harici Google Maps servisiyle URI/URL bazlı yönlendirme arayüzü aracılığıyla haberleşir. 
•	2. Yazılım ve Sunucu Arayüzleri (Software & Protocol Interfaces):
o	İstemci - Sunucu Haberleşmesi: Kullanıcı arayüzü (HTML/CSS) ile backend sunucu katmanı (Python/Java) arasındaki veri alışverişi standart HTTP/HTTPS protokolleri üzerinden gerçekleştirilecektir.
o	Veritabanı Arayüzü: Backend servisi, veritabanı yönetim sistemi (SQLite/MySQL) ile güvenli sorgu bağlantı katmanı (SQL Driver / ORM) üzerinden iletişim kuracaktır.
•	3. Üçüncü Taraf (3rd Party) Entegrasyon Kısıtları:
o	Projenin mevcut kapsamı doğrultusunda SMS doğrulama, e-posta bildirim sunucusu (SMTP) veya online ödeme altyapıları (İyzico vb.) gibi dış finansal ve doğrulama servisleri harici arayüz kısıtı olarak sistem dışında tutulmuştur. 

 
                                                        DİZAYN RAPORU
B.1.1. Kullanım Senaryosu (Use-Case) Diyagramı 


 
Şekil 1Bodrum Gezi ve Bütçe Planlama Sistemi Use-Case (Kullanım Senaryosu) Diyagramı

 
Bir önceki sayfada, Use-Case (Kullanım Senaryosu) diyagramı, Bodrum Gezi ve Bütçe Planlama Sistemi’nin temel aktörlerini, sistem sınırlarını ve bu aktörlerin gerçekleştirdiği işlevsel süreçleri modellemektedir. Sistem mimarisinde yetki ve sorumluluklar iki ana aktör üzerinden tanımlanmıştır: "Kayıtlı / Ziyaretçi Kullanıcı" ve "Sistem Yöneticisi (Admin)". 
Sistem içerisindeki temel aktörlerin işlevsel etkileşimleri şu başlıklar altında incelenmektedir:
•	Ziyaretçi ve Kayıtlı Kullanıcı Süreçleri:
o	Sisteme Kayıt Ol / SMS Doğrulama: Yeni kullanıcılar sistemde hesap oluştururken telefon numaralarını girer ve güvenli bir altyapı için harici SMS API üzerinden gönderilen tek kullanımlık doğrulama kodunu (OTP) sisteme girerek hesaplarını aktifleştirir. 
o	Bütçe ve Kategori Filtreleme: Kullanıcılar, tatil bütçelerine ve gitmek istedikleri mekan kategorilerine (Restoran, Plaj, Tarihi Yer vb.) göre veritabanında anlık filtreleme yapabilir. 
o	Mekan Listeleme ve Harita Yönlendirmesi: Filtreleme sonucunda listelenen Bodrum mekanlarının detaylarına ulaşan kullanıcılar, "Haritada Göster" bağlantısı aracılığıyla harici harita servisleri üzerinden mekanın konumuna erişebilir. 
o	Favori Yönetimi: Sisteme giriş yapmış kayıtlı kullanıcılar, beğendikleri mekanları kendi kişisel favori listelerine ekleyebilir veya listeden çıkarabilir. 
•	Sistem Yöneticisi (Admin) Süreçleri:
o	Mekan Yönetimi (CRUD): Admin, yönetim paneli aracılığıyla Bodrum bölgesine ait yeni mekanlar ekleyebilir, mevcut mekanların bütçe veya konum bilgilerini güncelleyebilir ya da pasife alabilir. 
o	Kullanıcı Hesap Denetimi: Yönetici, platformun güvenliğini sağlamak amacıyla kayıtlı kullanıcıların listesini denetleyebilir ve kurallara aykırı hareket eden hesaplar üzerinde yönetimsel işlemler gerçekleştirebilir.

 
B.2.1. Genişletilmiş Veritabanı Varlık-İlişki (ERD) Şeması ve Tablo Mimarisi

 
Şekil 2Bodrum Gezi ve Bütçe Planlama Sistemi Veritabanı Varlık-İlişki (ERD) Mimarisi
Bodrum Gezi ve Bütçe Planlama Sistemi'nin veritabanı tasarımı; güvenlik, yetkilendirme, veri bütünlüğü ve ölçeklenebilirlik prensipleri doğrultusunda 9 ana varlıktan (Entity) oluşacak şekilde normalize edilmiştir: 
•	Role ve User (Rol ve Kullanıcı Yönetimi): Rol tabanlı erişim kontrolü (RBAC) mimarisi kurulmuştur. Role tablosu sistemdeki yetki seviyelerini (ADMIN, USER) tanımlarken, User tablosu role_id yabancı anahtarı üzerinden kullanıcının sistemdeki rolünü belirler. 
•	SMS_Verification (SMS/OTP Doğrulama Mimarisi): Güvenlik gereksinimleri gereği, kayıt esnasında üretilen 6 haneli doğrulama kodları (otp_code), son kullanma zamanı (expires_at) ve kullanım durumu (is_used) bilgileriyle bu tabloda loglanır. 
•	Category ve Location (Kategori ve Konum Yönetimi): Mekanlar hem kategorilerine (Restoran, Plaj, Tarihi Yer) hem de Bodrum'un belde/mahalle bazlı konumlarına (location_id - Yalıkavak, Türkbükü, Marina vb.) göre iki farklı eksende ilişkilendirilmiştir. 
•	Place (Mekan Ana Verisi): Bodrum bölgesindeki işletmelerin temel bilgilerini saklar. Bütçe süzgeci için budget_level (Düşük, Orta, Yüksek) ve avg_price_range alanlarını barındırır. 
•	Place_Image (Görsel Galerisi): Bir mekana ait birden fazla fotoğrafın yüklenebilmesi ve vitrin görselinin seçilebilmesi (is_primary) için 1'e Çok (1:N) ilişkiyle tanımlanmıştır. 
•	Favorite ve Review (Kullanıcı Etkileşimi): Kayıtlı kullanıcıların mekanları favorilemesi (Favorite) ve 1-5 arası puan verip yorum yapabilmesi (Review) sağlanarak etkileşimli bir gezi rehberi altyapısı oluşturulmuştur. 

 
UML Sınıf (Class) Diyagramı:
 
Şekil 3Bodrum Gezi ve Bütçe Planlama Sistemi UML Sınıf (Class) Diyagramı
Sistemin nesne yönelimli yazılım mimarisi (Object-Oriented Architecture), modülerlik ve sürdürülebilirlik ilkeleri doğrultusunda tasarlanmıştır. Diyagramda yer alan temel sınıflar ve işlevleri aşağıda özetlenmiştir: 
•	Kullanici ve Admin (Nesne Kalıtımı / Inheritance): Admin sınıfı, temel kullanıcı özelliklerini ve SMS doğrulama metotlarını barındıran Kullanici sınıfından türetilmiştir (Inheritance). Admin, ek olarak mekanEkle(), mekanGuncelle(), mekanSil() ve kullaniciDenetle() yetkilerine sahiptir. 
•	Mekan ve Kategori: Mekan sınıfı Bodrum bölgesindeki işletmelerin özniteliklerini ve konumAc() fonksiyonunu barındırır. Her mekan bir Kategori nesnesine bağlıdır (1..* - 1 ilişkisi). 
•	BütçeFiltreleyici: Kullanıcının seçtiği bütçe aralığı ve kategori parametrelerine göre veritabanından uygun mekan listesini dönen servis sınıfıdır (filtrele()). 
•	FavoriServisi: Kullanıcıların beğendikleri mekanları kendi listelerine eklemesini, çıkarmasını ve listelemesini sağlayan iş mantığı (Business Logic) sınıfıdır. 

3. UI/UX Tasarımları (Kullanıcı Arayüzü Mimarisi)
Bodrum Gezi ve Bütçe Planlama Sistemi'nin kullanıcı arayüzü; kullanıcı deneyimini (UX) ön planda tutan, sade, erişilebilir ve mobil öncelikli (Mobile-First) tasarım prensiplerine uygun olarak kurgulanmıştır. Sistem ekranlarının işlevsel tasarımı ve tel kafes (Wireframe) bileşen yapısı bir sonraki sayfada detaylandırılmıştır:
























EKRAN ADI	ARAYÜZ BİLEŞENLERİ VE 
İÇERİK YAPISI	KULLANICI ETKİLEŞİMİ/
AKSİYON
1.Giriş ve OTP SMS doğrulama ekranı	Uygulama Logosu & Karşılama Metni
• Telefon Numarası Giriş Kutusu (+90 5XX...)
• 6 Haneli OTP Kod Giriş Kutucukları
• "Kodu Gönder" ve "Giriş Yap" Butonları
	Kullanıcı telefon numarasıı girer,harici SMS servisinden gelen tek kullanımlık doğrulama kodunu yazarak oturum açar.
2.Ana sayfa&bütçe filtreleme ekranı	Arama Çubuğu (Mekan Adı Arama)
• Kategori Seçim Menüsü (Restoran, Plaj, Tarihi Yer, Kafe, eğlence-aktivite)
• Bütçe Aralığı Kaydırıcısı (Slider: ₺ - ₺₺₺)
• Mekan Kartları Listesi (Görsel, Başlık, Bütçe Etiketi, Favori Butonu)

	Kullanıcı bütçesine ve gitmek istediği kategoriye göre anlık filtreleme yapar, mekan kartlarını inceler. 

3. Mekan Detay Ekranı	• Mekan Görsel Galerisi (Slider/Carousel)
• Mekan Başlığı, Kategori Etiketi ve Bütçe Seviyesi
• Detaylı Açıklama Metni
• 📍 "Haritada Göster" Link/Butonu
• ❤️ "Favorilerime Ekle" Butonu
	Kullanıcı mekan detaylarını okur, tek tıkla Google Maps uygulamasına yönlendirilir ve beğendiği mekanı favorilerine ekler. 

4. Admin Yönetim Paneli	Yeni Mekan Ekleme Formu (İsim, Kategori, Bütçe, Konum URL)

• Mevcut Mekan Listeleme Tablosu (Düzenle ✏️ / Sil 🗑️)
• Kullanıcı Hesap Denetim Tablosu
	Sistem yöneticisi veritabanına yeni mekan ekler, mevcut mekanları günceller/siler ve kullanıcı hesaplarını kontrol eder
 






tablolarda, Bodrum Gezi ve Bütçe Planlama Sistemi'nin kullanıcı arayüzü mimarisini oluşturan 4 temel ekran; bu ekranlarda yer alan bileşenler ve kullanıcıların gerçekleştirdiği temel aksiyonlar özetlenmiştir. Sistem tasarımı, kullanıcıların bütçelerine uygun mekanlara en az adımda ve sezgisel bir arayüz üzerinden ulaşabilmesini sağlayacak şekilde kurgulanmıştır.
UI/UX unsuru Tasarım kararı:
Renk paleti :Deniz mavisi, beyaz ve kum beji
Yazı tipi :Okunaklı, sade bir sans-serif yazı tipi
Navigasyon Ana sayfa, keşfet, harita ve favoriler
Butonlar Kolay fark edilen ve anlaşılır etiketlere sahip
Mekân kartları Fotoğraf, isim, kategori ve fiyat seviyesi
Mobil uyumluluk Telefon ekranlarına uygun, duyarlı tasarım
Geri bildirim Başarılı işlem ve hata mesajları
Erişilebilirlik Yeterli renk kontrastı ve okunaklı yazılar

 
4. Kullanılan Teknolojiler
Bodrum Gezi ve Bütçe Planlama Sistemi'nin geliştirilme sürecinde; sistem gereksinimleri, performans, güvenilirlik ve ekibin aktif olarak bildiği programlama dilleri (Python, Java, C, HTML, CSS) tam uyumlu şekilde tercih edilmiştir. Kullanılan teknolojiler ve tercih edilme nedenleri aşağıda açıklanmıştır:
4.1. Ön Yüz (Frontend) Teknolojileri
•	HTML5 & CSS3: Kullanıcı arayüzünün (UI) mobil öncelikli (Mobile-First), sade ve duyarlı (responsive) bir yapıda tasarlanması için kullanılmıştır. Ekibin iyi düzeyde hakim olduğu bu diller sayesinde arayüz hızlıca ayağa kaldırılmıştır.
4.2. Arka Yüz (Backend) Teknolojileri
•	Python (Flask veya FastAPI) / Java: Kullanıcı isteklerini işlemek, bütçe filtreleme algoritmalarını çalıştırmak ve veritabanı köprü işlemlerini yönetmek amacıyla arka yüzde tercih edilmiştir. Ekibin bildiği diller arasında yer alması, sunucu mantığının güvenli ve hatasız kodlanmasını sağlamıştır.
4.3. Veritabanı ve Veri Yönetimi (Database)
•	SQL / SQLite / MySQL: İlişkisel veritabanı yapısı (ERD) doğrultusunda mekan bilgileri, kategoriler, kullanıcı tercihleri ve favori listelerinin düzenli saklanması için seçilmiştir. Temel programlama derslerinde öğrenilen SQL altyapısı ile tam uyumludur.
4.4. Harici Servisler ve Entegrasyonlar
•	Google Maps URL Protocol: Kullanıcıların seçtiği mekanın konumuna harici tarayıcı veya harita uygulaması üzerinden tek tıkla ulaşabilmesi amacıyla entegre edilmiştir.
•	SMS Gateway / Harici OTP Servisleri: Kullanıcıların telefon numaraları ile güvenli giriş yapabilmesi için OTP doğrulama akışı kurgulanmıştır.
4.5. Tasarım ve Versiyon Kontrol Araçları
•	Draw.io & PlantUML: Use-Case, ERD, Sınıf Diyagramları ve UI/UX Bilgi Mimarisi şemalarının çizilmesi için kullanılmıştır.
•	Git & GitHub: Proje kaynak kodlarının versiyon kontrolünün yapılması, ekip içi eşzamanlı çalışma ve teslim sürecinin yönetilmesi için tercih edilmiştir.
Proje mimarisinde ekibimizin halihazırda yetkin olduğu Python, Java, HTML ve CSS teknolojileri tercih edilmiştir. Yeni bir dilin öğrenme süreciyle zaman kaybetmek yerine, bildiğimiz dillerle güvenli, temiz ve bütçe filtreleme odaklı bir arka yüz altyapısı kurulması hedeflenmiştir.
---
### Proje Şemaları ve Görselleri

![Use Case Diyagramı](<img width="523" height="683" alt="Başlıksız Diyagram drawio (1)" src="https://github.com/user-attachments/assets/8ad9288a-ed02-4a0c-a1d1-18546d50a87d" />
)
![ERD Şeması](<img width="1086" height="621" alt="veritbanı drawio" src="https://github.com/user-attachments/assets/bedeb454-f99c-4316-9cfd-ba9ee66974bf" />
)
![Sınıf Diyagramı](<img width="1091" height="953" alt="uml drawio" src="https://github.com/user-attachments/assets/1577f0a5-4c83-456e-9cb8-7c01d07b112c" />
)
![Arayüz Prototipleri](<img width="1160" height="261" alt="uı drawio" src="https://github.com/user-attachments/assets/f9e3867d-c680-466b-a78c-8a59a0ac9889" />
)
 
 







	
