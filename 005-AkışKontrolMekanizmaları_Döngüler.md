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




