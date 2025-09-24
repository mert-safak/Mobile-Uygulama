# ListView
## Future ile listesinin oluşturulması
Öncelikle _ ile başlayasn class ismi kısmına Future ile bir liste oluşturulur. Bu listedeki elemanları kullanarak gösterim yapacağız. Future ile oluşturulan fonksiyonumuzun Listelerden oluşacğını bu listeleride Kisiler sınıfından nesneler tutacağını belirtiyoruz. Daha sonra kisilerListesi adında Kisiler sınıfından oluşan boş listemizi tanımlıyoruz. Daha sonra listenin elemenlarını oluşturup bunları listeye ekliyoruz. return olarak da fonksiyona listeyi veriyoruz.
```dart
Future<List<Kisiler>>kisileriYukle() async {
    var kisilerListesi = <Kisiler>[];
    var k1 = Kisiler(kisi_id: 1, kisi_ad: "mert", kisi_tel: "1111");
    var k2 = Kisiler(kisi_id: 2, kisi_ad: "safak", kisi_tel: "2222");
    var k3 = Kisiler(kisi_id: 3, kisi_ad: "saglam", kisi_tel: "3333");
    kisilerListesi.add(k1);
    kisilerListesi.add(k2);
    kisilerListesi.add(k3);
    return kisilerListesi;
  }
```dart
## FutureBuilder oluşturulması
Daha sonra body içerisine FutureBuilder isimli bir widget ekliyoruz ve bunun içerisinde listeler olacağını ve o listelerde Kisiler sınıfından nesneler olacağını belirtiyoruz.içerisinde future ve builder parametreleri geliyor. Future tanımladığımız fonksiyonumuz olacak. Builder ise ctrl+space ile otomatik tamamlayıp context,snapshot'ı getirir. Burada snapshot'ı kullanarak veri var mı diye snapshot.hasdata şeklinde if bloğuna yazıyoruz. Eğer yok ise direkt boş bir Center() şeklinde ekran görünüyor ancak data var ise var kisilerListesi diye bir kisiler listesi daha oluşturuyoruz bu normalde yukardakinden bağımsızdır ama biz var kisilerListesi = snapshot.data; kullanarak ikisini birbirine eşitliyoruz. snapshot.data burada daha önceden fonskiyon aracılığıyla dönen veriye erişimimizi sağlıyor zaten o veri de kisilerListesi'di, 

Daha sonra return ile bir listView oluşturup .builder ile ayarlarını yapıyoruz. itemCount ve itemBuilder çıkıyor, buradan itemCount'a kisilerListesi!.lenght ekliyoruz. Burada bu şekilde nullable! olarak istiyor. Zaten data yoksa boş ekran dönecekti. Bu şekilde ListView'de kaç veri olduğunu listenin eleman sayısına eşitliyoruz. itemBuilder'ı ise ctrl+space ile dolduruyoruz ve context ve index geliyor. Buradaki indexi listemizin elemanlarını çağırmak için kullanıyoruz var kisi = kisilerListesi[index]; burada kisi nesnesi oluşturup listenin index elemanına eşitliyoruz. Daha sonra bir return daha yazıp Card() tasarımında istediğimiz için Card ekliyoruz. sonra Row ve column ile Textlerimizi yazdırıyor ve bir de yanlarına bir Cancel butonu ekliyoruz.
```dart
body: FutureBuilder<List<Kisiler>>(
          future: kisileriYukle(),
          builder: (context, snapshot) {
            if(snapshot.hasData){
              var kisilerListesi = snapshot.data;
              return ListView.builder(
                  itemCount: kisilerListesi!.length, //3
                  itemBuilder: (context, index) { //0,1.2
                    var kisi = kisilerListesi[index];
                    return Card(
                      child: Row(
                        children: [
                          Column(
                            children: [
                              Text(kisi.kisi_ad),
                              Text(kisi.kisi_tel),
                            ],
                          ),
                          IconButton(onPressed: () {
                            setState(() {
                              aramaYapiliyorMu = true;
                            });
                          }, icon: Icon(Icons.clear,color: Colors.black54,))
                        ],
                      ) ,
                    );
                  },);
            }else{
              return const Center();
            }
          },),
```
