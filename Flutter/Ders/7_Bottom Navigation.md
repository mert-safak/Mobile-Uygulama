# BOTTOM NAVIGATION
Örneğin elimizde 3 Sayfamız olsun temel mantık şudur 4. bir sayfa oluşturulur ve diğer sayfalar bottom navigation olan sayfanın body kısmında gösterilir. Bu sayede her sayfa için baştan bottom navigation yapmaya gerek kalmaz.

## Bottom Navigation Tasarım Kısmı
Öncelikle Bottom Navigation Tasarımını Oluşturalım. Bottom Navigation olan sayfanın body kısmınıa direkt body: const Sayfa1(), şeklinde yazarsak direk ilgili sayfa gösterilir. Yukarda da belirtildiği gibi amaç bottom navigationı ayrı bir sayfa gibi gösterip içerisinde sayfa göstermektir. Örneğin
```
return Scaffold(
      appBar: AppBar(title: const Text("Bottom Navigation"),),
      body: const SayfaBir(),
```
Devamında ise bottomNavitaionBar eklenir. İçerisine liste olarak items'lar alır. currentIndex hangi indexteki item'ın seçili olduğunu söyler. onTap ise bir callBack'tir. Tıklanan indexi yakalamak için kullanılır. Hangi indexe tıklandıysa onu verir bize.
Aşağıdaki şekilde BottomNavigationBar içerisinde BottomNavigationBarItem'lar oluşturulup liste halinde verilir ve current index
tanımlanır tanımlanmazsa default=0'dır. onTap tanımlanmazsa tıklamyı yakalayamayız.
Sadece görsel hali aşağıdadır
```
    return Scaffold(
      appBar: AppBar(title: const Text("Bottom Navigation"),),
      body: SayfaBir(),
      bottomNavigationBar: BottomNavigationBar(items: const [
        BottomNavigationBarItem(icon: Icon(Icons.looks_one_outlined),label: "Bir" ),
        BottomNavigationBarItem(icon: Icon(Icons.looks_two_outlined),label: "iki" ),
        BottomNavigationBarItem(icon: Icon(Icons.looks_3_outlined),label: "Üç" ),
      ],

```
## Kodlanmış Hali

Eğer bir liste yaparsak ve bir secilenIndex değişkeni ile de kontrol edersek sayfa ona göre değişir. Örneğin aşağıdaki şeklilde değişkenler ve liste tanımlanır.
```
int secilenIndeks = 0;
var sayfalar = [const SayfaBir(),const SayfaIki(),const SayfaUc()];
```
Devamında ise body kısmını da düzenleyelim ve listeyi ekleyelim. Liste BottomNavigation'ın onTap'ı ile tetiklenince sayfa da değişir.
```
body: sayfalar[secilenIndeks],
```
 Ayrıca currentIndex:'e de secılenIndex verilirse hangi index seçiliyse onu tıklanmış gösterir. OnTap içinde de callBack'i yani hangi sayfaya tıklandığını index isimli bir değişkende tutarız ve setState içerisinde secilenIndex = index; yaparsak callBack'ten kullanıcının seçtiği index bilgisi alınır ve seçilen indexi değiştirir. Aynı zamanda setState ile seçilen index'e göre tanımlanan listeden gösterilen sayfa değiştirilir ve baştan çizilir.
 ```
    return Scaffold(
      appBar: AppBar(title: const Text("Bottom Navigation"),),
      body: sayfalar[secilenIndeks],
      bottomNavigationBar: BottomNavigationBar(items: const [
        BottomNavigationBarItem(icon: Icon(Icons.looks_one_outlined),label: "Bir" ),
        BottomNavigationBarItem(icon: Icon(Icons.looks_two_outlined),label: "iki" ),
        BottomNavigationBarItem(icon: Icon(Icons.looks_3_outlined),label: "Üç" ),
      ],
        currentIndex: secilenIndeks,
        onTap: (index) {
          setState(() {
            secilenIndeks = index;
          });
        } ,
      ),
    );
```
