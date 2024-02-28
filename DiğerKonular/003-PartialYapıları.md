
## Partial Yapıları 
* Bir sınıfın, struct'ın yahut interface'in aynı yahut farklı dosyalarda birden fazla parçasının tasarlanmasını
lakin bu parçaların özünde bir bütün olarak kullanılmasını sağlayan, kodun daha organize ve kolay okunabilirliğini artıran özelliktir.
Normal şartlarda aynı namespace altında birden fazla aynı isimde yapı bulundurulamaz ama bu yapılar partial olarak tasarlanıyorsa
bu mümkündür. Tabi unutmamak lazım ki, fiziksel olarak farklı olan bu tanımların birbirlerinin parçaları olabilmesi için
aynı namespace içerisinde, aynı isimde ve aynı yapıda olmaları gerekmektedir.
* İç içe partial oluşturulabilir.

```cs
namespace EducationWorkspace
{
    partial class A
    {
        partial class B{}
        public virtual void method1()
        {
            Console.WriteLine("A sınıfı - metod1");
        }
    }

    partial class A
    {
        partial class B{}
        public void method2()
        {
            Console.WriteLine("A sınıfı - metod2");
        }
    }
}
```

## Partial Metotlar Nedir?
* Partial yapılar, partial metodlar barındırabilirler. Partial metodlar, sınıfın bir parçasında
geliştiricinin metod bildiriminde bulunmasını sağlar. Başka bir parçasında ise diğer geliştirici tarafınan
bu metod tanımlanabilir. Eğer şablonu tanımlanan metod uygulanmazsa derleyici tarafından metodun imzası ve
o metoda dair yapılan tüm çağrılar kaldırılır.
* Partial metotlar, çalışma zamanında var olup olmayacakları kesin olmadığı için, uygulanıp uygulanmayacaklarına bağlı
olarak çalışma zamanında mevcut olabilirler veya olmayabilirler.
* Partial metotlar, derleme sırasında yok sayılırlar eğer uygulanmazlarsa.
* Partial metotlar, delegate'lerle temsil edilemezler çünkü delegate'ler, çalışma zamanında kesin olarak var olan metotları referans ederler.
* Partial metotlar, partial yapılar içinde tanımlanabilir.
* Geri dönüş tipleri her zaman "void" olmak zorundadır partial metotlarda.
* Partial metotlar, static veya generic olabilirler.
* Partial metotlar, "out" parametreleri kabul etmezler ancak "ref" parametreleri kabul edebilirler.
* Partial metotlar, "virtual" olamazlar.
* Partial metotlar, tanım ve gövde olarak partial olarak işaretlenmelidir.
* Partial metotlar başka bir metot tarafından çağrıldıklarında, var oldukları bilinir, aksi takdirde derleyici tarafından göz ardı edilirler.
* Partial metotların gövdeleri tanımlandığında, public olarak işaretlenebilir ve nesne üzerinden erişilebilirler.
* Ancak, partial metotların gövdeleri tanımlanmamışsa, public olarak işaretlenemezler; çünkü derleyici, bu durumda gövdenin var olup olmadığını
bilemeyeceği için varsayılan olarak private olarak değerlendirir.

```cs
namespace EducationWorkspace
{

    partial class A
    {
        public A()
        {
            X();
            Y();
            Z();
        }

        partial void X();
        partial void Y();
        partial void Z();

    }

    partial class A
    {
        partial void Z()
        {
            Console.WriteLine("Z Metodu tetiklendi...");
        }
    }


    class Program
    {
        static void Main(string[] args)
        {
          A o1 = new A();
          Console.ReadLine();
        }
    }

}

// Çıktı:
// Z Metodu tetiklendi...
```





