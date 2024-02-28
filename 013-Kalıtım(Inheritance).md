# Kalıtım (Inheritance)
C# Kalıtım, nesne yönelimli programlamanın en önemli özelliklerinden birisidir. Kalıtım sayesinde sınıf yapılarımız 
birbirinden türetilebilir. Yani bir sınıftan yeni bir sınıf oluşturma işlemine kalıtım denir. Bir sınıf herhangi 
bir üst sınıftan türetildiği zaman, türemiş olduğu sınıfın içerisindeki public ve protected erişim belirleyicilerine sahip
bütün üyelere sahip olur. Bir sınıf sadece tek bir sınıftan kalıtım alabilir. Kalıtımsal tüm ilişkiler : operatörü tarafından yapılmaktadır.

**Not:** C# programlama dilinde kalıtım sınıflara özel bir niteliktir. Record'lar da sınıf olduğundan kalıtım alabilmektedirler.
Lakin bir sınıf bir sınıftan, bir record ise bir recordan kalıtım alabilir.

**Not:** Mevcutta olan yada senin yeni oluşturduğun bütün sınıflar Object sınıfından miras almaktadır.

## Base Class ve Derived Class Nedir?
* Kalıtım veren sınıfa Base / Parent Class denir.
* Kalıtım alan sınıfa Derived / Child Class denir.
* Peki, atalar bütün torunlarının Base Class'ı mıdır? Hayır değildir.
A class -> B class -> C class kalıtım versin. Bu durumda C nin base classı B classıdır. B classının da base classı A classıdır.
* Bir class'ın sade ve sadece bir Base Class'ı olur.

## Kalıtımda Nesne Üretim Sırası
Bir sınıftan nesne üretimi yapılırken kalıtım aldığı üst sınıflar varsa eğer
önce o sınıflardan sırasıyla heap bellekte nesne üretilir. Yani buradan anlaşılıyor ki,
bir sınıftan nesne üretilirken siz 1 adet nesne ürettiğinizi düşünsenizde kalıtımsal
açıdan birden fazla nesne üretimi gerçekleşecektir. A class -> B class -> C class kalıtım versin. Bu durumda
C sınıfından nesne üretilmek istendiği zaman; sırasıyla heap bellekte A nesnesi, B nesnesi ve son olarak C nesnesi üretilir.

```cs
namespace EducationWorkspace
{
    class A
    {
        protected int aField;
        public A()
        {
            Console.WriteLine("A sınıfı const. çalıştı...");
        }
    }

    class B : A
    {
        public int bField;
        public B()
        {
            bField = aField;
            Console.WriteLine("B sınıfı const. çalıştı...");
        }
    }

    class C : B
    {
        public int cField;
        public C()
        {
            cField = aField;
            Console.WriteLine("C sınıfı const. çalıştı...");
        }
        public int metod1()
        {
            aField = 20;
            return aField;
        }
    }
    class Program
    {
        static void Main(string[] args)
        {
            A a = new A();
            Console.WriteLine("----------------------------");

            B b = new B();
            // b.bField
            Console.WriteLine("----------------------------");

            C c = new C();
            // c.bField
            // c.cField
            Console.WriteLine("----------------------------");

            Console.WriteLine(c.metod1());

            Console.ReadLine();
        }
    }
}

// Çıktı:
// A sınıfı const. çalıstı...
// ----------------------------
// A sınıfı const. çalıstı...
// B sınıfı const. çalıstı...
// ----------------------------
// A sınıfı const. çalıstı...
// B sınıfı const. çalıstı...
// C sınıfı const. çalıstı...
// ----------------------------
// 20
```

**Not:** A sınıfının içinde x adında değişken tanımlayalım. Eğerki bu değişken private olur ise ben A sınıfı miras alan C sınıfında da
x adında değişken tanımlayabilirim, çakışma olmaz. Eğerki A sınıfının içinde ki x değişkeninin erişim tipi private olmaz ise
ben A sınıfı miras alan C sınıfında da x adında değişken tanımladığım taktirde çakışma olur ve alt sınıf(C), üst sınıfın(A) 
değişkenini geçersiz kılar.



