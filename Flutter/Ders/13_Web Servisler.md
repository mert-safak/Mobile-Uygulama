# Web Servisler
## Kütüphane Kurulumu
Öncelikle dio küütphanesi kurulur web servisler ile çalışma yaparken bunu kullanacağız.
```dart
dependencies:
  flutter:
    sdk: flutter
  flutter_bloc:
  dio:
```

## Class'ların Ayarlanması
Classlar veriye göre ayarlanır. Bizim verilerimiz örneğin bu şekilde olsun. İç kisim için ayrı bir class dış kısımdaki kişiler listesi ve success için ayrı bir class oluşturulur.
```json
{
   "kisiler":[
      {
         "kisi_id":"19126",
         "kisi_ad":"mert",
         "kisi_tel":"1234"
      },
      {
         "kisi_id":"19127",
         "kisi_ad":"safak",
         "kisi_tel":"1357"
      },
      {
         "kisi_id":"19128",
         "kisi_ad":"saglam ",
         "kisi_tel":"5678"
      },
      {

   ],
   "success":1
}
```
### İç kısım için class
Öncelikle normal bir class oluşturulur içerisine alacağımız veriler ve constructor'ı oluşturulur ve daha sonra Kisiler.fromJason isimli bir factory oluşturulur. Burada web servisinden gelecek veriler Map içerisinde tutulur. Factory yapılmasının amacı gelen veriler ile bu classdan nesneler oluşturmaktır.
```dart
class Kisiler {
  String kisi_id;
  String kisi_ad;
  String kisi_tel;

  Kisiler({required this.kisi_id, required this.kisi_ad, required this.kisi_tel});

  factory Kisiler.fromJson(Map<String,dynamic> json) {
    return Kisiler(
        kisi_id: json["kisi_id"] as String,
        kisi_ad: json["kisi_ad"] as String,
        kisi_tel: json["kisi_tel"] as String);
  }

}
```
### Dış kısım için class
Burada yine ilk başta gelecek veriler ve constructor'ı oluşturulur ve factory gelen veriler ile nesne oluşturmak için kullanılır. jsonArray.map kısmı for döngüsüne ihtiyaç kalmadan verileri map olarak iç kısım için yazdığımız factyory'ye teker teker gönderir.
```
import 'kisiler.dart';

class KisilerCevap{
  List<Kisiler> kisiler;
  int success;

  KisilerCevap({required this.kisiler, required this.success});

  factory KisilerCevap.fromJson(Map<String,dynamic> json) {
    var jsonArray = json["kisiler"] as List;
    int success = json["success"] as int;

    var kisiler = jsonArray.map((jsonArrayNesnesi) => Kisiler.fromJson (jsonArrayNesnesi)).toList();

    return KisilerCevap(kisiler: kisiler, success: success);
  }
}
```









