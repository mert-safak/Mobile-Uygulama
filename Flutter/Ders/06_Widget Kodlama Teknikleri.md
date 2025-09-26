# WIDGET KODLAMA TEKNİKLERİ
## Görünmezlik Widget'ı
Text widget'ını imleç ile seçip alt+enter yapılır. Wrap with widget seçilir çünkü listede Visibility widget yoktur.
Sonra Visibility yazılıp seçilir. Devamında ise içerisine child: ile tanımlı widget'tan önce visible:true veya visible:falsa yazılır. Bool tutan bir değişken de yazılabilir. Örneğin burada kontrol değişkeni yazılmıştır.
```dart
Visibility(visible: kontrol, child: Text("Merhaba")),
```
## Tek Satırlık Koşul Oluşturma
kontrol değişkeni bool değer alır. True iken sol taraf false iken sağ taraf çalışır
```dart
Text(kontrol ? "Merhaba" : "Güle Güle"),
```
### İçerisindeki style vb. öğelere de uygulama
Aşağıdaki gibi TextStyle'da color'da bu şekilde tru false olarak koşula bağlanmıştır.
```dart
Text(kontrol ? "Merhaba" : "Güle Güle",style: TextStyle(color: kontrol ? Colors.blue : Colors.red) ,),
```
