
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













               
