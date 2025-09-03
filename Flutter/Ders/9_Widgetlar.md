# WIDGET'LAR
## TextField
Öncelikle TextField'da yazılan verileri tutmak için _ ile başlayan sayfa class'ı altına bir değişken tanımlarız. Dceoration kısmı içeri yazılan metin kısmının ayarlarıdır. keyboardType ile kullanıcıya nasıl bir klavye açılacağını belirleriz. obscureText ise şifre yazar gibi yazılanı gizlemeye yarar
```
class _AnasayfaState extends State<Anasayfa> {
  var tfController = TextEditingController(); //Kullanıcıdan alınan veriyi tutmak için controller
  String alinanVeri = ""; //Alınan veriyi ekrana yazdırmak için tuttuğumuz değişken
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text("Widgets"),),
      body: Center(
        child: Column(
          children: [
            Text("$alinanVeri"),
            TextField(
              controller: tfController, //Tanımladığımız controller
              decoration: const InputDecoration(hintText: "Veri"), //Hint ile ilgili ayarlar
              keyboardType: TextInputType.number, //Burada kullanıcıya sayısal bir klavye açılır
              obscureText: true, //Bu özellik ile yazılar şifre girer gibi gizli bir şekilde açılır
              ),
          ],
        ),
      ),
    );
  }
}
```
## ElevatedButton
Eğer bu button da eklenirse butona basınca veriyi alır ve ekranda gösterir. İsmini TextButton olarak değiştirirsek de çerçevesiz sadece yazı olan bir button çıkar.
```
            ElevatedButton(onPressed: (){
              setState(() {
                alinanVeri = tfController.text;
              });
            }, child: const Text("Veriyi Al"),
            ),
```
## Resim Gösterme
Öncelikle ana paketin üzerine bir klasör oluşturulur tercihen ismi resimler. Sonra resimler bu klasörün içerisine atılır. Lib klasörünün içinde olursa resimler görünmez ana paketin altında olacak klasör. Daha sonra resimler klasörünün pubspec.yaml içerisine eklenmesi gerekir bunun için ilgili satıra assets: ve altına klasör aşağıdaki şekilde yazılır boşluklar ve girintiler çok önemlidir. Bu yüzden true'dan sonra enter'a basılır assets: yazılıp tekrar enter'a basılır ve - koyulup boşluk bırakılıp klasör yazılır sonuna / konulur.
```
  uses-material-design: true

  assets:
    - resimler/
```
