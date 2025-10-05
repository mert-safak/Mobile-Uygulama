# PowerBloc
## Gereki Klasörleri Oluşturma
Aşağıdaki şekilde klasörler oluşturulup dosyaları oluşturur. dao_repository yardımcı kütüphane olarak kullanılır. Birden fazla repository olabilir. Her sayfa için bir cubit oluşturulur.
```
lib--> data --> entity ->yapilacaklardao_repository.dart   
lib--> ui --> cubit ->anasayfa_cubit.dart  
                    ->detay_sayfa_cubit.dart  
                    ->kayit_sayfa_cubit.dart  
```

## Kütüphanenin kurulumu
pubspec.yaml içerisinde dependencies altına flutter_bloc yazılır girintiler çok önemlidir. Bu şekilde güncel son versiyon yüklenir.
```dart
dependencies:
  flutter:
    sdk: flutter
  flutter_bloc:

## Dao Repository
Uygulamada cubitlere gönderilecek fonksiyonlar burada yazılır. Class olarak tanımlanır.
```dart
class KisilerDaoRepository {
}
```

içerisinde çeşitli fonksiyonlar bulunur. Veritabanı vb. işlemleri de burada yapılır. Örneğin;
```dart
  Future<List<Yapilacaklar>>yapilacaklariYukle() async {
    var yapilacaklarListesi = <Yapilacaklar>[];
    var y1 = Yapilacaklar(id: 1, name: "Uyan");
    var y2 = Yapilacaklar(id: 2, name: "Yüzünü yıka");
    var y3 = Yapilacaklar(id: 3, name: "Kahvaltı yap");
    yapilacaklarListesi.add(y1);
    yapilacaklarListesi.add(y2);
    yapilacaklarListesi.add(y3);
    return yapilacaklarListesi;
  }
```
```
## Cubitleri Oluşturma
her sayfa için sayfaİsmi_cubit.dart şeklinde cubitler oluşturulur. Örneğin anasayfa_cubit şeklinde olur. İçerisine aşağıdaki şekilde bir class oluşturulur ve Cubit sınıfından miras alır bu sınıf içerisinde emit ediliecek değişkenleri alır. Altına ise bir constructor tanımlanır. Super anahtarının içerisindeki varsayılan olarak ilk state edilen değerdir. int değerlerde 0 yazılabilir. Herhangi birşey emit edilmeyecekse de 0 yazılabilir. İçerisinde repository'deki fonksiyonları kullanarak emit eden fonksiyonlar bulununur.
```dart
class AnasayfaCubit extends Cubit<List<Kisiler>>{
AnasayfaCubit():super(<Kisiler>[]);
}
```
Eğer hiçbirşey emit edilmeyecekse Cubit içerisine void yazılır.
```dart
class DetaySayfaCubit extends Cubit<void>{
  DetaySayfaCubit():super(0);
}
```
Aşağıda içerisinde DaoReposioory'ye bağlı ordan aldığı fonksiyonu emit eden bir fonksiyon vardır.
```dart
class AnasayfaCubit extends Cubit<List<Yapilacaklar>>{
  AnasayfaCubit():super(<Yapilacaklar>[]);

  var krepo = YapilaclarDaoRepository();

  Future<void>yapilacaklariYukle() async {
    var liste = await krepo.yapilacaklariYukle();
    emit(liste);
  }
}
```

## main.dart altında tanımlama
bizim ana dosyamız main.dart olduğu için onun içerisinde cubitleri tanımlamak gereklidir. Aşağıdaki halındaki MetarialApp üzerine wrap with widget ile widget eklenir ve MultiBlocProvider yazılır.
```dart
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'Flutter Demo',
      theme: ThemeData(

        colorScheme: ColorScheme.fromSeed(seedColor: Colors.deepPurple),
      ),
      home: const Anasayfa(),
    );
```
Devamında ise parantez içerisine providers: [] ile köşeli parantez içine Cubitler yazılır. Örneğin;
```dart
  @override
  Widget build(BuildContext context) {
    return MultiBlocProvider(
      providers: [
        BlocProvider(create: (context) => KayitSayfaCubit(),),
        BlocProvider(create: (context) => DetaySayfaCubit(),),
        BlocProvider(create: (context) => AnasayfaCubit(),),
      ],
      child: MaterialApp(
        title: 'Flutter Demo',
        debugShowCheckedModeBanner: false,
        theme: ThemeData(
      
          colorScheme: ColorScheme.fromSeed(seedColor: Colors.deepPurple),
        ),
        home: const Anasayfa(),
      ),
    );
  }
```
## Asıl view sayfasının düzenlenmesi
Bu sayfada FutureBuilder yerine BlocBuilder bulunur. Futurebuilder'ın içerisindeki listeden önce cubit sınıfı yazılır. Bu haliyle snaphsot'a ihtiyaç kalmamıştır. direk emit edilen değişken,liste builder içerisine yazılır. snapshot.hasdata snapshot olmadığından kullanılamaz yerine .isNotEmpty kullanılır.
```dart
body: BlocBuilder<AnasayfaCubit,List<Yapilacaklar>>(
          builder: (context, yapilacaklarListesi) {
            if(yapilacaklarListesi.isNotEmpty){
              return ListView.builder(
```

### Başlangıç state'i oluşturma
initState altında başlangıç için emit edilmesi gereken değerler olabilir. Örneğin aşağıda AnasayfaCubit içerisindeki yapılacaklarıYukle fonksiyonu başlangıçta bir kez emit edilir. Bu konulmazsa uygulamada ilk etapta boş ekran açılır. Çünkü state edecek hiçbir veri yoktur.
```dart
void initState() {
    super.initState();
    context.read<AnasayfaCubit>().yapilacaklariYukle();
  }
```










