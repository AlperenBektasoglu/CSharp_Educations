
## Değişken Nedir?
Yazılımlar veri tutmaz. Yazılım için işlenecek veriyi RAM'de tutabilmek için değişkenler kullanılır.
Değişkenler; işlenecek verilerin RAM'e yazılmasını ve RAM'den okunmasını sağlar. Değişken oluşturuken
aşağıdaki kurallara uyulmalıdır;

1. Her değişkenin bir tipi ve ismi vardır. Değişkene isim verilirken anlamlı isimler verilmelidir.
2. Değişkenlere isim verilirken yalnızca harf (büyük ve küçük), rakam ve alt çizgi karakteri kullanılabilir.
3. Değişken ismi  bir harf veya alt çizgi ile başlamak zorundadır.
4. C# büyük küçük harfe duyarlı bir dildir: footballTeam ve FootballTeam ismindeki iki değişken farklı değişkenlerdir.
5. Değişken isimlendirmede özel keyword'ler kullanılamaz. Eğer ki değişken isimlendirmede özel keyword 
kullanmak istiyorsanız, bunu @ sembolünü kullanarak yapabilirsiniz.

```cs
string isim = "Alperen"; // 1. Madde için örnek
int @static = 100; // 5. Madde için örnek
```

## Veri Tipleri Nedir?
 Değişkenleri tanımlarken tutacağımız verinin tipini bildirmek zorundayız.
C# dilinde veri tipleri değer tipleri ve referans tipleri olmak üzere 2’ye ayrılır.
Değer tiplileri belleğin stack alanını kullanırken, referans tipleri heap bellek bölgesinde tutulur. 
Değer tiplerinde tutulan verilere direk ulaşılabilirken, heap bölgesinde tutulan verilere ulaşmak için Stack'te verinin 
adres bilgisini içeren bir referans tutulur ve veriye dolaylı bir erişim sağlanır.

Değer Tipleri (Value Type): “int”, “long”, “float”, “double”, “decimal”, “char”, “bool”, “byte”, “short”, “struct”, “enum”

Referans Tipleri (Referance Type): “string”, “object”, “class”, “interface”, “array”, “delegate”, “pointer”

**Not:** Değer tipli değişkenler null değeri alamazken referans tipli değişkenler null değeri alabilir.

## Stack Ve Heap Kavramları Nedir?
Kodumuz işletim sisteminde bir yer kaplar. Bu yerin boyutu kimi zaman belli yani değişmez iken kimi zaman ise 
kullanıcının program esnasında gireceği verilere göre değişebilecek durumdadır. Temel olarak bu farklılıktan dolayı 
iki farklı yöntemimiz var. Eğer program esnasında boyutları bildirilmiş değişmez bir değer kullanıyorsak stack, 
değişebilir bir değer kullanıyorsak heap sizin için uygun olacaktır. Stack ve heap kullanımları farklı ve dikkat
edilmesi gereken bir konudur. Stack kullanılır ve işi bittikten sonra kendini otomatik olarak bellekten yok eder.
Fakat heap‘te bu işi siz yapmalısınız. Kısacası Hız gerekli olduğunda Stack, bellek gerekli odluğunda Heap kullanılır.
                
Stack:
1. Bilgisayarda RAM’de tutulur.
2. Ulaşılması heap‘e göre oldukça hızlıdır.
3. Derleme zamanında oluşturulur.
4. Kullanacağınız yerin boyutunu tam olarak biliyorsanız Stack‘i kullanmak sizin için uygun olacaktır.
5. Değer tipli değişenler belleğin stack alanını kullanır.
6. Stack de veriler FIFO mantığında dizilir.
7. Stack de veriler artan ya da azalan adres mantığında saklanır.
8. Stack de ki veri hemen silinebilir.

Heap:
1. Bilgisayarda RAM’de tutulur.
2. Stack ile karşılaştırıldığında oldukça yavaştır.
3. Değişkenler pointer ile kullanılır.
4. Çalışma zamanında oluşturulur.
5. İhtiyacınız olan boyutu tam olarak bilmiyorsanız Heap kullanımı sizin için biçilmiş kaftandır.
6. Referans tipli değişkenler belleğin heap alanını kullanır.
7. Heap de veriler karışık adres olarak saklanır.
8. Heap de ki veri silinebilmesi için Garbage Collector (Çöp Toplayıcı) algoritmasını kullanmak gerekir.

**Not:** Buna bağlı olarak stack de oluşturulan bir değişkene değer atıldığında ve sonradan aynı değer stack de 
bulunan farklı bir değişkene atıldığında dinamik olarak oluşamayacağı için birbirinden habersiz iki farklı değişken 
mantığında çalışır. Fakat heap alanında ise bir nesne oluşturulduğunda ve daha sonradan aynı değere sahip farklı bir 
nesne oluşturulduğunda heap alanında zaten böyle bir nesne bende var, bir daha oluşturmayacağım senin tipini bu 
nesneye referans ediyorum mantığında çalışır.

**Video:** <a href="https://www.youtube.com/watch?v=xtl6lynnj4Q"> Stack, Heap, Değer Tipleri ve Referans Tipleri </a>

## İlkel Tipler (Primitive Type) Nedir?
Primitive tipler, en ilkel tiplerdir. Bu tipler mevcutta vardır ve bu tipler ile yeni tipler oluşturulur. Örnek olarak "byte" bir primitive
tiptir. "Decimal" ise bir primitive tip değildir. Çünkü "decimal veri tipi ""byte" veri tipinden oluşturulmuştur. Bununla birlikte
değer tipleri, primitive tipleri kapsar diyebiliriz. Aşağıdaki kod örneğinde bir tipin primitive olup olmadığını öğrenebilirsiniz.

```cs
Console.WriteLine(typeof(int).IsPrimitive); // True
Console.WriteLine(typeof(decimal).IsPrimitive); // False
```

## Veri Tipleri Ve Değerleri
Aşağıda bazı C# veri tipleri (C# data types) gözükmektedir.

* byte : Uzunluğu 1 byte’tır, 0 ile 255 arasında değer alır.
* sbyte : Uzunluğu 1 byte’tır, -128 ile 127 arasında değer alır.
* short : Uzunluğu 2 byte’tır, -32768 ile 32767 arasında değer alır.
* ushort : Uzunlupu 2 byte’tır, 0 ile 65535 arasında değer alır. (UNSIGNED SHORT)
* int : Uzunluğu 4 byte’tır, -2.147.483.648 ile 2.147.483.648 arasında değer alır.
* uint : Uzunluğu 4 byte’tır, 0 ile 4.294.967.295 arasında değer alır. (UNSIGNED INT)
* long : Uzunluğu 8 byte’tır, -10^20 ile 10^20 arasında değer alır.
* ulong : Uzunluğu 8 byte’tır, 0 ile 2 x 10^20 arasında değer alır. (UNSIGNED LONG)
* float : Uzunluğu 4 byte’tır, 1.5 x 10^(-45) ile 3.4 x 10^38 arasında değer alır.
* double : Uzunluğu 8 byte’tır, 5.0 x 10^(-324) ile 1.7 x 10^308 arasında değer alır.
* decimal : Uzunluğu 12 byte’tır, ±1.0 x 10^(-28) ile ±7.9 x 10^28 arasında değer alır.
* char : Uzunluğu 2 byte’tır, Bütün unicode karakterleri kapsar.
* string : Tek bir karakter, sözcük veya cümle gibi değerlerin saklanmasında kullanılır.
* boolean : True – false değer tutan tiptir.

**Not:**  C# ta metinsel ifadeler "" ile, karakterler '' ile tutulur.
```cs
string kelime = "Alperen";
string harf = 'A';
```

**Not:** Sayısal ifadelerde bir değer varsayılan olarak int, ondalıklı sayısal ifadelerde bir 
değer varsayılan olarak double kabul edilir.
```cs
var x = 123; // x'in tipi varsayılan olarak int'tir.
```

**Not:** Bütün Ondalıklı sayılar için kullanılan tipler, tam sayıları karşılayabilirler.
```cs
int x = 100;
decimal y = 100;
```

**Not:** Ondalıklı sayılarda; float için sayının sonuna f-F ifadesi ve decimal için sayının 
sonuna m-M ifadesi getirilmelidir. Aksi taktirde derleyici derleyemez.
```cs
float x = 3.14F;
double y = 3.14; // y ile z değişkenlerinin değerleri aynıdır.
double z = 3.14D; // Double için D-d yazılabilir ama yazmaya gerekte yoktur.
decimal k =  3.14M; // k ile l değişkenlerinin değerleri aynıdır.
decimal l =  3.14m;
```

**Not:** Literal düzenleme c# 7.0 ile birlikte gemiştir. sayıların okunabilmesini kolaylaştırmak için _ kullanılabilir.
```cs
int x = 100_000_000;
```

**Not:** Tüm tiplerin default değerleri vardır. OOP'de class içinde tanımlanan değişkenlere, değişkenin tipine göre 
default değerler atanır ama main fonksiyonunda default değerler atanmaz. Main fonksiyonu içerisinde oluşturulan değişkenlerin 
ilk değerlerini manuel atmaya özen gösterilmelidir. Değeri olmayan değişkeni kullamazsınız. Aşağıda tipe göre
bazı default değerler verilmiştir:

* string: null
* char = '\0'
* sayısal ifadeler : 0
* bool: false

**Not:** default keyword'ü, içerisine verilen tipin varsayılan değerini döndürür. C# 7.0 ile syntax'ta kolaylığa gidilmiştir.
```cs
bool x = default(bool);
bool x = default; // C# 7.0 ile default değer ataması bu şekilde de yapılabilmektedir.
```

## "object" Veri Tipi
Tüm tipler varsayılan olarak object tipinden türemiştir. Object referans tiptir. Lakin değer 
türlü verileride karşılayabilir. Object olarak tanımlanan değişken her tipteki veriyi içinde saklayablir. Fakat 
object tipteki değişkene atanan değer Boxing(Kutulama) işlemine uğrar. Yani,object tipiyle oluşturduğumuz bir string 
değişken, RAM’e string olarak değilde object olarak kaydedilir. Tanımlanan object değişkeni kullanmak istediğimiz de,
içinde saklanan verinin tipini elde ederek kullanmalıyız. Bunun içinde Unboxing(Kutudan Çıkarma) 
işlemi yapılır. Bu işlem sonucunda object içindeki verinin asıl tipini veri ile birlikte almış oluruz.
                
**Not:** "object" veri tipi olan bir değişkene hangi değer girilirse girilsin, o değişken bellekte 
object tipinde tutulur ve veriye ulaşmak için boxing ve unboxing işlemleri uygulanır.
```cs
object x = 15; 
int y = (int)x;
```

## Boxing ve Unboxing Nedir?
Aslında boxing ve unboxing, tip dönüşümlerinin konusudur. Ama yukarıda değinildiği için burada anlatılmıştır.
Boxing: Object türündeki bir değişkene herhangi bir türdeki değeri göndermek Boxing olarak nitelendirilmektedir.

Unboxing: Boxing işleminin tersidir. Object bir değişkenin içerisindeki değer üzerinde türüne özgü işlemler yapabilmek için o object'in
içerisinde değeri kendi türünde elde etmememiz gerekmektedir. İşte bu işleme Unboxing denir ve cast operatörü kullanılarak
Unboxing işlemi uygulanır.

**Not:** Boxing ve Unboxing işleminde Cast operatörü kullanılmaktadır. Cast operatörü, Operatörler konu başlığının altında
daha detaylı anlatılacaktır.
```cs
object a = 13; // Boxing (İnt tipindeki değer, object tipli a değişkenine atanıyor.)
int b = (int)a; // Unboxing (a object tipli değişkenin içindeki değer, cast işlemi ile int'e dönüştürülüp, int tipli b değişkenine atanıyor.)
```

## "var" Anahtar Kelimesi
var anahtar kelimesi bir tip değildir. Tutulacak değerin türüne uygun bir değişken tanımlayabilmek için kullanılan anahtar kelimedir.
Farklı diller arasında desteklenmeyen verileri karşılayabilmek amacıyla oluşturulmuştur. "var" anahtar kelimesi kullanıldığı zaman, 
derleme zamanında değişkenin hangi tip olacağına derleyici karar verir. "var" ile tanımlanan değişkene kodun ilerleyen aşamalarında 
farklı bir tipte değer verilemez. "var" ile tanımlanan bir değişkene atanan ilk değer program derlendiği anda değişkenin veri türünü 
belirlemektedir.
```cs
//var x1 = "";
//x1 = 123;     // Hata verir. Çünkü değişenin tipi derleyici tarafından string olarak belirlenmiştir.
//var x2 = 123;    // Değişenin tipi derleyici tarafından integer olarak belirlenmiştir.
//x2 = 123;
```

## "dynamic" Veri Tipi
"dynamic" tip kullanıldığı zaman, tip dönüşümlerinde oluşan hatalar derleme esnasında kontrol 
edilmediği için hata oluşmaz. Ancak çalışma zamanında (Runtime) kontrol edilir ve hata varsa  RuntimeBinderException  
hatasını fırlatır. 'dynamic' ile, derleyici‘ye (compiler), değişkenin tipinin sadece çalışma zamanında bilinebileceğini 
söylemiş oluyoruz.
```cs
// Aşağıdaki örneği derleyebilirsiniz ancak çalışma zamanında hata verir.
// Object ile tanımlasaydık proje çalışmadan önce daha derleme zamanında bizi uyarırdı.
dynamic example = "Alperen";
int example1 = example; // Hata
```

**Not:** .GetType() metodu ile değişkenin çalışma zamanındaki tipini öğrenilebilir.
```cs
dynamic x = 100;
var y = x.GetType();
```
	
 **Not:** Runtime'da dynemic bir değişkenin tipini değiştirebilirsin.
 ```cs
dynamic x = 5;
Console.WriteLine (x.GetType());
x = "deneme";
Console.WriteLine (x.GetType());
 ```

## "const" Anahtar Kelimesi - Sabitler
Sabitler değişmeyen değerleri tutmak için oluşturulmuş yapılardır. İlk değer atamasından sonra değer atılamaz.
const, static bir yapılanmadır.
```cs
const double pi = 3.14;
```

## Readonly Anahtar Kelimesi
Readonly sadece okunabilir değişkenler için kullanılır. const'tan farkı sadece tanımlandığı yerde değil, 
ayrıca constructor method (ileride class konusunda anlatılacaktır) içerisinde de değerleri atanabilir. 
Readonly static yapıda değildir.

## Scope Kavramı
Değişken ve fonksiyonların erişebilirlik sınırlarını belirleyen alandır. {} ile ifade edilir. Aynı isimli değişkenleri 
farklı scoplarda tanımlayabilirsin. Bir değişken sadece tanımlandığı scope içerisinden erişilebilir ve kullanılabilir. 
Custom scope {} ile oluşturulabilir.
```cs
{
... 
   {
   ...
      {
      ...
      }
   }
}
```

## Enum Veri Tipi
Sayıların anlamlı şekilde isimlendirilerek kullanılabilmesini sağlayan yapılara Enum denir.
Enum sayısal değerler tutan bir yapıdır.  Varsayılan olarak enum içerisindeki elemanlar 0 dan başlar. 
İsterseniz numaralandırmayı kendinde yapabilirsin.
```cs
class Program
    {
        enum Gunler { Pazartesi, Salı, Carsamba, Persembe, Cuma, Cumartesi, Pazar };
        enum GecmeDurumu { Basarisiz = 0, Gecer = 45, Orta = 60, Iyi = 70, Pekiyi = 80 };
        static void Main(string[] args)
        {
            // ÖRNEK 1
            int deger = 1;
            Gunler secilenGun = (Gunler)deger;

            if (secilenGun == Gunler.Cumartesi || secilenGun == Gunler.Pazar)
            {
                Console.WriteLine("Hafta sonu seçtiniz.");
            }
            else
            {
                Console.WriteLine("Hafta içi seçtiniz.");
            }
            Console.WriteLine("-----------------------------------------------");
            // ÖRNEK 2
            int alinanNot = 70;
            GecmeDurumu gd = (GecmeDurumu)alinanNot;
            Console.WriteLine( "Geçme durumu: " + gd.ToString() );
        }
    }
```
## Tuple Veri Yapısı
"Tuple" aynı veya farklı tipte birden fazla değişkeni içerebilen bir veri yapısıdır. Aslında bu tanıma 
baktığımızda bize “class” tanımını çağrıştırıyor gibi görünebilir. "Tuple" veri yapısı sayesinde yeni bir
"class" yaratmadan da birden fazla farklı tipteki değişkeni aynı veri yapısı içerisinde tutabiliyoruz.
```cs
Tuple<string, string , int> result = Tuple.Create("Alperen", "Bektaşoğlu", 26);
Console.WriteLine( result.Item1 );
Console.WriteLine( result.Item2 );
Console.WriteLine( result.Item3 );
var (firstName, lastName, age) = result;
Console.WriteLine(firstName);
Console.WriteLine(lastName);
Console.WriteLine(age);
```




           
            










               
