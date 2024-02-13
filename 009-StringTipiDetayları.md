
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

### String Birleştirme
String birleştirme 3 şekilde yapılabilir:
1. "+" oeratörü ile string birleştirme
2. string.Format metodu ile string birleştirme
3. String interpolasyon operatürü ($) ile string birleştirme

```cs
var name = "Alperen";
var old = 27;
// 1.Yöntem
Console.WriteLine("Merhaba " + name + ", yaşın: " + old);
// 2.Yöntem
Console.WriteLine(string.Format("Merhaba {0}, yaşın: {1}", name, old);
// 3.Yöntem
Console.WriteLine($"Merhaba {name}, yaşın: {old}");
```

**Not:** String interpolation operatürü ($) ile string birleştirme yaparken metnin içerisinde {} kullanmak istersen,
{{ }} şu şekilde kullanabilirsin.

### Escape(Kaçış) Karakterleri
Eylem olarak algılanan karakterler,”\”(backward slash) simgesinden sonra kullanılırsa, ilgili karakterin eylem olarak değilde, normal olarak yorumlanmasını sağlar.
Aşağıdaki tabloda kaçış karakterlerinin bazıları listelenmiştir.

Kaçış Karakteri	Karakterin Açıklaması:
* \0	Null sonlandırma karakteridir.Genel olarak dosya veya veri kanalının bitişini belirtmek için kullanılır.
* \a	Bip sesini çıkartan karakterdir
* \b	BackSpace – Geri – Önceki karakteri silme
* \t	Tab
* \r	Satır başı (Carriage Return)
* \n	Bir alt satıra iner
* \v	Dikey Tab
* \f	Sayfa ilerleme
* \”	Çift tırnak
* \’	Tek tırnak
* \\	Backslash

### Verbatim Operatörü (@)
1. Bir değişken yada metod vs gibi yapılanma isimlerinde keywordlerin kullanımına izin verir.
```cs
int @int = 100;
```

2. Escape karkaterlerinin kullanılması icap eden durumlarda @ operatörü kullanarak eylemsel karakterleri kendileriyle ezebilecek özellik kazandırabiliriz.
```cs
string metin1 = "hava \"güzel\"";
string metin1 = @"hava \ ""güzel""";
```

3. c# ta string ifadeleri birleştirme operatörü kullanmadan alt alta yazamassınız. Yazabilmek için @ operatörü kullanabilirsiniz.
```cs
string metin = @"birinci satır
                 ikinci satır
                 üçüncü satır";
```

**Not:** String interpolasyonu ile verbatim operatörü birlikte kullanılabilir.
```cs
string metin = @$"birinci satır {param1}
                 ikinci satır {param2}
                 üçüncü satır {param3}";
```

### Önemli String Fonksiyonları
1. Contains
2. StartWith
3. EndWith
4. Equals
5. Compare
6. CompareTo
7. IndexOf
8. Insert
9. Remove
10. Replace
11. Split
12. Substring
13. ToLower
14. ToUpper
15. Trim / TrimEnd / TrimStart

## StringSegment Sınıfı Nedir?
StringSegment, ArraySegment'in string değerler için muadilidir. Metinsel değerlerdeki birçok analitik operasyonlardan bizleri kurtarmakta ve
Substring vs gibi fonksiyonlar yerine string değerde hedef kesit üzerinde işlem yapmamızı sağlayan bir türdür. Özetle String ifadeler üzerinde 
bellek üzerindeki alanı referans alarak işlemler yapmamızı sağlar. StringSegment, Microsoft.Extensions.Primitives paketinin altında tanımlanmıştır.

```cs
StringSegment segment = new StringSegment(text);
StringSegment segment = new StringSegment(text, 2, 5);
```

## StringBuilder Sınıfı Nedir?
+ operatörü ile stringler birleştirilirken arka tarafta fazladan diziler oluşturulur. StringBuilder, string birleştirme operasyonlarında
+ operatörüne nazaran yüksek maliyeti abzorbe edebilmek için arkaplanda StringSegment algoritmasını kullanan ve bu algoritma ile bizlere
ilgili değerleri olabilecek en az maliyetle birleştirip döndüren bir sınıftır.

```cs
StringBuilder builder = new StringBuilder();
builder.Append("Alperen");
builder.Append(" ");
builder.Append("Bektaşoğlu");
Console.WriteLine( builder.ToString() ); // Çıktı: Alperen Bektaşoğlu
```































