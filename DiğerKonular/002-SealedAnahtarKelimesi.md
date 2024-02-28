
## Sealed Keyword'ü Nedir? 
1. Sınıf için kullanıldığında, sınıfın miras vermesini engeller.

```cs
sealed class A // A sınıfının miras vermesi engellenmiştir.
{

}
```

2. Sealed anahtar kelimesi bir override metod için kullanılırsa ilgili sınıf başka bir sınıfa kalıtım aktaracağı
zaman metodun override edilmesini engellemiş olur. 

```cs
namespace EducationWorkspace
{

    class A
    {
        public virtual void method1()
        {
            Console.WriteLine("A sınıfı - metod1");
        }
    }
    class B : A 
    {
        public override void method1()
        {
            Console.WriteLine("B sınıfı - metod1");
        }
    }
    class C : B
    {
        sealed public override void method1()
        {
            Console.WriteLine("C sınıfı - metod1");
        }
    }
    class D : C
    {
        //  Aşağıdaki kod hata verecektir. Çünkü C sınıfında metod1 sealed ile işaretlenerek. Artık override edilmesinin önüne geçilmiştir.
        //  D sınıfından nesne üretilip, metod1 tetiklendiğinde en son override edilen metod tetiklenmiş olacaktır.

        //  public override void method1()
        //  {
        //    Console.WriteLine("C sınıfı - metod1");
        //  }
    }

    class Program
    {
        static void Main(string[] args)
        {
            D o1 = new D();
            o1.method1();

            Console.ReadLine();
        }
    }

}

// Çıktı:
// C sınıfı - metod1
```
