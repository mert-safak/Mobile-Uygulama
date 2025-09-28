# Shared Preferences 
Key-Value ile veri saklar. String, int, double, bool, list tipinde veri saklar. Uygulama silinirse veriler de silinir. Sadece string türünde liste kabul eder.

## Shared Preference Kullanımı
Aşağıdaki şekilde bir Future tanımlanır.. sp değişkeni oluşturulur ve SharedPreferences.getInstance() sınıfı bir nesneye eşitlenir. Performanslı olması için bu gibi işlemlerde await kullanılır.  .SetString(),SetInt() bunlar veri kaydeder. .getString() vb. ise veri okur. Veri okurken nullable uyarısı verir. ?? yanında veri yazılarak veri gelmemesi durumunda gelecek veri yazılır.
.remove() ile de kayıtlı veri sinilir. İşlemler yapılırken parantez içine key değeri yazılır.

```dart
Future<void> test() async {
    var sp = await SharedPreferences.getInstance();

    // Veri Kaydı
    sp.setString("ad", "mert");

    // Veri Silme
    sp.remove("ad");
    //Veri Okuma
    String gelenAd =  sp.getString("ad") ?? "isim yok";
    print("Gelen Ad: $gelenAd");
  }
```
## Çeşitli kullanım Şekilleri
```dart
Future<void> test() async {
    var sp = await SharedPreferences.getInstance();

    // Veri Kaydı
    sp.setString("ad", "mert");
    sp.setInt("yas", 23);
    sp.setDouble("boy", 1.78);
    sp.setBool("bekar", true);

    var arkadasListesi = <String>[];
    arkadasListesi.add("şafak");
    arkadasListesi.add("sağlam");
    sp.setStringList("arkadasListesi", arkadasListesi);

    // Veri Silme
    //sp.remove("ad");
    //Veri Okuma
    String gelenAd =  sp.getString("ad") ?? "isim yok";
    int gelenYas =  sp.getInt("yas") ?? 0;
    double gelenBoy =  sp.getDouble("boy") ?? 0.0;
    bool gelenBekar =  sp.getBool("bekar") ?? false;
    print("Gelen Ad: $gelenAd");
    print("Gelen Yaş: $gelenYas");
    print("Gelen Boy: $gelenBoy");
    print("Gelen Bekar: $gelenBekar");

    var gelenArkadasListesi = sp.getStringList("arkadasListesi") ?? <String>[];

    if(gelenArkadasListesi != null){
      for(var a in gelenArkadasListesi){
        print("Arkadaş : $a");
      }
    }
  }
```
