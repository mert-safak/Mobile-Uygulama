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
