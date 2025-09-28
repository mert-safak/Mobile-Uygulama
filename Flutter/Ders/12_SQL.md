# SQL
## DB Browser
DB Browser ile new database ile yeni bir veritabanı uluşturulur. Tablo oluştur ile tablolar oluşturulur tabloların string integer vb. değerleri seçilir ve urun_id gibi sütunlar primary key yapılır auto seçilir. Foreign key'ler için ise  yabancı anahtar kısmından ilgili tablo ve sütun eklenebilir.

## Browse Data
Bu kısımdan el ile veri eklenebilir. Veri eklenip sağ tarafa değeri yazılıp uygula denilirse veri işlenir.

## Execute SQL
Bu kısımdan kod ile işlem yapılır. Sağ alttan da SQL Günlüğü seçilirse yapılan işlem görülebilir.
### Veri Ekleme
 Örneğin aşağıdaki şekilde veri eklenebilir. Tabloyu tanımlarken urun_id'yi auto seçip  sadece urun_adi ve urun_fiyati girmemiz yeterlidir. urun_id'yi kenisi arttırarak yazar. Kodu yazıp play tuşuna basarsak kod ve tablo eklenir.
```SQL
INSERT INTO urunler(urun_adi,urun_fiyati) VALUES('Telefon',8000)
```
### Veri Değiştirme
Aşağıdaki şekilde veriler güncellenebilir. Güncellerken id kullanılır. Tablodan id değerine bakılabilir.
```SQL
UPDATE urunler SET urun_fiyati=1200 WHERE urun_id=7
```
### Veri Silme
