
## Abstarction(Soyutlama) Kavramı
Abstraction, bir sınıfın memberlarından ihtiyaç noktasında alakalı olanları gösterip, alakasız olanları göstermemektir diyebiliriz.
Bunu normal sınıflarla öyle yada böyle gerçekleştirebilirsiniz lakin bu davranışı uygularken sadece interfaceler yahut abstract classlar
diğer yapılara göre daha elverişli olabilmektedirler. Ayrıca sınıfların birden fazla interface ile implement edilebilmeleri, ilgili 
sınıfın birden fazla referans ile refere edilebilmesi anlamına geleceğinden dolayı, interfacelerin abstraction işlemleri için
oldukça yaygın olarak kullanılan yapılar olduğunu söyleyebiliriz. Bununla birlikte şu sonucu çıkarabiliriz ki; abstraction, bir
sınıfın belirli bir davranışa sahip olduğunun garantisini sağlamaktadır.

## Abstract Class
* Abstract anahtar kelimesi sınıflara, metotlara ve propertylere uygulanabilir.
* Temel(base) sınıfları tamamen kalıtım amaçlı kullanacağımız zaman Abstract anahtar sözcüğünü kullanırız. 
* Abstract bir sınıf oluşturabilmek için erişim belirtecinden sonra “abstract” anahtar sözcüğünü yazmamız gerekmektedir. 
* Abstract sınıflardan new anahtar kelimesi ile bir nesne oluşturulamaz.
* Abstract sınıflar içerisinde hem memberlar tanımlayabilir hem de arayüzler de (interface) olduğu gibi member bildirimi yapabiliriz.
* Abstract sınıflarda member bildirimi yapabilmek için erişim belirtecinden sonra “abstract” anahtar sözcüğünü yazmamız gerekmektedir.
* Abstract metotlar ve propertyler sadece abstarct sınıflar içerisinde tanımlanır.
* Abstract memberların yapacakları işlemler(gövdeleri), miras alan sınıfta override keyword'ü ile kodlanmalıdır. Abstract classlar sanal sınıflardır.
virtual - override yapısından tek farkı ezme işlemin zorunlu kılar.
* Abstract classlar içinde tanımlanan abstract metodlar yada propertylerin gövdeleri, abstract class'ı miras alan her sınıfta
oluşturulmak zorundadır.
*  Abstact classlar içinde tanımlanan abstact metodlar yada propertyler public olmak zorundadır.
*  Abstract classların nesnesi oluşturulmaz ama referans noktası alınabilir.

**Not:** Bir sınıf, bir sınıfa miras verdiği zaman kalıtım denir. Bir Abstract class yada interface, bir sınıfa kalıtım vermez. İmplementasyonu
yapılır yani uygulanır. Bir abstract class bir abstract class'a kalıtım verir çünkü abstract classlar içlerinde abstract olarak işaretlenmiş olan
yapıları zoraki olarak sadece kendilerini uygulayan sınıflara uygulatırlar, Abstract classlara değil.







