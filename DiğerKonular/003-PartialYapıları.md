
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
        public virtual void method2()
        {
            Console.WriteLine("A sınıfı - metod2");
        }
    }
}
```





