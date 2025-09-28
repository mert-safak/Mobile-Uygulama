# Shared Preferences 
Key-Value ile veri saklar. String, int, double, bool, list tipinde veri saklar. Uygulama silinirse veriler de silinir.

## Shared Preference Kullanımı
Aşağıdaki şekilde bir Future tanımlanır.. sp değişkeni oluşturulur ve SharedPreferences.getInstance() sınıfı bir nesneye eşitlenir. Performanslı olması için bu gibi işlemlerde await kullanılır.  SetString,SetInt bunlar veri kaydeder. getString vb. ise veri okur.

```
Future<void> test() async {
    var sp = await SharedPreferences.getInstance();

    // Veri Kaydı
    sp.setString("ad", "mert");

    // Veri Silme

    //Veri Okuma
    String gelenAd =  sp.getString("ad") ?? "isim yok";
    print("Gelen Ad: $gelenAd");
  }
```
