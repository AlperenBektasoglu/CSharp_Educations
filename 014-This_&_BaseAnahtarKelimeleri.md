## This Anahtar Kelimesi
This anahtar kelimesinin kullanım amaçları:
1. Sınıfın nesnesini temsil eder. İlgili sınıf yapılanmasının o anki nesnesine karşılık gelir.
2. Birinci maddedeki çalışma prensibi üzerinden, aynı isimde ki field ve metod parametrelerini ayırmak için kullanılır.
3. Bir yapıcı metoddan aynı sının içerisindeki başka bir yapıcı metodu çağırmak için kullanılır.

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
