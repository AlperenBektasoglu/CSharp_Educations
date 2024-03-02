# Hata Yönetimi

## Hata Yönetimi İle İlgili Genel Bilgiler

Hatalar çeşidi sayısı üçtür: Yazım Hataları(Syntax Error), Çalışma Zamanı Hataları (Run Time Error) ve Mantıksal Hatalar (Logical Error).
Aşağıda try-catch yapısının özellikleri anlatılmıştır.

1. Yazım hataları (Syntax errors) derleme zamanında alınır. Gelişmiş IDE'lerde derleme sürecinden önce de syntax hataları tespit edilebilir.
1. Try catch ile yakalanan hatalar çalışma zamanı (runtime) hatalarıdır.
1. Try catch yapısı maliyetlidir. Hata oluşma ihtimali olan kodlar için kullanmalısınız.
1. Catch yapısındaki parametre zorunlu değildir.
1. Exception sınıfı bütün hata tiplerinin atasıdır. Object ise exception sınıfının atasıdır.
1. Hata türüne göre birden fazla catch bloğu oluşturulabilir. Gelen hataya göre sırayla yukarıdan aşağıya göre inceleyerek uygun olan catch bloğuna girer.
1. Catch bloklarının en sonuna Exception tipinde parametre alan catch bloğu koyarsak, gelen hata üstteki catch bloklarına uygun değilse bu catch bloğu çalışır.
1. Hata oluşsada oluşmasada çalıştırılmak istenen kodlar finaly bloğu içerisine yazılır.

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

Yararlı Kaynaklar:

1. Kaynak: <https://www.srdrylmz.com/c-istisnai-durum-yonetimi/>
2. Kaynak: <https://www.srdrylmz.com/c-exception-sinifi-olusturma/>
3. Kaynak: <https://www.srdrylmz.com/c-merkezi-istisnai-durum-yonetimi/>

## Throw Kullanımı

Throw deyimi, program çalışması esnasında özel bir durum geçişi için hata fırlatmaya yarar. System.Exception dan türetilmiş bir sınıf geriye döner.

```cs
class CustomException : Exception
    {
        public CustomException() : base("Exception için hata mesajıdır!") { }
    }

class Program
{
    static void Main(string[] args)
    {
       if(1 == 1)
           throw new CustomException();
    }
}
```

Yararlı Kaynaklar:

1. Kaynak: <https://www.srdrylmz.com/c-istisnai-durum-yonetimi/>
2. Kaynak: <https://www.srdrylmz.com/c-exception-sinifi-olusturma/>
3. Kaynak: <https://www.srdrylmz.com/c-merkezi-istisnai-durum-yonetimi/>
