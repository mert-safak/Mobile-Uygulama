# NESNE TABANLI PORGRAMLAMA
## Kalıtım(Miras)
Miras almak istediğimiz sınıfı extends olarak ekleriz ve super anahtarı ile özelliğini ekleriz
```dart
class Saray extends Ev {
  int kule_sayisi;

  Saray({required this.kule_sayisi}) : super(pencereSayisi : 100);
}
```
 Veya değer default olarak verilmek istenmiyorsa aşağıdaki şekilde yapılabilir.
 ```dart
import 'ev.dart';

class Saray extends Ev {
  int kule_sayisi;

  Saray({required this.kule_sayisi, required int pencereSayisi}) : super(pencereSayisi : pencereSayisi);
}
```
## Upcasting ve Downcasting
 Upcasting üst class'a dönüştürür downcasting ile alt class'a
 ```dart
  //Downcasting
  var ev  = Ev(pencereSayisi: 10);
  var saray = ev as Saray;

  //Upcasting
  var s = Saray(kule_sayisi: 3, pencereSayisi: 100)
  Ev e = s;
```
