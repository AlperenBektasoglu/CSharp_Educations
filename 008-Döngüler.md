## For Döngüsü
```cs
Console.Write("Bir sayı giriniz:");
int v_sayi = Convert.ToInt32(Console.ReadLine());
int sonuc = 1;
for (int i = v_sayi; i > 1; i--)
{
    sonuc *= i;
    Console.Write("Sonuç Hesaplanıyor...");
}
Console.Write("Faktöriyeli:" + sonuc);
Console.ReadKey();
```

Aşağıdaki şekilde sonsuz döngü yapılabilir:
```cs
for (;;)
    Console.WriteLine("Sonsuz Döngü");
```

## While Döngüsü
```cs
int counter = 0;
while (counter <= 10)
{
    Console.WriteLine(counter);
    counter++;
}
```

Aşağıdaki şekilde sonsuz döngü yapılabilir:
```cs
while (true)
  Console.WriteLine("Sonsuz Döngü");
```

## Do-While Döngüsü
Do-while döngüsü, döngünün koşuldan bağımsız en az bir kere çalışması istendiği zaman kullanılır.
```cs
int counter1 = 1;
do
{
    Console.WriteLine(counter1);
    counter1++;
} while (counter1 <= 10);
```
            
Aşağıdaki şekilde sonsuz döngü yapılabilir:
```cs
do
{
    Console.WriteLine("Sonsuz Döngü");
} while (true);
```

## Break Ve Continue Komutları     
Break komutu: Break komutu döngüyü sonlandırır. Switch-Case yapısında ise, switch koşulunun 
scope’u({}) dışına çıkmamızı sağlar.

Continue komutu: Döngü içinde bu komutun bulunduğu satırdan sonrası işlenmeden döngünün sonraki değerini işlemek 
üzere başa dönmesini (sonraki tekrarı yapmasını) sağlar.
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

**Not:** Break komutu foreach mekanizmasını sonlandırmak için de kullanabilir.

**Not:** Break komutu sadece döngülerde, switclerde ve foreachlerde kullanılırken, continue komutu sadece döngülerde kullanılır.

**Not:** Return anahtar kelimesi metod içerisinde kullanılır. ve metodu sonlandırmaya yarar. Geriye değer döndürme özelliğide vardır. Returnler döngüyü değil metodu sonlandırır.

## Goto Komutu
C# goto deyimi koşulsuz olarak belirtilen etikete atlar. Etiket tanımlaması
goto kullanımından önce veya sonra yapılabilir. Performassızdır ve tavsiye edilmez.

```cs
int sayı;
baslangıc: // Etiket
Console.Write("Notunuzu Giriniz: ");
sayı = Convert.ToInt32(Console.ReadLine());

if (sayı >= 0 && sayı < 50)
    Console.WriteLine("Kötü");

if (sayı >= 50 && sayı < 60)
    Console.WriteLine("Geçer");

if (sayı >= 60 && sayı < 70)
    Console.WriteLine("Orta");

if (sayı >= 70 && sayı < 85)
    Console.WriteLine("İyi");

if (sayı >= 85 && sayı <= 100)
    Console.WriteLine("Pekiyi");

if ((sayı < 0 || sayı > 100))
{
    Console.WriteLine("Yanlış Sayı Birimi Girdiniz.");
    goto baslangıc;
}
Console.ReadKey();
Console.WriteLine("--------------------------------------"); 
```
                       
