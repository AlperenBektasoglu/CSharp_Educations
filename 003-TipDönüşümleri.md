# C# Tip Dönüşümü (Type Conversion)

Bazı durumlarda tanımladığımız değişkenleri başka bir tipe dönüştürmek isteyebiliriz.
Tip dönüşümleri iki tipe ayrılır:

1. Bilinçsiz Tip Dönüşümü (Implicit Type Conversion)
1. Bilinçli Tip Dönüşümü (Explicit Type Conversion)

## Bilinçsiz Tip Dönüşümü (Implicit Type Conversion)

C#'ta düşük kapasiteli bir değişken daha yüksek kapasiteli bir değişkene atanabilir. Buna bilinçsiz tip dönüşümü denir, bunun için herhangi bir özel kod gerekmez.

```cs
byte x1 = 5;
int x2 = x1;
```

## Bilinçli Tip Dönüşümü (Explicit Type Conversion)

C#'ta büyük kapasiteli bir değişken daha düşük kapasiteli bir değişkene atanabilir. Buna bilinçli tip dönüşümü denir. Bilinçli tip dönüşümünde veri kaybı olabilir. Bu işlemi gerçekleştirmek için Cast operatörü kullanılır.

```cs
int y1 = 125;
// byte y2 = y1; // Hata alınır.
byte y2 = (byte)y1; // Cast işlemi ile int tipinideki y1 değişkeninin değeri byte tipine dönüştürülerek y2 değişkenine atandı.
```

**Not:** Tip dönüşümünde int tipini bool tipine dönüştürürken; 0 false olarak, 0 dışındaki değerler ki bunlara negatif sayılarda dahil true olarak dönüşür.

**Not:** ASCII: Bilgisayardaki her bir karakterin sayısal bir karşılığı vardır. Bu sayısal değerlere ASCII kaynak kodu denmektedir. char tipinden int tipine dönüşüm yaparken ilgili karakterin ASCII karşılığını elde edersin.

## Checked/Unchecked Kullanımı

Checked: Tip dönüşümü yaparken, veri kaybı olduğu zaman hata vermesi için kullanılır.

Unchecked: Tip dönüşümü yaparken, veri kaybı olduğu zaman hata vermesini engellemek için kullanılır. Kod akışı Default
olarak Unchecked gibi davranır.

```cs
checked
{
    int i = 125;
    byte k;
    k = (byte)i;
}

unchecked
{
    int z = 900;
    byte l;
    l = (byte)z;
}
```

## Tip Dönüşümünde Kullanılan Metodlar

### Convert Sınıfı

Convert sınıfı bütün tipleri hedef tipe dönüştürebilir.

```cs
string x = "123";
int y;
y = Convert.ToInt32(x);
```

### Parse Metodu

Parse metodu sadece string tipleri hedef tipe dönüştürürken kullanılır.

```cs
int k;
string l = "123";
k = int.Parse(l);
```

### ToString() Metodu

Tipleri string tipine dönüştürmek için kullanılır. ToString() metodu tüm tiplerde tanımlıdır.

```cs
int c = 100;
string p;
p = c.ToString();
```

**Not:** Tip dönüşümlerinde dikkat edilmesi gereken tek bir husus vardır. Dönüşüm yapılacak verinin tipine uygun bir hedef tip belirlenmelidir.
