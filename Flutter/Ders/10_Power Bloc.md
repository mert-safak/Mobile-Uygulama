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
pubspec.yaml içerisinde dependencies altına
```dart
dependencies:
  flutter:
    sdk: flutter
  flutter_bloc:
```
