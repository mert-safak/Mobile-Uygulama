Sayfa geçişi yaparken örneğin ElevatedButton içerisine Navigator yazılır sonra.push seçilir. context bırakılır route silinir yerine ctrl+space ile metarialPageRoute yazılır. çıkan yerden builder silinir ve ctrl+space ile aşağıdaki forma getirilir.
```
Navigator.push(context, MaterialPageRoute(builder: (context) => OyunEkrani(),));
```
