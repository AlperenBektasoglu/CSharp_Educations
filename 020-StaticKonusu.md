# Static Konusu

## Static Elemanlar

- Bir sınıf içerisindeki metotlar, alanlar (field), özellikler (property) static olarak tanımlanabilir.
- Bir class'ta static üye için bellekte sabit bir yer açılır.
- Bir sınıf içerisindeki static olmayan üyelere o sınıftan oluşturduğumuz nesneler üzerinden erişiriz.
- Static olan üyelere ise nesne oluşturmadan, sınıf ismi ile erişiriz.
- Static olmayan üyeler static üyelere erişebilir ama static üyeler sadece static üyelere erişebilir.
- Sınıflarda static olarak tanımlanabilir.

**Not:** Static olmayan elemanlar nesneye özgü bilgileri tutarken static olan elemanlar uygulama çalıştığı sürece kendilerine en son atanan değeri tutarlar.

```cs
namespace EducationWorkspace
{
    class Example1
    {
        public int X;
        public static int Y;    // Static Field

        public int Carpma()
        {
            return X * Y;      // Static olmayan carpma isimli metod sınıf içindeki diğer elemanlara ulaşabiliyor.
        }

        public static void Göster()
        {
            // Console.WriteLine(X); // Static bir üye sadece static üyelere erişebilir.
            Console.WriteLine(Y);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            Example1 example1 = new Example1();
            example1.Carpma();
            example1.X = 100;
            Example1.Y = 200; //Static bir üye bu şekilde çağrılır.
            Example1.Göster(); //Static bir üye bu şekilde çağrılır.

            Console.ReadLine();
        }
    }

}
```

## Static Sınıflar

- Oluşturduğumuz sınıf içerisinde sadece static üyeler bulunuyorsa, sınıfı static olarak tanımlayabiliriz.
- Sınıfların static olarak tanımlanması bir zorunluluk değildir, sadece okunabilirliği arttıran bir yaklaşımdır. Sınıfının static olduğunu gören bir programcı, sınıf içerisinde sadece static elemanların bulunduğunu anlayacaktır.
- Static sınıflardan nesne oluşturulamaz. (new Matematik(); YANLIŞ)
- Static sınıf türünden referanslar oluşturulamaz. (Matematik m; YANLIŞ)
- Static sınıfların içinde static olmayan üyeler tanımlanamaz.
- Static sınıflarda kalıtım yoktur.

```cs
static class Matematik
{
    public static double Topla(params double[] Sayilar)
    {
        double Toplam = 0;
        for (int i = 0; i < Sayilar.Length; i++)
            Toplam = Toplam + Sayilar[i];
        return Toplam;
    }
    public static double Carp(params double[] Sayilar)
    {
        double Carpim = 1;
        for (int i = 0; i < Sayilar.Length; i++)
            Carpim = Carpim * Sayilar[i];
        return Carpim;
    }
}
```
