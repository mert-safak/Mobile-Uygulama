Stateful bir sayfadan üstteki StatefulWidget'a kşöeli parantezden sonra değişkenler tanımlanır. Daha sonra kendi constructoru silinir ve generate ile tüm yazılanlar constructor olarak işaretlenir ok denilir. Yapı Aşağıdaki gibi olur. İstenirse hepsi seçilip AltGr+7 ile köşeli parantez uapılıp required'ler yazılır.
```
class OyunEkrani extends StatefulWidget {
  String ad;
  int yas;
  double boy;
  bool bekar;
  OyunEkrani({required this.ad, required this.yas, required this.boy, required this.bekar});

  @override
  State<OyunEkrani> createState() => _OyunEkraniState();
}
```
 widget.ad, widget.yas diyerek o verilere erişebiliriz
 ```
Text("${widget.ad} - ${widget.yas} - ${widget.boy} - ${widget.bekar}"),
```
Anasayfa hata vermektedir. Sebebi az önce oluşturduğumuz veriler constructor olarak oluşturuldu. Navigator'deki sayfa yapısı değişti . Bu yüzden silinip tekrar yazılıp seçilir. Aşağıdaki örnekteki gibi Navigator ile birlikte gönderilir.
```
Navigator.push(context, MaterialPageRoute(builder: (context) => OyunEkrani(ad: "mert", yas: 31, boy: 177, bekar: false),));
```
