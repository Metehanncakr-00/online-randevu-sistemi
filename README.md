📅 KVKK Uyumlu Online Randevu & Güvenli Kapora Tahsilat SistemiCanlı Demo • Özellikler • Test Kartları • Kurulum • Veritabanı Mimarisi💡 Projenin AmacıTürkiye'de hizmet veren bağımsız profesyonellerin (hukuk büroları, klinikler, psikologlar, mali müşavirler) en büyük operasyonel kaybı alınan randevulara gelinmemesi (no-show) ve KVKK mevzuatına uyumsuz randevu toplama süreçleridir.Bu proje:6698 Sayılı KVKK Kanunu'na tam uyumlu aydınlatma metni ve açık rıza mekanizması sunar.Randevu kesinleştirme aşamasında 50 TL güvence kaporası tahsil ederek ciddiyetsiz randevuları engeller.Sunucu maliyeti olmadan (Serverless), Supabase PostgreSQL ve iyzico Sandbox entegrasyonuyla 7/24 kesintisiz çalışır.✨ Öne Çıkan Özellikler🛡️ 6698 Sayılı KVKK Tam Uyumu:Özel aydınlatma metni modalı ve zorunlu kullanıcı onay mekanizması.Onaylanmayan formların gönderilmesini engelleyen görsel uyarı sistemi.💳 iyzico 3D Secure Kapora Tahsilatı:Gerçek zamanlı kart numarası formatlama (otomatik boşluk bırakma).3D Secure SMS doğrulama simülasyonu (123456).Başarılı ödemelerde provizyon fişi ve işlem takip kodu üretimi.🗄️ Supabase PostgreSQL Backend:Güvenli Row Level Security (RLS) politikalarıyla korunan veri akışı.randevular ve odemeler tabloları arasında dinamik ilişkilendirme.📱 Mobile-First & Modern Arayüz:Tailwind CSS ile hazırlanan, her ekran boyutuna (telefon, tablet, masaüstü) tam duyarlı tasarım.Tıklanabilir dinamik saat dilimleri (09:30, 10:30, 11:30 vb.).Geçmiş günlere randevu alınmasını engelleyen akıllı takvim kısıtı.🌍 Canlı DemoWeb sitemiz Vercel altyapısı üzerinde SSL korumalı olarak yayındadır:👉 Canlı Site: https://online-randevu-sistemi.vercel.app (Kendi Vercel linkinizi buraya ekleyebilirsiniz)🧪 Test Kart Bilgileri (iyzico Sandbox)Sistemi gerçek kredi kartı kullanmadan test edebilmeniz için tanımlanmış resmi test kartları:DurumKart NumarasıSon KullanmaCVC3D SMS KoduBeklenen SonuçBaşarılı İşlem5890 0400 0000 001612/30123123456✅ Randevu onaylanır, odemeler tablosuna 50 TL kayıt düşer.Yetersiz Bakiye5890 0400 0000 002412/30123-❌ Ödeme reddedilir, kullanıcıya bakiye uyarısı verilir.💡 İpucu: Ödeme ekranındaki "Kartı Doldur ⚡" butonuna basarak başarılı test kartını tek tıkla otomatik doldurabilirsiniz.🏛️ Veritabanı ŞemasıProje, Supabase (PostgreSQL) üzerinde ilişkisel 3 temel tablo barındırır:erDiagram
    RANDEVULAR ||--o{ ODEMELER : "randevu_id"
    RANDEVULAR {
        uuid id PK
        string isim
        string soyisim
        string telefon
        string email
        date randevu_tarihi
        string randevu_saati
        string durum
        boolean kvkk_onay
        timestamp created_at
    }
    ODEMELER {
        uuid id PK
        uuid randevu_id FK
        decimal tutar
        string odeme_durumu
        string iyzico_token
        timestamp created_at
    }
    CALISMA_SAATLERI {
        uuid id PK
        string gun
        time baslangic_saati
        time bitis_saati
    }
🚀 Kurulum ve Yerel ÇalıştırmaProjeyi kendi bilgisayarınızda yerel olarak çalıştırmak için:1. Depoyu Klonlayıngit clone https://github.com/Metehanncakr-00/online-randevu-sistemi.git
cd online-randevu-sistemi
2. Supabase Veritabanını Hazırlayınsupabase.com üzerinde ücretsiz bir proje oluşturun.Sol menüdeki SQL Editor bölümüne gidin.Projede paylaşılan schema.sql dosyasının içeriğini yapıştırıp Run butonuna basarak tabloları ve RLS izinlerini oluşturun.3. API Anahtarlarını Tanımlayınindex.html dosyasını favori metin düzenleyicinizle açın ve alt kısımda bulunan Supabase bilgilerinizi girin:const SUPABASE_URL = 'https://PROJE_KODUNUZ.supabase.co';
const SUPABASE_ANON_KEY = 'sb_publishable_...';
4. Tarayıcıda BaşlatınEk bir derleyiciye veya Node.js kurulumuna gerek yoktur. index.html dosyasına çift tıklayarak doğrudan Chrome veya Edge üzerinde sistemi deneyimleyebilirsiniz.🛠️ Kullanılan TeknolojilerFrontend: HTML5, Modern Vanilla JS (ES6+)Tasarım & UI: Tailwind CSS CDN, Inter Typography, HeroiconsVeritabanı & Backend: Supabase (PostgreSQL 15), Supabase JS Client v2Ödeme Altyapısı: iyzico Sandbox REST API SimülasyonuDağıtım (Deployment): Vercel & GitHub Actions (CI/CD)📄 LisansBu proje MIT Lisansı kapsamında açık kaynak olarak paylaşılmıştır. Dilediğiniz gibi ticari veya kişisel projelerinizde kullanabilir ve geliştirebilirsiniz.
