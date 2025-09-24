Öncelikle lib klasörüne sağ tıklanır "anasayfa" veya başka bir isimde dart file oluşturulur. Sonra anasayfa dosyasında st yazılarak stful bir sayfa oluşturulur. Oluşan class'a anasayfa ismi verilir ve ilk satırdaki StatefulWidget'ın sondaki "et" kısmı silinir ve tekrar yazılıp metarial dart olan seçilir. 
Daha sonra main.dart'a gelinir ve class MyHomePage'dan itibaren aşağı doğru tamamı silinir. Sonra aradaki yorum satırları silinir. Sonra en altta kalan myHomePage silinerek yerine Anasayfa yazılıp seçilir ve bu sayede ilk açılan sayfa değiştirilmiş olur. Sonra MyHomePage(title: 'Flutter Demo Home Page') kısmı da silinerek yerine Anasayfa yazılır ve çıkan seçililir. En sonda ise const Placeholder() yazan yer silinir ve Scaffold yazılıp seçilir. En son ise debug yazısının gitmesi için ilgili kısma debugShowCheckedModeBanner: false yazılır
```dart
class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'Flutter Demo',
      theme: ThemeData(
```
