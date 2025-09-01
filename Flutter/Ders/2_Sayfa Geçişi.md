# SAYFALAR ARASI GEÇİŞ
## Sayfa Geçişi
Sayfa geçişi yaparken örneğin ElevatedButton içerisine Navigator yazılır sonra.push seçilir. context bırakılır route silinir yerine ctrl+space ile metarialPageRoute yazılır. çıkan yerden builder silinir ve ctrl+space ile aşağıdaki forma getirilir.
```
Navigator.push(context, MaterialPageRoute(builder: (context) => OyunEkrani()));
```
## Geriye Dönme
ElevatedButton vb. altına bu şekilde yazılırsa geldiğin sayfaya dönmeyi sağlar. Geri butonunun yaptığı şeyin aynısını yapar.
```
Navigator.pop(context);
```

## Anasayfaya Dönme
```
Navigator.of(context).popUntil((route) => route.isFirst,);
```

## Arkada kalan sayfanın yerine oluşturma
Eğer push değil de pushReplacement kullanılırsa bir önceki sayfayı backstage'den  siler  geriye dönerken atlayarak döner.
```
Navigator.pushReplacement(context, MaterialPageRoute(builder: (context) => const SonucEkrani()));
```
