# Akış Kontrol Mekanizmaları
Akış kontrol mekanizmaları 2 tanedir.
1. if - if else - else if Yapısı
2. Switch-Case Yapısı

## if - if else - else if Yapısı
Koşul doğruysa if bloğu çalıştırılır. Değil ise else bloğu çalıştırılır.
```cs
int sayi;
Console.Write("Lütfen bir sayı girin:");
sayi = Convert.ToInt32(Console.ReadLine());
if (sayi > 0)
    Console.WriteLine("{0} sayısı pozitif bir sayıdır.", sayi);
else if (sayi < 0)
    Console.WriteLine("{0} sayısı negatif bir sayıdır.", sayi);
else
    Console.WriteLine("Girilen sayı 0'a eşittir.");
```

**Not:** Tek satırlık if yapılarında scope kullanmaya gerek yoktur. Birden fazla satır
için scpoe kullanılması gerekir.

## Switch-Case Yapısı
Switch-Case yapılanmasında bir değişkenin değeri için sadece eşitlik durumlarını kontrol etmek için kullanılır.
Switch-Case yapılanmasında default yapısı zorunlu değildir.
```cs
string job = "CE";
switch (job)
{
    case "Police": 
        // ...
        break;
    case "Lawyer":   
        // ...
        break;
     default:
        // ...
        break;
}
```

**Not:** When anahtar kelimesi ile Switch-Case yapısı zenginleştirilebilir.
```cs
int salary = 50_000;
switch (job)
{
    case int x when x > 10_000 || x < 20_000: 
        // ...
        break;
}
```

**Video:** <a href="https://www.youtube.com/watch?v=bbaKxvFELB4&list=PLQVXoXFVVtp3e_urGZcMNAHx2Eo4Rm5Xk&index=134"> Switch Expressions </a>




