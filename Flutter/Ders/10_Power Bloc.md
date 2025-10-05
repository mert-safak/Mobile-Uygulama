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
```
## Cubitleri Oluşturma
her sayfa için sayfaİsmi_cubit.dart şeklinde cubitler oluşturulur. Örneğin anasayfa_cubit şeklinde olur. İçerisine aşağıdaki şekilde bir class oluşturulur ve Cubit sınıfından miras alır.
```dart
class AnasayfaCubit extends Cubit<List<Kisiler>>{
AnasayfaCubit():super(<Kisiler[]>);
}
```

## main.dart altında tanımlama
bizim ana dosyamız main.dart olduğu için onun içerisinde cubitleri tanımlamak gereklidir. Aşağıdaki halındaki MetarialApp silinir yerine MultiBlocProvider yazılır.
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
