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
### Belirli Bir Değere Göre Filtreleme
Aşağıdaki ise urun_fiyatı=750 olanları seçer.
```SQL
SELECT * FROM urunler WHERE urun_fiyati=750
```
veya ismi TV olanları. String ifadeler için tek tırnak kullanılır.
```SQL
SELECT * FROM urunler WHERE urun_adi = 'TV'
```
#### Matematik Oparetörü
Benzer şekilde matematik öperatörleri de kullanılabilir.
```SQL
SELECT * FROM urunler WHERE urun_fiyati>5000
```
#### Karşılaştırma Operatörü
Ayrıca karşılaştırma operatörleri de kullanılabilir.
```SQL
SELECT * FROM urunler WHERE urun_fiyati>5000 AND urun_fiyati<9000
```
#### İçerisinde Geçen Harf/Karaktere Göre Seçme
Burada içerisinde a harfi geçenleri buluyor. % ile başlarsa başlangıç harf/karaktere % ile biterse bitiş harf/karaktere iki tane % arasında olursa içerisinde geçen harf/karaktere göre seçim yapar.
```SQL
SELECT * FROM urunler WHERE urun_adi like '%a%'
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
### Sıralama
#### Ascend Sıralama
Bu şekilde urun_adi değerine göre alfabetik sıralama yapılıp seçilir. 
```SQL
SELECT * FROM urunler ORDER BY urun_adi
```
Bu ve yukardaki aslında aynıdır buna ASC(Ascend) sıralama denir.
```SQL
SELECT * FROM urunler ORDER BY urun_adi ASC
```
#### Descend Sıralama
Tam tersi sıralamak için Descend(DESC) sıralama kullanılır.
```SQL
SELECT * FROM urunler ORDER BY urun_adi DESC
```
Benzer şekilde sayısal da sıralama yapar.
```SQL
SELECT * FROM urunler ORDER BY urun_fiyati DESC
```
### Rastgele Sıralama
Aşağıdaki şekilde rastgele sıralama yapılır. Her çalıştırmada rastgele veri sıralaması gelir.
```SQL
SELECT * FROM urunler ORDER BY RANDOM()
```

### Veri seçerken Limitleme
Veriler seçilirken gelen veri sayısını limitleyebiliriz. Aşağıdaki şekilde sadece 2 veri gelir.
```SQL
SELECT * FROM urunler LIMIT 2
```
Bu şekilde koşul da konulabilir.
```SQL
SELECT * FROM urunler WHERE urun_fiyati>2000 LIMIT 2
```
Rastgele veri seçilirken de limitleme eklenirse örneğin içinden birisi rastgele seçilebilir.
```SQL
SELECT * FROM urunler ORDER BY RANDOM() LIMIT 1
```

## Foreign Key Yapısı
Normalde seçim yaparken bu şekilde foreign keyler kod ile belirtilmelidir. WHERE ve devamında yazılan kısım yazılmazsa matrisleme yapar fazladan veri gelir.  Ancak bu şekilde yapılınca da aynı sütun birkaç kez görilebilir.
```SQL
SELECT * FROM siparisler,urunler,musteriler WHERE siparisler.urun_id=urunler.urun_id AND siparisler.musteri_id=musteriler.musteri_id //Yanlış Kullanım
```










