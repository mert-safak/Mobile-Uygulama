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
