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
Devamında ise Image.asset ekleyerek resimler gösterilir
```
Image.asset("resimler/mutlu.png"),
```
Butonlara tıklayarak değişimini yaptığımız kod ise`aşağıdadır. Burada sadece resimAdi değişkeni _ ile başlayan class isminin altında String resimAdi = "mutlu.png"; bu şekilde başlangıç değeri olarak tanımlanmıştır.
```
            Row(mainAxisAlignment: MainAxisAlignment.spaceEvenly ,
              children: [
                ElevatedButton(onPressed: (){
                  setState(() {
                    resimAdi = "mutlu.png";
                  });
                }, child: const Text("Resim 1"),
                ),
                Image.asset("resimler/$resimAdi"),
                ElevatedButton(onPressed: (){
                  setState(() {
                    resimAdi = "uzgun.png";
                  });
                }, child: const Text("Resim 2"),
                ),
              ],
```

### Online Resim Gösterme
Image.asset değil de Image.network kullanacağız. src yazan yere "" içerisinde url yazarsak resim görünür.
```
Image.network(src)
```
#### SizedBox ile boyutunu ayarlama
Image.network imleç ile seçilip alt+enter yapılıp wrap with SizedBox seçilirse. Width ve Height değerleri girilip resmin boyutu değiştirilebilir.
```
SizedBox(width: 100, height: 100,
              child: Image.network("https://cdn.yemek.com/mnresize/1250/833/uploads/2022/03/ev-usulu-pizza-yemekcom.jpg"),),
```

## Switch
İlk önce _ ile başlayan class'da true,false kontrol için bir değişken oluşturulur.
```
bool switchKontrol = false;
```
Daha sonra bir SwitchListeTile Widget'ı oluşturulur. Bunu SizedBox'a almaz ve width değeri vermezsek ekranı kaplar ve ekran boş görünür. controlAffinity: ListTileControlAffinity.leading şu satırda chechbox'ın solda title'ın ise sağdaq olmasını sağlıyoruz. En sonda setState ile de switch konumunu değiştirip baştan çizdiriyoruz.
```
                SizedBox(width: 200,
                  child: SwitchListTile(
                    title: const Text("Dart"), // başlık
                      controlAffinity: ListTileControlAffinity.leading, //Switch'i title'ın soluna alır
                      value: switchKontrol, //burası Switch'in konumudur.
                      onChanged: (veri){ // Burada (veri) callBack mantığı gibidir konumunu söyler. 
                        setState(() {
                          switchKontrol = veri;
                        });
                      }
                  ),
                ),
```

## ChechBox
Mantık Switch'in aynısıdır. Başta yine bir Bool değişkende tutulur değer.
```
bool switchKontrol = false
```
Fark sadece burada gelen veri nullable'dır. Bu yüzden checkboxKontrol = veri! şeklinde sonunda ! olarak yazılır.
```
                SizedBox(width: 200,
                  child: CheckboxListTile(
                      title: const Text("Flutter"),
                      controlAffinity: ListTileControlAffinity.leading,
                      value: checkboxKontrol,
                      onChanged: (veri){
                        setState(() {
                          checkboxKontrol = veri!;
                        });
                      }
                  ),
```
## RadioList
CheckBox gibi ancak sadece tek biri seçilebilir. Öncelikle yine bir değişken tanımlanır ancak bu sfer integer olarak.
```
int radioDeger = 0;
```
Devamında ise kod aşağıdaki gibidir
```
Row(mainAxisAlignment: MainAxisAlignment.spaceEvenly,
              children: [
                SizedBox(width: 200,
                  child: RadioListTile(
                    title: const Text("Barcelona"),
                      value: 1,
                      groupValue: radioDeger,
                      onChanged: (veri){
                        setState(() {
                          radioDeger = veri!;
                        });
                      }
                  ),
                ),
                SizedBox(width: 200,
                  child: RadioListTile(
                      title: const Text("Real Madrid"),
                      value: 2,
                      groupValue: radioDeger,
                      onChanged: (veri){
                        setState(() {
                          radioDeger = veri!;
                        });
                      }
                  ),
                ),
              ],
            ),
```
## ProggressBar
Ekrana yükleniyor şeklinde bir widget eklemek için kullanılır. Yine önce bir değişken tanımlanır.
```
bool progressKontrol = false;
```
Burada 2 buton ile bu progress bar çıkartılmıştır veya durdurulmuştur. Burada önce CircularProgressIndicator() isimli bir widget eklenir. Daha sonra alt+enter wrap with widget ile üzerine bir Visibility widget eklenir. Buradan da görünür olma olmama durumunu kontrol eden değişkenimiz atanır.
```
Row(mainAxisAlignment: MainAxisAlignment.spaceEvenly,
              children: [
                ElevatedButton(onPressed: (){
                  setState(() {
                    progressKontrol = true;
                  });
                }, child: const Text("Başla")
                ),
                Visibility(visible: progressKontrol, child: const CircularProgressIndicator()),
                ElevatedButton(onPressed: (){
                  setState(() {
                    progressKontrol = false;
                  });
                }, child: const Text("Dur")
                ),
              ],
            )
```
## Slider
Öncelikle yine _ ile başlayan class'a bir değişken tanımlanır.
```
double ilerleme = 30.0;
```
Devamında ise Slider widget'ı eklenir üzerine de takip edebilmek için bir text eklenebilir. Text'te double'da çok fazla ondalık olduğu için önce int'e çevirip sonra string yaptık.
```
            Text(ilerleme.toInt().toString()),
            Slider(max:100, min:0.0, value: ilerleme, onChanged: (veri){
              setState(() {
                ilerleme = veri;
              });
            }),
```

## Date Time Picker
TextField kullanacağımız için _ ile başlayan class'ta  yine saat ve tarih için ayrı TextEditingController tanımlanır
```
  var tfSaat = TextEditingController();
  var tfTarih = TextEditingController();
```
Devamında ise .then'den önceki kısımda Icon'a tıklayınca date veya time picker'ı açar ama seçince işlem yapmaz. O kısımda seçileni alp controller'ın text'ine eşitliyoruz.
```
            Row(mainAxisAlignment: MainAxisAlignment.spaceEvenly,
              children: [
                SizedBox(width: 120,
                  child: TextField(controller: tfSaat, decoration: const InputDecoration(hintText: "Saat"),),),
                IconButton(onPressed: (){
                  showTimePicker(context: context, initialTime: TimeOfDay.fromDateTime(DateTime.now()))
                  .then((value) => {
                    tfSaat.text = "${value!.hour} : ${value.minute}"
                  });
                  
                }, icon: const Icon(Icons.access_time)),
                SizedBox(width: 120,
                  child: TextField(controller: tfTarih, decoration: const InputDecoration(hintText: "Tarih"),),),
                IconButton(onPressed: (){
                  showDatePicker(
                      context: context,
                      initialDate: DateTime.now(),
                      firstDate: DateTime(2000),
                      lastDate: DateTime(2030))
                      .then((value) =>
                  {
                    tfTarih.text = "${value!.day} / ${value.month} / ${value.year}"
                  });
                }, icon: const Icon(Icons.date_range)),
              ],
            ),
```
## DropDown Menu
Öncelikle string elemanlar barındıran bir ulkeler listesi ve secilenUlke değişkeni tanımlıyoruz. Seçilen ulkeyi ekranda göstermeye yarar varsayılan olarak da Türkiye seçilidir. Devamında ise listeye elemanları eklerken initState() ile ekleriz çünkü setState vb. metodlar çağrıldığında yeniden listeye bu elemanlar eklenmesin sadece ilk açıldığında çalışsın diye bu şekilde yapılır. Listeye eleman eklemeler genelde bu şekilde olurlar.
```
  var ulkelerListesi = <String>[];
  String secilenUlke = "Turkiye";

  @override
  void initState() {
    super.initState();
    ulkelerListesi.add("Turkiye");
    ulkelerListesi.add("İtalya");
    ulkelerListesi.add("Japonya");
  }
```
Devamında ise Widget tanımlanır. Normal çağırınca value ve icon özelliği taslar olarak gelmez ancak el ile klenebilir. Value varsayılan seçili değeri gösterir. Yukarda bunun için Türkiye tanımlamıştık. items için önce ulkelerListesi.map yapılır. Dart dilinde bir listenin tüm elemanları bu şekilde .map ile gösterilir. Sonra  DropdownMenuItem isimli bir class çağırılır ve içindeki ulke isimli tanımlaıdğımız değişken buraya yazılır. OnChanged ile de yine callBack'de kullanıcı tarafından seçilen setState altında secilenUlke değişkenine atanır.
```
DropdownButton(
                value: secilenUlke,
                icon: const Icon(Icons.arrow_drop_down),
                items: ulkelerListesi.map((ulke) {
                  return DropdownMenuItem(value: ulke, child: Text(ulke),);
                }).toList(),
                onChanged: (veri){
                  setState(() {
                    secilenUlke = veri!;
                  });
                }),
```

## GestureDetector
Tıklanabilen görseller oluşturmaya yarar. Öncelikle bir Container widget'ı oluşturulur. Boyu ve genişliği yazılır. Rengi de belirtilir. Devamında ise imleç ile seçilip alt+enter ile widget as wrapped seçilir. Sonra GestureDetector olarak değiştirilir Wdiget. bunun onTap onDoubleTap onLongPress gibi metodları vardır.
```
GestureDetector(
                onTap: (){
                  print("Container tek tıklandı");
                },
                onDoubleTap: (){
                  print("Container çift tıklandı");
                },
                onLongPress: (){
                  print("Container uzun basıldı");
                },
                child: Container(width: 200, height: 100, color: Colors.red,))
```










