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
                                 
**Not:** Field tanımlamadan da property oluşturulabilir. Bu durumda property aynı zamanda field gibi davranır.

**Not:** Bu üç tanım classlar içinde ileride anlatılacak struct yapılar içinde mevcuttur.

Property'lerin iki çalışma şekli vardır:
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

  // 1. olarak aşağıdaki şekilde tanımlandığında aslında Myproperty adında ve int tipinde bir değişken vardır.
  // Aşağıdaki property o değişkene kontrollü erişim sağlar.
  public int MyProperty { get; set; } // Bu işlemin adı AutoPropert dir. // Property

  // 2. olarak class içinde private bir field oluşturulur ve tanımlanan property o field'a kontrollü erişim sağlar.
  private string userLocation;
  public string userLocation // Property
  {
      get { return userLocation; }
      set { userLocation = value; }
  }
}
```
**Not:** Property olmadan da propertylerin sağladığı imkanı metodlarla da oluşturabilmekteyiz ama propertyleri kullanarak
kod kalabalığının önüne geçmiş oluruz.

## Encapsulation Nedir?
Bir nesne içerisindeki dataların dışarıya kontrollü bir şekilde açılması ve kontrollü bir şekilde veri almasıdır. 




















