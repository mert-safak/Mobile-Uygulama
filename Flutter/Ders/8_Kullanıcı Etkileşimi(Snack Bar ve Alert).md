# KULLANICI ETKİLEŞİMİ SNACK BAR VE ALERT
## Snack Bar
Bir buton içerisine tanımlanabilir. Veya başka bir aksiyona da tanımlanabilir. Kod orjinal olarak sadece bildirim göstermek için şu şekildedir. Kod düzeltme çoğu taslak kısmı otomatik olarak getirir.
```
              ScaffoldMessenger.of(context).showSnackBar(
                  SnackBar(content: const Text("Silmek istiyor musunuz?")));
```
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
