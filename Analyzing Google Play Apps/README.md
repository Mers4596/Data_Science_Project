📊 Google Play Apps Veri Analizi Projesi
========================================

Bu proje, Google Play Store uygulama veri seti üzerinde **Veri Temizleme (Data Preprocessing)**, **Keşifsel Veri Analizi (EDA)** ve **Makine Öğrenmesine Hazırlık** adımlarını kapsamlı şekilde uygulamak amacıyla hazırlanmıştır.

Notebook içerisinde ham verinin analiz edilmesi, dönüştürülmesi ve görselleştirilmesi süreçleri uçtan uca ele alınmıştır.

🧠 Proje Amacı
--------------

Bu çalışmanın temel amacı:

*   Ham veri setini analiz etmek
    
*   Veri tiplerini düzenlemek
    
*   Eksik ve hatalı verileri temizlemek
    
*   Kategorik ve sayısal değişkenleri incelemek
    
*   Görselleştirmeler ile içgörü elde etmek
    
*   Veri setini makine öğrenmesi modellerine hazır hale getirmek
    

🗂️ Kullanılan Veri Seti
------------------------

*   **Kaynak:** Google Play Store Apps Dataset
    

**İçerik:**

*   Uygulama adı
    
*   Kategori
    
*   Puan (Rating)
    
*   Yorum sayısı
    
*   Boyut
    
*   İndirilme sayısı
    
*   Fiyat
    
*   Tür (Free / Paid)
    
*   İçerik derecelendirmesi
    
*   Son güncelleme tarihi
    
*   Android sürüm bilgisi
    

⚙️ Kullanılan Teknolojiler
--------------------------

*   Python
    
*   Pandas
    
*   NumPy
    
*   Matplotlib
    
*   Seaborn
    
*   Jupyter Notebook
    

🧹 Veri Ön İşleme (Data Preprocessing)
--------------------------------------

### 1️⃣ Reviews Kolonu

*   Sayısal olmayan değerler tespit edildi
    
*   Hatalı satırlar veri setinden çıkarıldı
    
*   Veri tipi **int** formatına dönüştürüldü
    

### 2️⃣ Size Kolonu

Yapılan işlemler:

*   M → 000 dönüşümü yapıldı
    
*   k karakteri kaldırıldı
    
*   "Varies with device" değerleri **NaN** yapıldı
    
*   Kolon **float** tipine çevrildi
    

### 3️⃣ Installs Kolonu

Dönüşümler:

*   \+ ve , karakterleri temizlendi
    
*   Sayısal formata dönüştürüldü (**int**)
    

### 4️⃣ Price Kolonu

*   $ işareti kaldırıldı
    
*   **float** veri tipine çevrildi
    

### 5️⃣ Tarih Verisi İşleme

*   Last Updated kolonu **datetime** formatına dönüştürüldü
    
*   Yıl bilgisi ayrı kolon olarak üretildi
    

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   df_clean['Year'] = df_clean['Last Updated'].dt.year   `

🔎 Keşifsel Veri Analizi (EDA)
------------------------------

### 📌 Duplicate Analizi

*   Aynı uygulamaya ait tekrar eden kayıtlar tespit edildi
    
*   App kolonuna göre tekrar eden veriler silindi
    

### 📊 Sayısal Değişken Analizi

*   KDE dağılım grafikleri oluşturuldu
    
*   İncelenen değişkenler:
    
    *   Rating
        
    *   Reviews
        
    *   Size
        
    *   Installs
        

### 📊 Kategorik Değişken Analizi

İncelenen başlıca değişkenler:

*   Category
    
*   Genres
    
*   Type
    
*   Content Rating
    

Bar grafikleri ile dağılımlar görselleştirildi.

### 📈 İndirilme Analizleri

Yapılan çalışmalar:

*   Kategori bazlı toplam indirilme sayısı
    
*   En çok indirilen ilk 10 kategori
    
*   Uygulama + kategori kırılımı analizleri
    

### ⭐ Rating Analizleri

*   Kategori + uygulama bazlı ortalama puan hesaplandı
    
*   İndirilme sayısı ile puan ilişkisi incelendi
    

🤖 Android Versiyon Temizliği
-----------------------------

Yapılan işlemler:

*   "and up" ifadeleri temizlendi
    
*   "Varies with device" değerleri kaldırıldı
    
*   Aralık belirten sürümler veri setinden çıkarıldı
    

🧬 Feature Engineering
----------------------

### Genres Encoding

*   Tür bazlı ortalama indirilme sayısı hesaplandı
    
*   Milyon ölçeğine normalize edildi
    
*   Sayısal encoding kolonu oluşturuldu
    

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   df_clean['Genres Encoded'] = df_clean['Genres'].map(main_genres_encoded)   `

💾 Çıktı Alma
-------------

Temizlenmiş veri seti CSV olarak dışarı aktarıldı:

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   df_clean.to_csv("ml_ready_dataset.csv", index=False)   `

Bu çıktı, makine öğrenmesi projelerinde doğrudan kullanılabilecek formata getirilmiştir.

📌 Proje Kazanımları
--------------------

Bu proje ile:

*   Veri temizleme pratiği kazanıldı
    
*   Gerçek dünya veri seti üzerinde çalışıldı
    
*   EDA becerileri geliştirildi
    
*   Feature engineering uygulandı
    
*   ML öncesi veri hazırlama süreci öğrenildi
    

🚀 Geliştirme Fikirleri
-----------------------

Projeyi ilerletmek için:

*   Rating tahmin modeli kurulabilir
    
*   Uygulama başarı skoru üretilebilir
    
*   Fiyatlandırma analizi yapılabilir
    
*   Tavsiye sistemi geliştirilebilir
    

Dataset Reference & Usage

This project utilizes the Google Play Store Apps dataset created and published by L. Gupta (2019) on Kaggle.

The dataset contains detailed information about mobile applications available on the Google Play Store, including attributes such as category, rating, size, installs, pricing, and other relevant metadata. It was collected through web scraping techniques applied to the Google Play Store, where dynamic page loading mechanisms make large-scale data extraction more complex compared to other app marketplaces.

This dataset was used strictly for educational, analytical, and research purposes within the scope of this project. All credits belong to the original dataset author and source platform.

Citation:

L. Gupta, “Google Play Store Apps,” Feb 2019. \[Online\]. Available:

https://www.kaggle.com/lava18/google-play-store-apps

Veri Seti Kaynağı ve Kullanımı

Bu projede, L. Gupta (2019) tarafından oluşturulup Kaggle platformunda yayımlanan Google Play Store Apps veri seti kullanılmıştır.

Veri seti; Google Play Store’da yer alan mobil uygulamalara ait kategori, puan, boyut, indirme sayısı, fiyat ve benzeri birçok özelliği içermektedir. Söz konusu veriler, Google Play Store sayfalarından web scraping yöntemleri ile elde edilmiştir. Google Play Store’un dinamik sayfa yükleme altyapısı nedeniyle veri çıkarma süreci, diğer uygulama mağazalarına kıyasla daha karmaşıktır.

Bu veri seti proje kapsamında yalnızca eğitimsel, analitik ve araştırma amaçlı kullanılmış olup, tüm hak ve atıf veri setinin orijinal sahibine aittir.

Atıf:

L. Gupta, “Google Play Store Apps,” Şubat 2019. \[Çevrimiçi\]. Erişim:

https://www.kaggle.com/lava18/google-play-store-apps
