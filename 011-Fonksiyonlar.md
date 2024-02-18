# Fonksiyonlar
Fonksiyonlar programlamanın en küçük iş yapan parçacıklarıdır. C# da fonksiyon kullanmak, size oluşturduğunuz kod bloğunu 
programın herhangi bir yerinde tekrar tekrar çalıştırma imkanı verir. Metodlar sınıf elemanlarıdır. Dolayısı ile sınıfların içerisinde
tanımlanırlar. C# ın ileriki versiyonlarında metodlar başka yerlerde de(interface, fonksiyon içi vs.) tanımlanabilmektedir. Metodlar,
imza ve gövdeden oluşur. Aşağıda metot İmzasınının yapısı mevcuttur.

[Erişim Belirleyicisi] [Geri Dönüş Değeri] [Metod Adı] ([Parametreler])
{
  // Burası metod gövdesidir. Kodlar buraya yazılır.
}

**Not:** Main de bir fonksiyondur ve her programda en az ve en fazla 1 tane olmak zorundadır.
**Not:** Return komutu ile değer döndürülebilir. Değer döndürmeyen fonksiyonların geri dönüş değeri void tir.
**Not:** Metotlarda static ifadesinin kullanılması ile sınıftan nesne üretmeden o metodun kullanımı sağlanmış olur. Static
ifadesi konulmaz ise o metodu kullanabilmek için metodun bulunduğu sınıftan nesne üretilmek zorundadır.
**Not:** Başka bir sınıftaki metodu kullanabilmek için o sınıftan nesne üretmek gerekir. Metotlarda static ifadesinin kullanılması ile 
sınıftan nesne üretmeden o metodun kullanımı sağlanmış olur. Static ifadesi konulmaz ise o metodu kullanabilmek için metodun 
bulunduğu sınıftan nesne üretilmek zorundadır.

```cs
class Program
{
    public int Topla(int x, int y) {
        return x + y;
    }
    
    static void Main(string[] args)
    {
        Console.WriteLine(Topla(2,5));
    }
}
```
## Erişim Belirleyicileri (Access Modifiers)
Erişimin sınırlarını belirlemek için kullanılır.         
1. Private: Sadece tanımlandığı sınıf içerisinden erişilebilir.
2. Public: Her yerden erişilebilir.
3. Protected: Sadece tanımlandığı sınıfta ya da o sınıfı miras alan sınıflardan erişilebilir. Dikkat edilmesi gereken nokta
   sadece türetilmiş sınıflar erişebilir, torun sınıflar erişemez.
4. Internal: Sadece bulunduğu projede erişilebilir.(Aynı assembly içerisinden erişilebilir.)
5. Protected-Internal: Bir nesne protected internal olarak tanımlandığında aynı protected gibi kendi bulunduğu 
   sınıf üzerinde ve bu sınıfı miras alan sınıflar üzerinden çağrılabilir. Artı olarak 
   aynı proje (assembly/dll) üzerinden de çağırılabilir.

**Not:** Bir sınıfın erişim belirleyicisi yazılmaz ise default erişim belirleyicisi Internal dır.
**Not:** Sınıfın içindeki bir değişkenin yada metodun erişim belirleyicisi yazılmaz ise default erişim belirleyicisi Private dır.

## Metotlarda Optional Parameters(İsteğe Bağlı Parametreler)
Metod parametrelerine = operatörü ile bir dğer atanır ise o parametre varsayılan değeri atanmış olur.
Haliyle opsiyonel parametre olarak kullanılabilir. Opsiyonel parametreler parametre sırasında en sağ tarafa
yazılırlar.

```cs
class Program
{
    public int Topla(int x, int y = 10) {
        return x + y;
    }
    
    static void Main(string[] args)
    {
        Console.WriteLine(Topla(2);
    }
}
```

## Metotlarda Non Trailing Named Arguments Özelliği
Bu özellik ile metoda geçilen parametreler sırayla verilme zorunluluğu ortadan kaldırılmıştır.

```cs
class Program
{
  public int Topla(int x, int y,  int z = 10) {
      return x + y;
  }
  
  static void Main(string[] args)
  {
      Console.WriteLine(Topla( z: 20, x: 10, y:200 ));
  }
}
```

## Değişken Sayıda Parametre Alan Metotlar (Params Anahtar Kelimesi)
C#'ta params anahtar kelimesi, değişken sayıda argüman(parametre) alan bir parametreyi belirtmek için kullanılan anahtar kelimedir.
Yalnızca bir params anahtar sözcüğüne izin verilir ve bir fonksiyon bildiriminde params anahtar sözcüğünden sonra hiçbir ek parametreye 
izin verilmez.

Link: https://www.srdrylmz.com/c-degisken-sayida-parametre-alan-metotlar/
 
```cs
class Program
{
   public void ShowForInt(params int[] val) // Params Paramater  
   {
        for (int i = 0; i < val.Length; i++)
        {
            Console.WriteLine(val[i]);
        }
    }
    
    public void ShowForObject(params object[] items) // Params Paramater  
    {
        for (int i = 0; i < items.Length; i++)
        {
            Console.WriteLine(items[i]);
        }
    }
    
    static void Main(string[] args)
    {
        ShowForInt(2, 4, 6, 8, 10, 12, 14); // Değişken uzunluktaki argümanları iletme
        Console.WriteLine("\n------------------------------------------");
        ShowForObject("Ramakrishnan Ayyer", "Ramesh", 101, 20.50, "Peter", 'A'); // Değişken uzunluktaki argümanları iletme
    }
}
```

##  Local Functions (Lokal Fonksiyonlar)
Metodlar struct, abstract class, interface, record ve class içerisinde tanımlanamabilir. C# 7.0 ile gelen bu özellik ile metod içerisinde
metod tanımlanabilir. Bu tanımlanan metoda lokal fonksiyon denir. Lokal fonksiyonlar sadece tanımlandığı metod içerisinde erişilebilir.
Lokal fonksiyonlarda erişim belirleyicisi yazılmaz. lokal fonksiyon tanımlandığı fonksiyonun adından farklı bir isimde olmak zorundadır.

```cs
public static int X(){
  Y();
  void Y(){...}
  Y();
  return 0;
}
```
**Not:"" Ana fonksiyonun içerisindeki değişkenlere lokal fonksiyondan erişilmesini istemiyorsan lokal fonksiyonu static ile işaretleyebilirsin ve
ihtiyacın olan parametreleri lokal fonksiyona parametre olarak geçebilirsin.

## Recursive Fonksiyonlar
Kendi içerisinde kendini çağıran fonksiyonlardır. Öngörülemeyen, derinliği tahmin edilemeyen durumlarda tercih edilmektedir.
```cs
public void X(int a=1){
    Console.WriteLine("Merhaba");
    if( a < 3)
      X(++a);
    Console.WriteLine("Dünya");
  
    // Output: Merhaba Merhaba Merhaba Dünya Dünya Dünya
}
```



## C# Hazır Sınıflar Ve Fonksiyonlar
1. Math sınıfı, bir çok matamatiksel işlemleri rahatlıkla yapabilmemizi sağlar. İçerisinde matematiksel bir çok özellik ve metod barındırır.
```cs
int val1 = Math.Abs(-5); // Mutlak değer işlemini yapar.
int val2 = Math.Ceiling(3.14); // Yukarı yuvarlama işlemini yapar. (val2: 4)
int val3 = Math.Floor(3.87); // Aşağı yuvarlama işlemini yapar. (val3: 3)
int val4 = Math.Round(3.50); // Genel yuvarlama işlemini yapar. (val4: 4)
int val5 = Math.Pow(2, 3); // Üs alma işlemini yapar. (val5: 8)
int val6 = Math.Sqrt(4); // Karakök alma işlemini yapar.
int val7 = Math.Truncate(3.14) // Ondalıklı sayının tam kısmını getirir. (val7: 3)
```

2. DateTime sınıfı, tarihsel işlemlerle iligili birçok hazır özellik ve metod barındırır.
```cs
DateTime tarih1 = new DateTime(2021, 01, 01);
DateTime tarih2 = new DateTime(2022, 01, 01);

var val1 = Datetime.Now; // Kodun çalıştırıldığı andaki tarihi ve saati getirir.
var val2 = Datetime.Today; // Kodun çalıştırıldığı andaki tarihi, saat bilgisini sıfırlayarak getirir.
var val3 = DateTime.Compare(tarih1, tarih 2); // İki tarihi kıyaslar. Sonuç olarak -1, 0 ve 1 değerini döndürür.
// tarih1<tarih2 => -1
// tarih1=tarih2 => 0
// tarih1>tarih2 => 1
var val4 = tarih1.AddYears(100); // ilgili tarihe parametre olarak verilen yıl verisini ekleme işlemini yapar.
```
Bunlar dışında add metodlarıda(AddHours(), AddYears() vs.) vardır. Bunlarda ilgili tarihe belirtilen değeri ekler.

3. TimeSpan sınıfı, C#’ta DateTime yapısından farklı olarak, elimizdeki bir tarih değerine göre süre tutmamızı sağlar.
TimeSpan, DateTime gibi struct(yapı) olarak tasarlanmış bir süre temsil eden değişkendir.
```cs
TimeSpan time1 = new TimeSpan(3, 2, 17, 1, 12); // time1 değişkeni 3 gün, 2 saat, 17 dakika, 1 saniye ve 12 milisaniye olarak bir süre tutar.

DateTime tarih1 = new DateTime(2021, 01, 01);
DateTime tarih2 = new DateTime(2022, 01, 01);
TimeSpan time2 = tarih1 - tarih2; // İki DateTime tipindeki veriyi birbirinden çıkarınca TimeSpan tipinde değer döner.
```
TimeSpan ile ilgili daha detaylı bilgi için aşağıdaki linki inceleyebilirsiniz.
Link: https://www.gencayyildiz.com/blog/c-timespan-ile-sure-formatlama/

4. Random sınıfı, rastegele sayılar üretmek için kullanılır.
```cs
Random random = new Random();
var val1 = random.(); // 0 - int[Max] arasında rastgele sayı üretir.
var val2 = random.(100); // 0 - 100 arasında rastgele sayı üretir. 100 dahil değil.
var val3 = random.(50, 100); // 50 - 100 arasında rastgele sayı üretir. 100 dahil değil.
var val4 = random.NextDouble(); // 0-1 arasında rastgele ondalıklı sayı üretir.
```


