# CSharp_Educations
ENG: Repository for C# education documentations. This documentation is in Turkish.

TR: C# eğitim dökümanları reposudur. Bu dökümanlar Türkçedir.

-----------------------------------------

#region Nullable Veya ? Kullanımı
/* 
    Değer tipli değişkenler null değeri alamazken referans tipli değişkenler null değeri alabilir. 
    Bu ifadeler, değer tipli değişkenlerin null değer alabilmesi için kullanılır.
    Aşağıda örnekler mevcuttur.
 */

Nullable<int> i = null; // Değişkenin null değeri alabilmesi için gereklidir. 
//int? j = null; // Nullable ifadesi yerine kısa kullanımıdır.

if (i.HasValue) // i değişkeni içindeki veriyi kontrol eder. 
    Console.WriteLine(i.Value);
else
    Console.WriteLine("Null");
#endregion
