
## String Tipinin Detayları

String referans tiplidir. Aslında özüne baktığında string bir char dizisidir.
```cs
string metin = "Alperen";
Console.WriteLine( metin[1] ); // Çıktı: l
```
**Not:** String ifadelerde her bir karakter baştan sona otomatik indexlenmektedir. Dolayısıyla indexer operatörü
kullanılabilr. Bununla birlikte yapısal olarak string olduğundan dolayı Array referansına atılamaz. Array ile karşılanamaz.

**Not:** String null ve empty değerlerini de değer olarak alabilmektedir.
1. Bir değişken eğer ki null ise bu durum ilgili değişkenin bellekte herhangi bir alanı tahsis etmediği anlamına gelir.
2. Bir değişken eğer ki empty ise bu durum ilgili değişkenin bellekte bir alanı tahsis ettiği ve değerinin boş olduğu anlamına gelir.

**Not:** Default değerlerin olduğu durumlar empty olarak geçer.
```cs
int var1 = 0;
bool var2 = false;
string var3 = ""; 
string var4 = string.Empty; // var3 ve var4 aynı değerdir.
```

**Not:** Null olan bir değer üzerinde işlem yapmaya çalıştığınızda run time hatası meydana gelir.

### IsNullOrEmpty ve IsNullOrWhiteSpace Metodlarının Kullanımı
```cs
string var1 = "alperen";
string var2 = "";
string var3 = null;
string var4 = "    ";

// IsNullOrEmpty Metodu
Console.WriteLine( string.IsNullOrEmpty(var1) ); // Çıktı: false
Console.WriteLine( string.IsNullOrEmpty(var2) ); // Çıktı: true
Console.WriteLine( string.IsNullOrEmpty(var3) ); // Çıktı: true
Console.WriteLine( string.IsNullOrEmpty(var4) ); // Çıktı: false

// IsNullOrWhiteSpace metodu
Console.WriteLine( string.IsNullOrWhiteSpace(var1) ); // Çıktı: false
Console.WriteLine( string.IsNullOrWhiteSpace(var2) ); // Çıktı: true
Console.WriteLine( string.IsNullOrWhiteSpace(var3) ); // Çıktı: true
Console.WriteLine( string.IsNullOrWhiteSpace(var4) ); // Çıktı: true
```



