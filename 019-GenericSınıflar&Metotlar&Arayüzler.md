
# C# – Generic Sınıflar, Metotlar ve Arayüzler
## Generic Sınıflar 
```cs
public class Example
{
    public int example_1;
    public void example_2(int parameter) { }
}
``` 
Example sınıfında example_1 değişkeninin veri tipini ve example_2 metodunun parametresinin veri tipini de int olarak belirttik. Artık example_1 değişkenine int haricinde bir değer 
atamamız veya example_2 metoduna int’den farklı bir parametre göndermemiz mümkün değildir. Generic yapıyı kullandığımız takdirde sınıf içerisindeki değişkenlerin, parametrelerin ve 
metotların geri dönüş tiplerini o sınıftan bir nesne oluştururken belirleyebilmekteyiz. Yani Generic’ler sayesinde bir sınıfın elemanlarının veri tiplerini ihtiyaç doğrultusunda yeni 
bir sınıf tanımlamaya gerek kalmadan değiştirebilmekteyiz.
```cs
public class Example<T>
{
    public T example_1;
    public void example_2(T parameter) { }
}
```
Example sınıfından nesne oluştururken T (T yerine farklı bir isim verilebilir, isteğe bağlı) yerine hangi veri tipini yazarsak; sınıf içerisindeki değişken ve parametrenin tipi o şekilde olacaktır.
```cs
class Program
{
    static void Main(string[] args)
    {
        Example<int> exp_1 = new Example<int>();
        exp_1.example_1 = 18;
        exp_1.example_2(128);
        Example<string> exp_2 = new Example<string>();
        exp_2.example_1 = "Alperen Bektaşoğlu";
        exp_2.example_2("C# - Generic Sınıflar");
    }
}
```
## Generic Metotlar
Bazen bir sınıf içerisindeki metotların sadece birkaçını Generic olarak kullanmak isteyebiliriz. Böylesi bir durumda sınıfı Generic yapmak yerine sadece ilgili metotları Generic yapmak çok daha mantıklı olacaktır.
```cs
public class Example
{
    public int example_1(int parameter)
    {
        return parameter;
    }
    public T example_2<T>(T parameter)
    {
        return parameter;
    }
}

class Program
{
     static void Main(string[] args)
     {
         Example exp_1 = new Example();
         Console.WriteLine(exp_1.example_1(18));
         Console.WriteLine(exp_1.example_2(true));

         Console.WriteLine(exp_1.example_2<string>("Alperen Bektaşoğlu"));
         Console.WriteLine(exp_1.example_2<double>(3.14));
    }
}
```

## Generic Arayüzler
Tıpkı sınıflarda olduğu gibi arayüzleri de Generic olarak tanımlayabiliriz.
```cs
public interface IExample<T>
{
    T example_1(T input);
    void example_2(T input1, T input2);
}
```
Tek fark; Generic sınıflarda veri tipini o sınıftan bir nesne oluştururken belirtmekteyiz, 
Generic arayüzlerde ise veri tipini, o arayüzü bir sınıfa implement ederken belirtmekteyiz.
```cs
public class ExampleClass_1 : IExample<int>
{
    public int example_1(int input) { return input; }
    public void example_2(int input1, int input2) { }
}
public class ExampleClass_2 : IExample<string>
{
    public string example_1(string input) { return input; }
    public void example_2(string input1, string input2) { }
}
```

## Arayüzlerde Generic Metot Bildirimi 
Arayüz içerisindeki metotların tamamı Generic değilse; Arayüz yerine sadece ilgili metotları Generic yapmak daha mantıklı olacaktır, tıpkı Generic metotlarda anlattığımız gibi.
```cs
public interface IExample
{
    void example_1(int input);
    T example_2<T>(T input);
}
public class ExampleClass_1 : IExample
{
    public void example_1(int input) { }
    public T example_2<T>(T input) { return input; }
}
```
IExample arayüzü Generic olmadığı için herhangi veri tipi belirtmeden ExampleClass_1 sınıfına implement edebildik. example_2 metodu Generic olduğu için veri tipi metot çağrılırken girilecektir.
```cs
class Program
{
    static void Main(string[] args)
    {
        ExampleClass_1 example = new ExampleClass_1();
        example.example_1(18);
        example.example_2<string>("Serdar YILMAZ");
    }
}
```

## Statik Generic Sınıflar
Statik sınıflar ile statik olmayan sınıfların Generic yapılması noktasında arada herhangi bir fark bulunmuyor. Statik sınıfların metot ve değişkenlerine 
nesne oluşturmadan erişebildiğimiz için, veri tipini sınıf adını yazdıktan hemen sonra belirtiyoruz.
```cs
public static class Example<T>
{
    public static T example_1(T input) { return input; }
}
class Program
{
    static void Main(string[] args)
    {
        Example<string>.example_1("Alperen Bektaşoğlu");
    }
}
```

## Generic’lerde Birden Fazla Veri Tipinin Kullanılması

```cs
public class Example<T, Y, C>
{
    public T example_1;
    public void example_2(Y parameter1, C parameter2) { }
}
class Program
{
    static void Main(string[] args)
    {
        Example<int, string, bool> example = new Example<int, string, bool>();
        example.example_1 = 18;
        example.example_2("Serdar YILMAZ", true);
    }
}
```

## Generic Kısıtlar
### Değer ve Referans Tip Kısıtı
```cs
public class ExampleClass<T>
{
    public T example_1 { get; set; }
    public T example_2(T parameter)
    {
        return parameter;
    }
}
```
ExampleClass Generic sınıfına herhangi bir kısıt uygulanmadığı için T yerine int, double, float gibi değer tipleri gönderebileceği gibi; string, object, array gibi referans tipleri de gönderilebilir.

* Değer Tipleri: “int”, “long”, “float”, “double”, “decimal”, “char”, “bool”, “byte”, “short”, “struct”, “enum”
* Referans Tipleri: “string”, “object”, “class”, “interface”, “array”, “delegate”, “pointer”

Oluşturduğumuz ExampleClass Generic sınıfına sadece referans tip veya sadece değer tip gönderilmesini isteyebiliriz. Böylesi bir durumda Generic sınıfımıza bir kısıt koymamız gerekmekte.
Sadece referans tip gönderilmesi için;  
```cs
public class ExampleClass<T> where T:class
{
    public T example_1 { get; set; }
    public T example_2(T parameter)
    {
        return parameter;
    }
}
```
Sadece değer tip gönderilmesi için; 
```cs
public class ExampleClass<T> where T : struct
{
    public T example_1 { get; set; }
    public T example_2(T parameter)
    {
        return parameter;
    }
}
```

### new() Kısıtı
Generic sınıfa gönderilen veri tipini, sınıf içerisinde new’liyorsak, yani o tipten yeni bir nesne oluşturuyorsak; Generic sınıfa “new()“ kısıtını 
uygulamamız gerekmektedir. Eğer Visual Studio ile geliştirme yapıyorsanız zaten IDE sizi new() kısıtını uygulamaya zorlayacaktır.
```cs
public class ExampleClass<T> where T : new()
{
    public T createObject()
    {
        T obj = new T();
        return obj;
    }
}
```
ExampleClass Generic sınıfında gönderilen veri tipi createObject metodunda new’lenerek yeni bir nesne oluşturulmak istendiğinden new() kısıtı uygulanmıştır. 
Artık ExampleClass Generic sınıfına sadece nesne oluşturulabilen yani new() lenebilen türler gönderilebilir.

### Arayüz kısıtı
Generic sınıfa sadece belirttiğimiz arayüzleri implement alan türlerin gönderilmesini istiyorsak arayüz kısıtını uygularız.
```cs
public interface IExample1 { }
public interface IExample2 { }
public class ExampleClass1 : IExample1
{
    public string example_1 { get; set; }
}
public class ExampleClass2 : IExample1
{
    public string example_1 { get; set; }
}
public class ExampleClass3 : IExample2
{
    public string example_1 { get; set; }
}
```
IExample1 ve IExample2 isminde iki arayüz oluşturduk. IExample1 arayüzünü ExampleClass1 ve ExampleClass2‘ye implement ettik. IExample2 arayüzünü de ExampleClass3 sınıfına implement ettik.
```cs
public class GenericClass<T> where T : IExample1
{
    public T example_1 { get; set; }
    public T example_2(T parameter) { return parameter; }
}
```
Generic sınıfımıza “where T : IExample1” kısıtını eklediğimiz takdirde; Generic sınıfımıza veri türü olarak sadece IExample1 arayüzünü implement alan ExampleClass1 ve ExampleClass2 gönderilebilecektir. 
ExampleClass3 sınıfı IExample1 arayüzünü implement almadığı için GenericClass’a veri tipi olarak gönderilmek istendiğinde hata alınacaktır. Arayüz kısıtı sayesinde Generic 
sınıflara sadece belli arayüzleri implement alan sınıfların gönderilmesini sağlayabiliriz.

### Birden Fazla Kısıt Ekleme
```cs
public interface IExample1 { }
public class ExampleClass<T> where T : class, IExample1 , new()
{
    public T createObject()
    {
        T obj = new T();
        return obj;
    }
}
```
ExampleClass Generic sınıfına sadece referans tipli olan, IExample1 arayüzünü implement alan ve new’lenebilen veri türleri gönderilebilir.
**Not:** new() kısıtı her zaman en son da yer almalıdır.

Generic kısıtları tıpkı sınıflarda kullandığımız gibi generic metotlarda da kullanabiliriz.
```cs
public class ExampleClass
{
    public T createObject<T>() where T : class, IExample1, new()
    {
        T obj = new T();
        return obj;
    }
}
```
createObject Generic metoduna sadece referans tipli olan, IExample1 arayüzünü implement alan ve new’lenebilen veri türleri gönderilebilir.



