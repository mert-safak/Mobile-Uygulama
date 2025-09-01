# YAŞAM DÖNGÜSÜ YAPILARI
## setState Mantığı
setState yapılan bir değişiklikte sayfanın yenilenmesini sağlar. Örneğin herhangi bir değer değişti sayfa yeniden çizilir flutter bu mantıkta hareket eder. Her setState çalıştığında build metodu çalışır yani. Button tıklamalarında değerler değişecekse tıklamanın altına yazılması gereklidir. Örneğin aşağıda bir ElevatedButton'un onPressed'ı içerisine yazılmıştır ve sayfayı yeniden çizerek bir sayacı arttırmaya sebep olur. Sayfa oluştururken Stateful ve Stateness bunu işaret eder Statefullda bu sayfayı yenileme işlemi yapılabilir. Bu sayede sayfa dinamik değişkenler alabilir.
```
            ElevatedButton(onPressed: (){
              setState(() {
                sayac = sayac + 1;
              });
            }, child: const Text("Tıkla")),
```
## initState
Sayfa ilk açıldığında çalışır. initState yazılıp seçilerek hazır taslağı getirir.
```
  @override
  void initState() {
    // TODO: implement initState
    super.initState();
    print("initState() çalışıyor");
  }
```
## .then
Sayfadan geçiş yapıldıpında çalışan yaşam döngüsü. Navigatorden sonra yazılır. Sonuna .than konur tamamlanır. Sonra içerisindeki value'ye de parantezli olan seşilir. Devamında içerisine kod yazılırsa o kod çalışır.
```
            ElevatedButton(onPressed: (){
              var kisi = Kisiler(ad: "Mert", yas: 31, boy: 177, bekar: false);
              Navigator.push(context, MaterialPageRoute(builder: (context) => OyunEkrani(kisi: kisi),))
                  .then((value) {
                  print("Anasayfaya dönüldü çalışıyor");
                  },);
            }, child: const Text("Başla"))
```
