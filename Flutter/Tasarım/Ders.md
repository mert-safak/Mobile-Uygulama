# TASARIM AŞAMASI
Öncelikle yeni bir dart file oluşturulur.
## Renk Belirleme
Aşağıdaki kodda 0x hexedecimal olduğunu FF alpha(opacity)değerini belirlir. FF tam görünür 0 görünmez olur. Diğer CB2020 kısmı da RGB kısmıdır. CB kırmızı, 20 yeşil, 20 blue kısmıdır.
 
```
var anaRenk = const Color(0xFFCB2020);
```
## Font Belirleme
Font kullanmak için öncelikle https://fonts.google.com/ gibi bir siteden font(bu sitede hepsi ücretsiz lisanslıdır) indirilir.
Sonra projenin içine bir package oluşturulur ismi fonts olacak şekilde. Sonra indirdiğimiz font'un ttf dosyası buraya kopyalanır. Sonra pubspec.yaml açılarak flutter altına, Aşağıdaki şekilde yazlır. family bizim verdiğimiz isimdir. Programlarken o ismi kullanırız.
```
flutter:
  fonts:
    - family: Pacifico
      fonts:
        - asset: fonts/Pacifico-Regular.ttf
```
Yorum satırıyla yazılmış örneği de mevcuttur taslak olarak kullanılır. Değiştridikten sonra yukardan Pub get seçilir hata alınıyorsa yanlış yazılmış olabilir. Hizalamalar da çok önemlidir hizalamalarda da sorun olmuş olabilir. Tekrar kodlama kısmına geçerken Pubspec has been edited diye bir uyarı çıkabilir. Eminsek ignore edebiliriz.

## Yerleşim seçme
3 farklı şekilde yerleşebilir row(satır), column(sütun), stack(üst üste)

### MainAxisAlignment
Ane eksende hizalama yapar.
start - varsayılan olarak başladığı yerden bitişik hizalar.
end - en sonuna bitişik hizalar.
center - merkeze bitişik hizalar.
spaceBetween- Başlangıç orta ve bitiş olarka hizalar
spaceEvenly - Araya boşluklar atarak hizalar.

### CrossAxisAlignment
Diğer eksende hizalama yapar.
start - varsayılan olarak başladığı yerden bitişik hizalar.
end - en sonuna bitişik hizalar.
center - Ortalayarak başlangıçtan hizalar.
stretch - kendini uzatarak hizalar.

## Resim ekleme
Yine ana klasör altına package eklenim ismi resimler yapılıp resim içerisine atılır. Daha sonra pubspec.yaml içerisine flutter'ın altına aşağıdaki kod eklenirse(örneği pubspec.yaml içerisinde mevcut) pub get denilirse resim yüklenir.
```
flutter:
  assets:
    - resimler/pizza_resim.png
```
Resim hata verirse vb. durdur başlat yapılır( Hot reload bazen sorun yapıyor). Aşağıdaki şekilde anaysayfa içerisine asset eklenebilir. Image.asset kısmı imleç ile seçilip Alt+Enter yapılıp padding seçilrse padding verecek şekilde kodu düzenler.
```
Image.asset("resimler/pizza_resim.png"),
```


