## Hata Yönetimi İle İlgili Genel Bilgiler
0. Hatalar çeşidi sayısı üçtür: Yazım Hataları(Syntax Error), Çalışma Zamanı Hataları (Run Time Error) ve Mantıksal Hatalar (Logical Error)
1. Yazım hataları (Syntax errors) derleme zamanında alınır. Gelişmiş ide'lerde derleme sürecinden öncede syntax hataları tespit edilebilir.
2. Try catch ile yakalanan hatalar çalışma zamanı (run time) hatalarıdır.
3. Try catch yapısı maliyetlidir. Hata oluşma ihtimali olan kodlar için kullanmalısınız.
4. Catch yapısındaki parametre zorunlu değildir.
5. Exception sınıfı bütün hata tiplerinin atasıdır. Object ise exception sınıfının atasıdır.
6. Hata türüne göre birden fazla catch bloğu oluşturulabilir. Gelen hataya göre sırayla yukarıdan aşağıya göre inceleyerek uygun olan catch bloğuna girer.
7. Catch bloklarının en sonuna Exception tipinde parametre alan catch bloğu koyarsak, gelen hata üstteki catch bloklarına uygun değilse bu catch bloğu çalışır.
8. Hata oluşsada oluşmasada çalıştırılmak istenen kodlar finaly bloğu içerisine yazılır.

 ```cs
 try
{
    Console.Write("Birinci sayıyı giriniz: ");
    int sayi_1 = Convert.ToInt32(Console.ReadLine());
    Console.Write("İkinci sayıyı giriniz: ");
    int sayi_2 = Convert.ToInt32(Console.ReadLine());
    double sonuc = sayi_1 / sayi_2;
    Console.WriteLine("Birinci sayının ikinci sayıya bölümü:{0}", sonuc);
}
catch (FormatException exception) when (sayi_1 > 0 && sayi_2 > 0)
{
    // Klavyeden sayı yerine harf veya karakter girildiğinde bu catch bloğu çalışacak.
    Console.WriteLine("Hata! Sadece sayı girilebilir. Hata Mesajı:{0}", exception.Message);
}
catch (DivideByZeroException exception)
{
    // sayi_2 değişkenine sıfır değeri atandığında bu catch bloğu çalışacak.
    Console.WriteLine("Hata! Bir sayının sıfıra bölümü sonsuzdur. Hata Mesajı:{0}", exception.Message);
}
catch (Exception exception)
{
    // Öngördüğümüz hatalar haricinde bir hata oluştuğunda bu catch bloğu çalışacak.
    // En sona yazılmalıdır. Aksi taktirde direk bu cath çalışır.
    Console.WriteLine("Beklenmedik bir hata oluştu. Hata Mesajı:{0}", exception.Message);
}
```

## Yararlı Kaynaklar
Kaynak: https://www.srdrylmz.com/c-istisnai-durum-yonetimi/
Kaynak: https://www.srdrylmz.com/c-exception-sinifi-olusturma/
Kaynak: https://www.srdrylmz.com/c-merkezi-istisnai-durum-yonetimi/


## Logical Pattern
switch expression'da and, or ve not gibi mantıksal operatörler kullanılabilmektedir. Relational pattern ile oldukça uyumludur.

## Not Pattern
switch expression'da not operatörünün kullanılabildiği bir desendir.
