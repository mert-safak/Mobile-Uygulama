# DEĞİŞKENLER  
## Değişken Tanımlama
```dart
var yas = 31;
```
veya

```dart
int yas = 31;
```

## Print
$ işareti ile değişkenler print içerisine yazılabilir.
```dart
int urun_id = 3416;
print("ürün id : $urun_id");
```
Köşeli parantez içerisinde $ ile yazılan kısma parantez açar
```dart
int a = 10;
var b = 20;
print("$a ve $b'nin toplamı : ${a+b}");
```

## Birden Fazla Değişken Oluşturma
```dart
var s1,s2,s3;
s1 = 10;
s2 = 20;
s3 = 30;
```
veya
```dart
int k1 = 44,k2 = 78;
```

## Tür dönüşümleri
Normalde dönüşümlerde x.toInt(), y.toDouble(), z.toString() dönüşümleri kullanılabilir. Ama int ve double dönüşümü sadece sayıdan sayıya dönüştürür. Metinden sayıya dönüşümlerde parse metodu kullanılır

### Metinden Sayısala
  ````dart
  String yazi1 = "34";
  String yazi2 = "34.67";

  int s1 = int.parse(yazi1);
  double s2 = double.parse(yazi2);
````
## Konsol Girdisi
Aşağıdaki gibi stdin.readLineSycn() çağırılır. Nullable kontrolü yapar bu yüzden sonuna ! konulur. Ayrıca her zaman konsoldan alınan veri stringdir. Tür dönüşümü yapmak gerekebilir.
```dart
  print("Adınızı giriniz");
  
  String isim = stdin.readLineSync()!;

  print("Adınız : $isim");
```
