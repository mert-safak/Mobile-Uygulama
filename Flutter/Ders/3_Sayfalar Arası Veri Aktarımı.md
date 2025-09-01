Stateful bir sayfadan üstteki StatefulWidget'a kşöeli parantezden sonra değişkenler tanımlanır. Daha sonra kendi constructoru silinir ve generate ile tüm yazılanlar constructor olarak işaretlenir ok denilir. Yapı Aşağıdaki gibi olur.
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
