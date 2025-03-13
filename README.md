# Akbank-Python-ile-Yapay-Zekaya-Giri-Bootcamp

## Proje Tanımı
Bu proje, bir metro ağında iki istasyon arasındaki **en az aktarmalı rotayı** ve **en hızlı rotayı** bulan bir simülasyon geliştirmeyi amaçlar. Graf veri yapısı kullanılarak metro ağı modellenmiş, BFS (Breadth-First Search) algoritması ile en az aktarmalı rota, A* algoritması ile ise en hızlı rota bulunmuştur. Proje, Akbank Python ile Yapay Zekaya Giriş Bootcamp kapsamında hazırlanmıştır.

### Amaçlar
1. Graf veri yapısını kullanarak metro ağını modelleme.
2. BFS algoritması ile en az aktarmalı rotayı bulma.
3. A* algoritması ile en hızlı rotayı bulma.
4. Gerçek dünya problemlerini algoritmik düşünce ile çözme.

## Kurulum ve Çalıştırma
### Gereksinimler
- Python 3.x (math ve standart kütüphaneler dışında ek paket gerekmez)

### Kurulum
1. Proje dosyasını (`AdSoyad_MetroSimulation.py`) bir klasöre kaydedin.
2. Terminal veya komut istemcisini açın ve dosyanın bulunduğu klasöre gidin:
3. Python ile dosyayı çalıştırın

   
### Çıktı
Kod çalıştırıldığında, örnek metro ağı üzerinden üç test senaryosu için sonuçlar ekrana yazdırılır:
- AŞTİ'den OSB'ye
- Batıkent'ten Keçiören'e
- Keçiören'den AŞTİ'ye

## Algoritma Açıklamaları
### 1. BFS (En Az Aktarmalı Rota)
- **Mantık**: Breadth-First Search (BFS), graf üzerinde katman katman ilerleyerek hedefe en az adımda ulaşan rotayı bulur. Metro ağında bu, en az aktarma sayısına karşılık gelir.
- **Çalışma Şekli**:
  1. Başlangıç istasyonu bir kuyruğa (`deque`) eklenir.
  2. Her adımda mevcut istasyonun komşuları keşfedilir ve ziyaret edilmemiş olanlar kuyruğa eklenir.
  3. Hedefe ulaşıldığında, o ana kadarki rota döndürülür.
- **Kod Detayları**: `en_az_aktarma_bul` fonksiyonu, `ziyaret_edildi` seti ile döngüleri önler ve en kısa rotayı listeler.

### 2. A* (En Hızlı Rota)
- **Mantık**: A* algoritması, toplam maliyeti (`f(n) = g(n) + h(n)`) minimize ederek en hızlı rotayı bulur:
  - `g(n)`: Başlangıçtan mevcut istasyona kadarki gerçek süre.
  - `h(n)`: Mevcut istasyondan hedefe tahmini süre (heuristik).
- **Heuristik**: Euclidean mesafe (koordinatlar arası düz mesafe) kullanıldı. Bu, gerçek süreye bir alt sınır sağlar ve A*’ın etkinliğini artırır.
- **Çalışma Şekli**:
  1. Öncelik kuyruğu (`heapq`) ile en düşük `f_skoru`na sahip yollar önceliklendirilir.
  2. Her komşu için `g_skoru` (gerçek süre) ve `h_skoru` (tahmini süre) hesaplanır.
  3. Hedefe ulaşıldığında, rota ve toplam süre döndürülür.
- **Kod Detayları**: `en_hizli_rota_bul` fonksiyonu, `g_skorlari` ile en iyi süreleri takip eder ve döngüleri önler.

## Test Senaryoları ve Çıktılar
Aşağıda, örnek metro ağı için test sonuçları verilmiştir:

### 1. AŞTİ'den OSB'ye
- **En Az Aktarmalı Rota**: AŞTİ -> Kızılay -> Demetevler -> OSB
- **En Hızlı Rota**: AŞTİ -> Kızılay -> Demetevler -> OSB (18 dakika)

### 2. Batıkent'ten Keçiören'e
- **En Az Aktarmalı Rota**: Batıkent -> Demetevler -> Gar -> Keçiören
- **En Hızlı Rota**: Batıkent -> Demetevler -> Gar -> Keçiören (21 dakika)

### 3. Keçiören'den AŞTİ'ye
- **En Az Aktarmalı Rota**: Keçiören -> Gar -> AŞTİ
- **En Hızlı Rota**: Keçiören -> Gar -> Sıhhiye -> Kızılay -> AŞTİ (16 dakika)

### Notlar
- En hızlı rota, aktarma sayısından bağımsız olarak toplam süreyi optimize eder.
- Koordinatlar hayali olarak atanmıştır; gerçek bir metro ağı için daha doğru veriler kullanılabilir.

## Kod Yapısı
- **`Istasyon` Sınıfı**: İstasyonları temsil eder (idx, ad, hat, koordinatlar ve komşular).
- **`MetroAgi` Sınıfı**: Metro ağını yönetir, istasyon ve bağlantı ekleme ile rota bulma fonksiyonlarını içerir.
- **Ana Kod**: Örnek ağ oluşturur ve test senaryolarını çalıştırır.

## Geliştirme Önerileri
- Gerçek metro haritası verileriyle koordinatları güncelleme.
- Görselleştirme ekleme (örneğin, matplotlib ile rota çizimi).
- Daha fazla test senaryosu ile algoritma doğruluğunu artırma.

## Katkıda Bulunanlar
EMRE KONÇE

-
