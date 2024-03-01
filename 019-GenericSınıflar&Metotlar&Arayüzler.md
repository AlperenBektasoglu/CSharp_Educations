
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





















```cs

```
