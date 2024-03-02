# Struct Yapısı

Aralarında mantıksal ilişkiler bulunan farklı veya ayni türden bilgileri bir arada tutarak gruplamak ve daha kolay kullanmak için struct yapıları kullanılır. OOP'da class yapılarına benzerdir.

Struct yapısının özellikleri:

- Birbiri ile ilişkili verileri bir araya toplamak için kullanılır.
- Değer tiplidir. (Atama işleminde değerler kopyalanır)
- Stack'te saklanır. (Stack bellek hızlıdır ancak dardır ve çabuk şişer)
- Kalıtımı desteklemez.
- "New" anahtar kelimesinin kulanılma zorunluluğu yoktur.
- Struct parametresiz bir kurucu metod içeremez ama bir tane parametreli kurucu metod içerebilir.
- Struct yıkıcı metod içeremez.
- Struct yapılar içerilerinde metod, property veya field barındabilirler. Struct yapısı içinde ki metodları kullanabilmek için struct değişkenine "new" operatörüyle bir nesne bağlama zorunluluğumuz yoktur ama struct yapısı içindeki property yada field yapılarını kullanabilmek için struct’tan bir nesneye ihtiyacımız vardır.
- Struct yapılar içlerinde static elemanlar barındırabilirler ve bu static elemanlara struct ismi üzerinden . operatörü ile ulaşabilmekteyiz. ( Örnek: MyStruct.Islem(); )
- Bildiğiniz gibi "new" operatörü classlarda kullanıldığı zaman ilgili classtan bir nesne talep edilmekte ve üretilen nesne belleğin Heap kısmında muhafaza edilmektedir. Struct yapısında da "new" operatörünü kullanırsak ilgili stuct'tan bir nesne üretilecektir ama struct bir değer tipli değişken yapısında olduğundan dolayı o nesne belleğin Stack kısmında muhafaza edilecektir. Ayrıca "new" operatörünü kullanılarak struct'tan nesne üretildiğinde, struct içerisindeki fieldlara default değerleri atanmış olacaktır. "new" operatörünü kullanılmasaydı ilk değerleri atamadığımız ve kullanmaya çalıştığımız taktirde derleyici hata verecekti.
- Struct yapılar içerisinde class, class içerisinde de struct yapılar tanımlanabilir.

Kaynak: <https://www.gencayyildiz.com/blog/cta-struct-yapilari-ve-kullanim-durumlari/>

## C#'ta Class ve Struct Arasındaki En Önemli Farklılıklar Nelerdir?

- Structlar değer tiplidir ve stack'de tutulur. Classlar referans tiplidir ve heap'te tutulur.
- Structlar da "New" anahtar kelimesinin kullanılması zorunluluğu yoktur. Classlar da ise böyle bir zorunluluk vardır.
- Structlar da nesne oluşturulmaz ama classlar da nesne oluşturulur.
- Structlar, classlar'dan her zaman daha hızlı çalışır ve daha fazla performanslıdır. Çünkü stack bellek, heap bellekten her zaman daha hızlıdır.
- Struct yapısının içinde ilk değer ataması yapılamaz ama classların içerisinde ilk değer ataması yapılabilir.
- Struct ve class birbirinin yerlerine kullanılabilir. İkisi de benzer işleri yapar.
- Hız gerekli ise structlar, bellek gerekli ise classlar kullanılabilir.

```cs
struct Urun
{
    public int urunNo; // Field
    public string urunAdi;
    public string urunKategori;
    public string urunAciklama;
    public string satici { get; set; } // Property

    public Urun( int a, string b, string c, string d, string e) //Yapıcı Fonks.
    {
        urunNo = a;
        urunAdi = b;
        urunKategori = c;
        urunAciklama = d;
        satici = e;
    }

    public string urunAciklamaGetir(int id) // Metod
    {
        if (urunNo == id)
        {
            return urunAciklama;
        }
        else
            return "Böyle bir ürün yok.";
    }
}

static void Main(string[] args)
{
    Urun yeniurun1 = new Urun(15, "Tablet Pc", "Elektronik", "Ev Kullanımı İçin Uygun","Alperen Bektaşoğlu");
    Console.WriteLine(yeniurun1.urunNo);
    Console.WriteLine(yeniurun1.urunAdi);
    Console.WriteLine(yeniurun1.urunKategori);
    Console.WriteLine(yeniurun1.urunAciklama);
    Console.WriteLine(yeniurun1.satici);
    Console.WriteLine("-----------------------------------------");

    Urun yeniurun2 = new Urun(); // "new" operatörünü kullanılarak struct'tan nesne üretildiğinde, struct içerisindeki fieldlara default değerleri atanmış olacaktır.
    Console.WriteLine(yeniurun2.urunNo);
    Console.WriteLine(yeniurun2.urunAdi);
    Console.WriteLine(yeniurun2.urunKategori);
    Console.WriteLine(yeniurun2.urunAciklama);
    Console.WriteLine(yeniurun2.satici);
    Console.WriteLine("-----------------------------------------");

    Urun yeniurun3; // "new" operatörünü kullanılarak struct'tan nesne üretilmediğinde, struct içerisindeki fieldlara değer ataması yapmamız gerekir.
    yeniurun3.urunAdi = "Masa";
    Console.WriteLine(yeniurun3.urunAdi);
    // Console.WriteLine(yeniurun3.urunNo); // Bu satır hata verecektir.
    Console.WriteLine("-----------------------------------------");

    int urunId = 1;
    String aciklama = yeniurun1.urunAciklamaGetir(urunId);
}
```
