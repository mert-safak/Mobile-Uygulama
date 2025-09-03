# KULLANICI ETKİLEŞİMİ SNACK BAR VE ALERT
## Snack Bar
Bir buton içerisine tanımlanabilir. Veya başka bir aksiyona da tanımlanabilir. Kod orjinal olarak sadece bildirim göstermek için şu şekildedir. Kod düzeltme çoğu taslak kısmı otomatik olarak getirir.
```
              ScaffoldMessenger.of(context).showSnackBar(
                  SnackBar(content: const Text("Silmek istiyor musunuz?")));

```
### Button içerisinde SnackBar
Aşağıda ElevatedButton içerisinde yazılmış hali mevcuttur.
```
            ElevatedButton(onPressed: (){
              ScaffoldMessenger.of(context).showSnackBar(
                  SnackBar(content: const Text("Silmek istiyor musunuz?")));
            },
              child: const Text("Snackbar"),
            ),
```
Ayrıica bir de içerisine action tanımlanarak bir eylem gerçekleştirilebilir veya yeni bir SnackBar ile bilgi verilebilir. Aşağıda yeni bir SnackBar ile bilgi verilmiştir.
```
            ElevatedButton(onPressed: (){
              ScaffoldMessenger.of(context).showSnackBar(
                  SnackBar(
                    content: const Text("Silmek istiyor musunuz?"),
                    action: SnackBarAction(label: "Evet", onPressed: (){
                      ScaffoldMessenger.of(context).showSnackBar(SnackBar(content: const Text("Siindi"),));
                    }),
                  ));
            },
              child: const Text("Snackbar"),
            ),
```
### Çeşitli SnackBar Özelleştirmeleri
Ayrıca istenirse aşağıdaki şekilde de özelleştirmeler yapılabilir.
```
            ElevatedButton(onPressed: (){
              ScaffoldMessenger.of(context).showSnackBar(
                  SnackBar(
                    content: const Text("Silmek istiyor musunuz?",style: TextStyle(color: Colors.indigoAccent),),
                    backgroundColor: Colors.white ,
                    action: SnackBarAction(label: "Evet", textColor: Colors.red, onPressed: (){
                      ScaffoldMessenger.of(context).showSnackBar(
                          SnackBar(
                            content: const Text("Siindi",style: TextStyle(color: Colors.red)),
                            backgroundColor: Colors.white,
                            ));

                    }),
                  ));
            },
              child: const Text("Snackbar (özel)"),
            ),
```
## Alert Dialog
### Alert Dialog Kod
Alert Dialog aşağıdaki kod ile yapılır.
```
             showDialog(
                  context: context,
                  builder: (BuildContext context){
                    return AlertDialog(
                      title: const Text("Başlık"),
                      content : Text("İçerik")
                    );
```
### Button İçinde Alert Dialog
```
            ElevatedButton(onPressed: (){
              showDialog(
                  context: context,
                  builder: (BuildContext context){
                    return AlertDialog(
                      title: const Text("Başlık"),
                      content : Text("İçerik")
                    );
                  }
              );
            },
              child: const Text("Alert"),
            ),
            ElevatedButton(onPressed: (){},
              child: const Text("Alert Özel"),
            ),
```
### Alert Dialog İçerisine Buton Ekleme
Aşağıda görüldüğü üzere AlertDialog'un actions özelliğine TextButton eklenebilir. Bu button tek başına tıklamayla işlem yapar ama tıklandıktan sonra kapanmaz. kapatılmak istenirse Navigator.pop(context) ile cihazın geri tuşunu çalıştırma kullanılır.
```
              showDialog(
                  context: context,
                  builder: (BuildContext context){
                    return AlertDialog(
                      title: const Text("Başlık"),
                      content : Text("İçerik"),
                      actions: [
                        TextButton(onPressed: (){
                          print("İptal Seçildi");
                          Navigator.pop(context);
                        }, child: const Text("İptal"),),
                        TextButton(onPressed: (){
                          print("Tamam Seçildi");
                          Navigator.pop(context);
                        }, child: const Text("Tamam"),)
                      ],
                    );
```

## Alert Dialog Özelleştirme
Kodun devamında özelleştirme TextField() ile yapılacak bu yüzden öncelikle _ ile başlayan sayfa class'ına aşağıdaki kod yazılır ve bir TexEditController tanımlanır.
```
var tfControl = TextEditingController();
```

Kodun devamı ise aşağıdaki şekildedir.
```
            ElevatedButton(onPressed: (){
              showDialog(
                  context: context,
                  builder: (BuildContext context){
                    return AlertDialog(
                      title: const Text("Kayıt İşlemi"),
                      content : TextField(controller: tfControl, decoration: InputDecoration(hintText: "Veri"),),
                      backgroundColor: Colors.grey,
                      actions: [
                        TextButton(onPressed: (){
                          print("İptal Seçildi");
                          Navigator.pop(context);
                        }, child: const Text("İptal",style: TextStyle(color: Colors.black),),),
                        TextButton(onPressed: (){
                          print("Alınan Veri ${tfControl.text}");
                          Navigator.pop(context);
                        }, child: const Text("Kaydet",style: TextStyle(color: Colors.black),),)
                      ],
                    );
                  }
              );
            },
              child: const Text("Alert Özel"),
            ),
```















