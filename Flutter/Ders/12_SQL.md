# SQL
## DB Browser
DB Browser ile new database ile yeni bir veritabanı uluşturulur. Tablo oluştur ile tablolar oluşturulur tabloların string integer vb. değerleri seçilir ve urun_id gibi sütunlar primary key yapılır auto seçilir. Foreign key'ler için ise  yabancı anahtar kısmından ilgili tablo ve sütun eklenebilir.

## Browse Data
Bu kısımdan el ile veri eklenebilir. Veri eklenip sağ tarafa değeri yazılıp uygula denilirse veri işlenir.

## Execute SQL Veri Ekleme-Çıkarma
Bu kısımdan kod ile işlem yapılır. Sağ alttan da SQL Günlüğü seçilirse yapılan işlem görülebilir.
### Veri Ekleme
 Örneğin aşağıdaki şekilde veri eklenebilir. Tabloyu tanımlarken urun_id'yi auto seçip  sadece urun_adi ve urun_fiyati girmemiz yeterlidir. urun_id'yi kenisi arttırarak yazar. Kodu yazıp play tuşuna basarsak kod ve tablo eklenir.
```SQL
INSERT INTO urunler(urun_adi,urun_fiyati) VALUES('Telefon',8000)
```
### Veri Değiştirme
Aşağıdaki şekilde veriler güncellenebilir. Güncellerken id(primary key) kullanılır. Tablodan id değerine bakılabilir.
```SQL
UPDATE urunler SET urun_fiyati=1200 WHERE urun_id=7
```
### Veri Silme
Aşağıdaki şekilde veriler sililebilir. Aynı şekilde id(primary key) kullanılır.
```SQL
DELETE FROM urunler WHERE urun_id=5
```

## Execute SQL Veri Okuma
### Tüm Tabloyu Okuma
Aşağıdaki kod ile tüm tablo okunur. * tablodaki tüm alanları getirir.
```SQL
SELECT*FROM urunler
```
### Seçili Sütunları Okuma(SELECT Sorguları)
Burada sadece urun_adi bilgisi okunur.
```SQL
SELECT urun_adi FROM urunler
```
Aşağıda ise urun_adi ve urun_fiyati getirilir.
```SQL
SELECT urun_adi,urun_fiyati FROM urunler
```
Aşağıdaki ise urun_fiyatı=750 olanları seçer.
```SQL
SELECT * FROM urunler WHERE urun_fiyati=750
```
veya ismi TV olanları. String ifadeler için tek tırnak kullanılır.
```SQL
SELECT * FROM urunler WHERE urun_adi = 'TV'
```
Benzer şekilde matematik öperatörleri de kullanılabilir.
```SQL
SELECT * FROM urunler WHERE urun_fiyati>5000
```
Ayrıca karşılaştırma operatörleri de kullanılabilir.
```SQL
SELECT * FROM urunler WHERE urun_fiyati>5000 AND urun_fiyati<9000
```
### Satır Sayısı
Aşağıdaki kod ile satır sayısı gösterilir. Ancak bu şekilde açıklaması count(*) olur.
```SQL
SELECT count(*) FROM urunler
```
Aşağıdaki şekilde yapılır ise açıklama kısmı da toplam olmuş olur.
```SQL
SELECT count(*) as toplam FROM urunler
```
Aşağıdaki şekilde ise urun_fiyati=750 olanların sayısını gösterir.
```SQL
SELECT count(*) as toplam FROM urunler WHERE urun_fiyati=750
```















