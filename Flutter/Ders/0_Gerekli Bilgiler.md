# GEREKLİ BİLGİLER
## setState Mantığı
setState yapılan bir değişiklikte sayfanın yenilenmesini sağlar. Örneğin herhangi bir değer değişti sayfa yeniden çizilir fluuter bu mantıkta hareket eder. Button tıklamalarında değerler değişecekse tıklamanın altına yazılması gereklidir. Örneğin aşağıda bir ElevatedButton'un onPressed'ı içerisine yazılmıştır ve sayfayı yeniden çizerek bir sayacı arttırmaya sebep olur.
```
            ElevatedButton(onPressed: (){
              setState(() {
                sayac = sayac + 1;
              });
            }, child: const Text("Tıkla")),
```
