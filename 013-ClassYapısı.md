# Class(Sınıf) Yapısı 
Atık nesne tabanlı programlamaya(OOP) sınıflar ile giriş yapmış bulunmaktayız. 
Nesne(object)'ler sınıfların birer örneğidirler. Bu durumda sınıf, nesnelerin 
nasıl inşa edileceğini tanımlayan bir kılavuzdur diyebiliriz. Sınıf soyut bir ifadedir, 
nesneler oluşuncaya kadar fiziksel olarak bellekte yer almazlar.

Sınıf yapısının özellikleri:  
* Sınıflar bir referans tipidir.
* Sınıflar; namespace içerisinde, namespace dışarısında ve class içerisinde oluşturulabilirler.
  Fonksiyonlar vs gibi yapıların içerisinde tanımlanamazlar.
* Bir sınıf tanımlamasında, tanımlanan yerde aynı isimde birden fazla sınıf tanımlanamaz.
* Sınıflarda erişim belirleyicisi yazılır. Yazılmamış ise varsayılan olarak Internal'dır.
* Sınıf üyeleri için erişim belirleyicisi belirtilmediğinde varsayılan olarak Private olur.
* Sınıflar içerilerinde metod, property veya field barındabilirler.

**Not:** Belleğin stack alanında değer türlü değişkenler ve referanslar tutulur. Belleğin 
heap alanında ise sadece nesneler tutulur. Geliştirme sürecinde belleğin heap alanına doğrudan müdahale
edemediğimz için heapteki nesneyi stackte oluşturduğumuz bir referans ile işaretleyerek ulaşır ve kullanırız.

**Not:** Eğerki bir değişken sınıf içerisinde field olarak tanımlanıyorsa tpine göre default değeri verilir.
Yok eğer sınıfta değil metot vs. içerisinde tanımlanıyorsa default değer verilmez.

**Not:** Sınıf içerisindeki sınıf, ana sınıfın elemanı değildir.

**Not:** Oluşturulan referanslar bir nesneyi işaretlemiyorsa null değerini alır.

** Not:** Referans etmeden nesne oluşturabilmekteyiz. Referansız nesnelere ulaşılamaz.
          Bellekte yer kaplamaması için bir süre sonra garbage collector tarafından otomatik olarak silinir.

```cs
class Example1{
  private int userId; // Field // Default değeri = 0
  int userOld; 
  public string userName;
}

class Program
{
    static void Main(string[] args){
      new Example1(); // Heap te nesne oluşturur ama stack ta referans numarası oluşturmaz.
      Example1 o1 = new Example1();   // Heap bellekte nesne oluşturur ve stack bellekte "o1" adı ile referans numarası oluşturur.
      Example1 o2 = new Example1();   // o2 ve o3 referanslarının heap bellekte gösterdiği nesne aynıdır.
      Example1 o3 = o2;

      Example1 example1 = new Example1();
      example1.userOld = 100; // Sınıf üyelerine . operatörü üzerinden erişip kullanabilirsiniz.

      Example1 example2; // example2 = null
    }
}
```

## Field,Metod,Property Tanımı
* Field : Bir class yada struct içinde tanımlanan her tipten değişkendir.
* Metod : Bir class yada struct içinde tanımlanan fonksiyonlardır.
* Property :  Oluşturulan private field 'lara kontrollü bir şekilde erişim sağlanmak için 
              Property tanımlanmaktadır. Property tanımı ile bu alanları get edebilir, set edebilir 
              ya da her ikiniside aynı anda kullanabilirsiniz. Propertler özünde bir metottur.
              Yazılımcılar nesnelerin içerisindeki field'lara direkt erişilmesini istemez. Propertyler ile
              fieldları dışarı kontrollü bir şekilde açabiliriz. İçerisinde get ve set blokları vardır.
              Property hangi tipten bir field'ı temsil ediyorsa o tipten olmalıdır.

**Not:** Propertler genellikle temsil ettikleri fieldların isimlerinin baş harfi büyük olacak şekilde isimlendirilirler.
                                 
**Not:** Field tanımlamadan da property oluşturulabilir. Bu durumda property aynı zamanda field gibi davranır.

**Not:** Propertylerde set bloğu tanımlanmazsa sadece okunabilir(readonly) bilakis get bloğu tanımlanmazsa sadece
yazılabilir(writeonly) olacaktır.

**Not:** Bu üç tanım classlar içinde ileride anlatılacak struct yapılar içinde mevcuttur.

Property imza çeşitleri:
```cs
class Example1{
  private int userId; // Field
  int userOld;   
  public string userName;
  protected string userSurname;

  public void metod1() // Metod
  {
      Console.WriteLine("Metod1 e hosgeldiniz...");
  }

  // 1. Full Property
  // Sınıf içinde private bir field oluşturulur ve tanımlanan property o field'a kontrollü erişim sağlar.
  int sayı1;
  public int MyProperty1 {
      get{
        return sayı1;
      }
      set{
        sayı1 = value;
      }
  }

  // 2. Prop Property (AutoPropert)
  public int MyProperty2 { get; set; } // Prop propertler compile edildiklerinde arka tarafta kendi field'larını oluştururlar. Dolayısıyla field tanımlamaya gerek yoktur.

  // 2.1 AutoProperty Initializer
  // Bu özellik ile AutoProperty'ye ilk değer atanabilir.
  public int MyProperty3 { get; set; } = 10;

  // 3. Ref Readonly Returns
  // Bir sınıf içerisindeki field'ı referansıyla döndürmemizi sağlayan, bununla birlikte değişkenin değerini read only yapan özelliktir.
  string isim = "Alperen Bektaşoğlu";
  public ref readonly string Isim => ref isim;

  // 4. Expression - Bodied Property
  // Tanımlanan propertyler de Lambda Expression kullanmamızı sağlayan söz dizimidir. Expression - Bodied Propertyler readonly dir.
  public string Cinsiyet => "Erkek"; // Get bloğu sonucu Erkek değeri döner.

  // 5. Inıt - Only Property
  // Nesnenin sadece ilk yaratılış anında propertlerine değer atanmaktadır. Devamında değiştirilemezler.
  public int MyProperty4 { get; init; };
}
```

![Alternatif Metin](Assets/Screenshot1.png)

**Not:** Property olmadan da propertylerin sağladığı imkanı metodlarla da oluşturabilmekteyiz ama propertyleri kullanarak
kod kalabalığının önüne geçmiş oluruz.

**Not:** Sınıfa ve sınıfın elemanlarına açıklama satırı nasıl eklemek için, eklenecek öğenin üstüne gelip "///" yazıp tab tuşuna
basmanız yeterlidir.

## Encapsulation Nedir?
Bir nesne içerisindeki dataların dışarıya kontrollü bir şekilde açılması ve kontrollü bir şekilde veri almasıdır.

## This Anahtar Kelimesi
This anahtar kelimesinin kullanım amaçları:
1. Sınıfın nesnesini temsil eder. İlgili sınıf yapılanmasının o anki nesnesine karşılık gelir.
2. Aynı isimde field ile metod parametrelerini ayırmak için kullanılır 1. maddedeki çalışma prensibi üzerinden.
3. Bir yapıcı metoddan başka bir yapıcı metodu çağırmak için kullanılır.

## New Operatörü
new operatörü nesne üretilirken kullanılmaktadır.

**Not:** Nesne üretilirken kullanılan new ifadedesinde ki parantezler yapıcı metodu çağırır.

**Not:** C#9.0 da gelen Target-Typed New Expressions özelliği ile aşağıdaki şekilde tanımlamakta mümkündür.
```cs
Example1 example1 = new Example1();
Example1 example1 = new (); //  Target-Typed New Expression
```

























