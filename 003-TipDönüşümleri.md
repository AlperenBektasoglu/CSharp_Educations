## C# Tip Dönüşümü (Type Conversion)
Bazı durumlarda tanımladığımız değişkenleri başka bir tipe dönüştürmek isteyebiliriz.
Tip dönüşümleri iki tipe ayrılır: 

1- Bilinçsiz Tip Dönüşümü (Implicit Type Conversion)

2- Bilinçli Tip Dönüşümü (Explicit Type Conversion)

## Bilinçsiz Tip Dönüşümü (Implicit Type Conversion))
C#’ta düşük kapasiteli bir değişken daha yüksek kapasiteli bir değişkene atanabilir.
Buna bilinçsiz tip dönüşümü denir, bunun için herhangi bir özel kod gerekmez.
```cs
byte x1 = 5;
int X2 = x1;
```
## Bilinçli Tip Dönüşümü (Explicit Type Conversion)
C#’ta büyük kapasiteli bir değişken daha düşük kapasiteli bir değişkene atanabilir.
Buna bilinçli tip dönüşümü denir. Bilinçli tip dönüşümünde veri kaybı olabilir.
Bu işlemi gerçekleştirmek için Cast operatörü kullanılır.
```cs
int y1 = 125;
// byte y2 = y1; // Hata alınır.
byte y2 = (byte)y1; // Cast işlemi ile int tipinideki y1 değişkeninin değeri byte tipine dönüştürülerek y2 değişkenine atandı.
```

 ## Checked/Unchecked Kullanımı
Checked : Tip dönüşümü yaparken, veri kaybı olduğu zaman hata vermesi için kullanılır.

Unchecked : Tip dönüşümü yaparken, veri kaybı olduğu zaman hata vermesini engellemek için kullanılır. Kod akışı Default
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


            
            
        
