# NESNE TABANLI PORGRAMLAMA
## Kalıtım(Miras)
Miras almak istediğimiz sınıfı extends olarak ekleriz ve super anahtarı ile özelliğini ekleriz
```
class Saray extends Ev {
  int kule_sayisi;

  Saray({required this.kule_sayisi}) : super(pencereSayisi : 100);
}
```
 Veya değer default olarak verilmek istenmiyorsa aşağıdaki şekilde yapılabilir.
 ```
import 'ev.dart';

class Saray extends Ev {
  int kule_sayisi;

  Saray({required this.kule_sayisi, required int pencereSayisi}) : super(pencereSayisi : pencereSayisi);
}
```
