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

# Döngüler
for, while ve do-while olmak üzere üç çeşit döngü yapısı vardır.

**Not:** Döngülerde tek satırlık kodlar için scope kullanılmasına gerek yoktur.

**Not:** foreach yapısı bir döngü değil iterasyondur.

## for Döngüsü
for döngüsünde koşul true iken döngü devam eder.
for döngüsünde koşul verilmediği zaman sonsuz döngü oluşur.
```cs
// Example1
Console.Write("Bir sayı giriniz:");
int v_sayi = Convert.ToInt32(Console.ReadLine());
int sonuc = 1;
for (int i = v_sayi; i > 1; i--)
    sonuc *= i;
Console.Write("Faktöriyeli:" + sonuc);

// Example2
for(int i1 = 0, i2 = 0; i1 < 10 && i2 < 5; i1++, i+=5){}

// Example3
for(;;){} // Sonsuz Döngü
for(int i = 20 ;  ; i++) {} // Sonsuz Döngü
```

## while Döngüsü
```cs
// Example1
int counter = 0;
while (counter <= 10)
{
    Console.WriteLine(counter);
    counter++;
}

// Example2
while (true){} // Sonsuz Döngü
```

## do-while Döngüsü
do-while döngüsü, döngünün koşuldan bağımsız en az bir kere çalışması istendiği zaman kullanılır.
```cs
// Example1
int counter1 = 1;
do
{
    Console.WriteLine(counter1);
    counter1++;
} while (counter1 <= 10);

// Example2
do {}while(true) // Sonsuz Döngü
```

## Break Ve Continue Komutları
Break komutu: Break komutu döngüyü sonlandırır. Switch-Case yapısında ise, switch koşulunun 
scope’u({}) dışına çıkmamızı sağlar.

Continue komutu: Döngü içinde bu komutun bulunduğu satırdan sonrası işlenmeden döngünün sonraki değerini işlemek 
üzere başa dönmesini (sonraki tekrara geçmesini) sağlar.

```cs
for (int i = 0; i < 20; i++)
{
    if (i == 5)
        continue;

    if (i == 10)
        break;

    Console.WriteLine(i);
}
```

## Foreach Iterasyon Yapısı
Foreach yapısı döngü değildir. listeler ya da diziler üzerinde işlem yapmak için kullanılır.
Özellikle eleman sayısının bilinmediği durumlarda büyük kolaylık sağlamaktadır.

**Not:** Foreach yapısı sadece dizi elemanlarını okumak için kullanılır. Dizi elemanları üzerinde 
              düzenleme işlemlerine izin verilmez. Bu tür engelleme ReadOnly (Sadece okunabilir) olarak bilir.

```cs
string[] isimler = { "Alperen", "Ahmet", "Elif", "Hakan", "Sema" };
foreach (string eleman in isimler)
    Console.WriteLine(eleman);
Console.ReadKey();
```




