Öncelikle yeni bir dart file oluşturulur.
 Aşağıdaki kodda 0x hexedecimal olduğunu FF alpha(opacity)değerini belirlir. FF tam görünür 0 görünmez olur. Diğer CB2020 kısmı da RGB kısmıdır. CB kırmızı, 20 yeşil, 20 blue kısmıdır.
 
```
var anaRenk = const Color(0xFFCB2020);
```

Font kullanmak için öncelikle https://fonts.google.com/ gibi bir siteden font(bu sitede hepsi ücretsiz lisanslıdır) indirilir.
Sonra projenin içine bir package oluşturulur ismi fonts olacak şekilde. Sonra indirdiğimiz font'un ttf dosyası buraya kopyalanır. Sonra pubspec.yaml açılarak flutter altına, Aşağıdaki şekilde yazlır. 
```
flutter:
  fonts:
    - family: Pacifico
      fonts:
        - asset: fonts/Pacifico-Regular.ttf
```
Yorum satırıyla yazılmış örneği de mevcuttur taslak olarak kullanılır. Değiştridikten sonra yukardan Pub get seçilir hata alınıyorsa yanlış yazılmış olabilir.
