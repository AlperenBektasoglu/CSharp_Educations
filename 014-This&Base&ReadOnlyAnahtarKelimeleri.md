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
      }
  }

}

// Çıktı:
// 2 Parametreli Yapıcı Metod
// 1 Parametreli Yapıcı Metod
// Parametresiz Yapıcı Metod
```

## Base Anahtar Kelimesi
1. Madem ki, herhangi bir sınıftan nesne üretimi gerçekleştirilirken öncelikle base
class'ından nesne üretiliyor, bu demektir ki önce base class'ın constructor'ı tetikleniyor.
Haliyle bizler nesne üretimi esnasında base class'ta üretilecek olan nesnenin istediğimiz
constructor'larını tetikleyebilmeli yahut varsa parametre bu değerleri verebilmeliyiz.
İşte bunun için base Keyword'ü nü kullanmaktayız.
2. Ayrıca nasıl ki this, ilgili sınıfta o anki nesnenin memberlarına erişebilmemizi sağlıyor,
aynı şekilde base'de base class'da ki memberlara erişebilmemizi sağlamaktadır.

**Not:** Eğer ki base ifadesi yok ise, base sınıfın parametresiz constructor'ı o da yok ise 
base sınıfın default constructor'u çalışacaktı.

```cs
namespace EducationWorkspace
{

    class A
    {
        public int x;
        public A()
        {
            Console.WriteLine("parametresiz A const. çalıştı.");
        }

        public A(int x) : this()
        {                          
            this.x = x;
            Console.WriteLine("A const. çalıştı. x degeri: " + x);
        }
    }
    class B : A
    {
        public B() : base(100)                        
        {                       
            Console.WriteLine("parametresiz B const. çalıştı.");
        }

        public B(int z) : base(150) // 1. Madde Örneği
        {
            Console.WriteLine("B const. çalıştı. z degeri: " + z);
        }
    }
    class C : B
    {
        public C()
        {
            base.x = 150; // 2. Madde Örneği
            Console.WriteLine("parametresiz C const. çalıştı.");
        }

        public C(int k) : base(k)
        {
            Console.WriteLine("c const. çalıştı.");
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            C c = new C(50);
            Console.WriteLine(c.x);
            Console.ReadLine();
        }
    }

}

// Çıktı:
// parametresiz A const. çalıstı.
// A const. çalıstı. x degeri: 150
// B const. çalıstı. z degeri: 50
// c const. çalıstı.
// 150
```

## ReadOnly Anahtar Kelimesi
* Bir sınıf içerisinde tanımlanmış olan değişkenin yahut referansın sadece okunabilir olmasını sağlayan anahtar kelimedir.
* Readonly ile işaretlenmiş olan referansların değerleri ya tanımlama noktasında ya da constructor'da verilebilir.
* Const yapılar, readonly ile karıştırılabilir. Aralarındaki fark şöyledir; const bir değişkene tanımlandığı yerde
değeri verilmelidir ve constructor içerisinde bile değer ataması gerçekleştirilemez. Lakin readonly bir değişkene
ister tanımlama noktasında isterseniz de constructor içerisinde değer ataması gerçekleştirilebilir.




















