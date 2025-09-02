# WIDGET KODLAMA TEKNİKLERİ
## Görünmezlik Widget'ı
Text widget'ını imleç ile seçip alt+enter yapılır. Wrap with widget seçilir çünkü listede Visibility widget yoktur.
Sonra Visibility yazılıp seçilir. Devamında ise içerisine child: ile tanımlı widget'tan önce visible:true veya visible:falsa yazılır. Bool tutan bir değişken de yazılabilir. Örneğin burada kontrol değişkeni yazılmıştır.
```
Visibility(visible: kontrol, child: Text("Merhaba")),
```
