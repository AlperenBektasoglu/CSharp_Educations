## This Anahtar Kelimesi
This anahtar kelimesinin kullanım amaçları:
1. Sınıfın nesnesini temsil eder. İlgili sınıf yapılanmasının o anki nesnesine karşılık gelir.
2. Birinci maddedeki çalışma prensibi üzerinden, aynı isimde ki field ve metod parametrelerini ayırmak için kullanılır.
3. Bir yapıcı metoddan aynı sınıfın içerisindeki başka bir yapıcı metodu tetiklemek için kullanılır.

```cs
namespace WorkArea{

  class Example1{
    public string userName;

    public Example1() : this("Alperen")
    {
        Console.WriteLine("Parametresiz Yapıcı Metod");
    }

    public Example1(string userName) : this(userName, 10)
    {
        this.userName = userName; // 1. ve 2. Madde Örneği
        Console.WriteLine("1 Parametreli Yapıcı Metod");
    }

    public Example1(string userName, int yas){
        Console.WriteLine("2 Parametreli Yapıcı Metod");
    }
  }
  
  class Program
  {
      static void Main(string[] args){
          Example1 e1 = new Example1();
          // Output:
          // 2 Parametreli Yapıcı Metod
          // 1 Parametreli Yapıcı Metod
          // Parametresiz Yapıcı Metod
      }
  }

}
```

## Base Anahtar Kelimesi
* Madem ki, herhangi bir sınıftan nesne üretimi gerçekleştirilirken öncelikle base
class'ından nesne üretiliyor, bu demektir ki önce base class'ın constructor'ı tetikleniyor.
Haliyle bizler nesne üretimi esnasında base class'ta üretilecek olan nesnenin istediğimiz
constructor'larını tetikleyebilmeli yahut varsa parametre bu değerleri verebilmeliyiz.
İşte bunun için base Keyword'ü nü kullanmaktayız.
* Ayrıca nasıl ki this, ilgili sınıfta o anki nesnenin memberlarına erişebilmemizi sağlıyor,
aynı şekilde base'de base class'da ki memberlara erişebilmemizi sağlamaktadır.

**Not:** Eğer ki base ifadesi yok ise, base sınıfın parametresiz constructor'ı o da yok ise 
base sınıfın default constructor'u çalışacaktı.

```cs

```






















