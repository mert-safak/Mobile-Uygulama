# GERİ TUŞUNU KODLAMA
## AppBar'daki Geri Tuşu
leading sol anlamına gelir flutter'da buradan erişiyoruz AppBar'daki geri tuşunun yerine. Önce leading yazılır sonra içerisine bir IconButton tanımlıyoruz. Aşağıdaki şekilde gekecek onPressed çierisine öncelikle (){} yapıp kodlayana kadar boş bırakıyoruz. 
```
leading: IconButton(onPressed: onPressed, icon: icon),),
```
icon olarak da aşağıdaki gibi bir icon eklenebilir. Bu şekilde tuş çalışmaz çünkü onPressed kısmı boş.
```
icon: const Icon(Icons.arrow_back_ios_new))
```
onPressed köşeli parantezinin içerisine de Navigator.pop(context) eklenirse AppBar'ın tam hali aşağıdaki gibi olur.
```
      appBar: AppBar(
        title: const Text("Oyun Ekranı"),
        leading: IconButton(onPressed: (){
          print("Appbar geri tuşu seçildi");
          Navigator.pop(context);
        }, icon: const Icon(Icons.arrow_back_ios_new)),
      ),
```
## Telefon Geri Tuşu veya Geriye Kaydırma

Öncelikle aşağıdaki gibi class'ın altına bir async fonksiyon tanımlanır. Return false ile geri dönmeyi kapatır. true olursa geri dönebilir.
```
class _OyunEkraniState extends State<OyunEkrani> {

  Future<bool> geriDonusTusu(BuildContext context) async {
    print("Navigation geri tuşu seçildi");
    return true;
  }
```

Daha sonra body'deki center vb. ilk katman imleç ile seçilerek Wrap with Widget denir. Çünkü ihtiyacımız olan widget listede yok. oraya WillPopScope yazılır. Bu widget geriye gitmeyi kontrol eder. Devamında ise aşağıdaki şekilde yapılarak fonskiyon verilir ve son hali görülür.
```
      body: WillPopScope(
        onWillPop: () => geriDonusTusu(context),
        child: Center(
```
 
