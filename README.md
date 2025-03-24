# Metro Ağı Rota Optimizasyonu

Bu proje, bir metro ağında **en az aktarmalı** veya **en hızlı rotayı** bulmak için *BFS  ve A** algoritmalarından *\* faydalanmaktadır. Kullanıcıların metro ağındaki en uygun rotayı bulmasını sağlar.

## Kullanılan Teknolojiler ve Kütüphaneler

Bu projede aşağıdaki Python kütüphanelerini kullanılmaktadır:

- `collections.deque`: BFS algoritması için kuyruk veri yapısını oluşturmak için kullanılır.
- `heapq`: A\* algoritması için öncelikli kuyruğu yönetmek amacıyla kullanılır.
- `defaultdict`: Metro hatlarını ve istasyonları saklamak için kullanılır.
- `typing`: Kodun daha okunaklı ve anlaşılır olması için tür ipuçları sağlar.

## Algoritmaların Çalışma Mantığı

### BFS Algoritması (En Az Aktarmalı Rota)

**Genişlik Öncelikli Arama (BFS)**, istasyonlar arasındaki **en az aktarmalı rotayı** bulmayı sağlamaktadır. Algoritma aşağıdaki adımlarla çalışır:

1. Başlangıç istasyonundan başlayarak bir kuyruk oluşturur.
2. Her istasyonda komşularını keşfeder ve kuyruk içine ekler.
3. Hedef istasyona ulaşıldığında, en az aktarma gerektiren yol bulunmuş olur.

**Neden BFS?**

- Özellikle **en kısa yolu** bulmak için idealdir çünkü bir grafı katman katman keşfeder.
- Ağırlıklandırılmamış (her geçiş eşit kabul edilen) graf yapılarında **en az adımda ulaşımı** sağlar.

### A\* Algoritması (En Hızlı Rota)

*A** Algoritması*\*, her istasyon arasındaki **seyahat süresi** dikkate alınarak en hızlı rotanın bulunması amacıyla kullanılır. Algoritma aşağıdaki adımlarla çalışır:

1. **Öncelikli kuyruk (priority queue)** kullanarak başlangıç noktasını işler.
2. Her istasyon için en düşük maliyete sahip (en hızlı) yolu hesaplar.
3. Hedefe ulaştığında en kısa süreyi veren rota gösterilir.

*Neden A**?*\*

- **BFS gibi körü körüne tüm yolları denemek yerine**, **öncelik sırasına göre** en iyi rotayı değerlendirir.
- Gerçek dünyadaki **optimizasyon problemlerine uygun** bir algoritmadır.

## Örnek Kullanım ve Test Sonuçları

Aşağıda, **örnek metro hattı ve bazı test senaryoları** verilmiştir.

**Metro Ağı:**

```
Kırmızı Hat: Kızılay -> Ulus -> Demetevler -> OSB
Mavi Hat: AŞTİ -> Kızılay -> Sıhhiye -> Gar
Turuncu Hat: Batıkent -> Demetevler -> Gar -> Keçiören
```

### 1. AŞTİ -> OSB (BFS ile en az aktarmalı rota)

```python
rota = metro.en_az_aktarma_bul("M1", "K4")
```

Çıktı:

```
En az aktarmalı rota: AŞTİ -> Kızılay -> Ulus -> Demetevler -> OSB
```

### 2. AŞTİ -> OSB (A\* ile en hızlı rota)

```python
rota, sure = metro.en_hizli_rota_bul("M1", "K4")
```

Çıktı:

```
En hızlı rota (15 dakika): AŞTİ -> Kızılay -> Demetevler -> OSB
```

## Projeyi Geliştirme Fikirleri

- **Metro hatları için görselleştirme**: Matplotlib kullanarak metro ağını grafiksel olarak gösterilebilir
- **Farklı ulaşım modlarının eklenmesi**: Otobüs, tren ve tramvay gibi ulaşım araçları da entegre edilerek tüm şehir içi ulaşım optimizasyonu sağlanabilir.
- **Metro Veri Analitiği ve Optimizasyon**: Yolcu yoğunluğu ve güzergah verilerini analiz ederek daha verimli hat planlaması sağlar. Bu sayede sefer aralıkları ve kapasite yönetimi iyileştirilir.
