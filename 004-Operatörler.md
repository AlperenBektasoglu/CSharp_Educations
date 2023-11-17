## C#’da İşlem Önceliği
C#’da işlem önceliği aynen matematikte olduğu gibidir. Öncelikle parantez içi işlemler yapılır, 
daha sonra parantez dışına çıkılır. Aritmetiksel olarak da çarpma (*), bölme (/) ve mod alma (%) kendi 
içlerinde aynı önceliğe sahipken daha sonra toplama (+) ve çıkarma (-) gelir. Toplama ve çıkarma da kendi 
içinde aynı önceliğe sahiptir. Aynı önceliğe sahip ifadelerde işlemler soldan sağa doğru yapılır.

##  Aritmetik Operatörler
Aritmetik operatörler: + , ‐ , * , / , % 

## Karşılaştırma Operatörleri
Karşılaştırma operatörleri: < , > , <= , >= , == , !=

## Bitsel Operatörler
Bitsel operatörler: &(bitsel ve), ~(bitsel değil), | (bitsel veya), ^(bitsel özel veya)

## Mantıksal operatörler
Mantıksal operatörler: &&(ve), !(değil), ||(veya), ^(yada)

**Not:** ^ operatörünün || operatöründen tek farkı:
* true || true -> true
* true ^ true -> false
                
**Not:** Bitwise ve Mantıksal operatörler arasındaki temel fark; Bitsel işleçler bitler üzerinde çalışır ve bit-bit işlemleri 
gerçekleştirirken, mantıksal işleçler birden çok koşula dayalı bir karar vermek için kullanılır.

**Not:** farklı tipler arasında işlem olduğunda sonuç büyük olan tipte döner.

**Not:** Normalde iki aynı tipteki sayisal değer üzerinde yapılan işlem neticesinde sonuc aynı tipte dönecekken,
bu iki değer byte ise sonuc her daim int dönecektir.

## Arttırma Azaltma Operatörleri
* Artırma Operatörü: ++ (1 artırır.)
* Azaltma Operatörü: -- (1 azaltır.)

**Not:** i++ ile ++i arasında fark vardır.
* i++ -> önce değeri döndür sonra 1 artır anlamına gelir.
* ++i -> önce değeri 1 artır ardından değeri dön anlamına gelir.

```cs
int x = 10;
Console.WriteLine(i++); // Çıktı: 10, x: 11 
Console.WriteLine(++i); // Çıktı: 12, x: 12
```
## Atama Operatörleri
Atama operatörleri: = , += , -= , *= , /=

## Ternary Operatörü (?:)
Koşul işlemlerinde kullanılır. İf yapısı ile aynı işlemi yapar.
If kullanarak kontrol etmek istediğimiz koşullarda ternary operatorünü kullanarak kod satır sayısından avantaj sağlamış oluruz.

koşul ? true : false;
```cs
var money = 40;
var canBuy = 
    (money < 30) ? "Satın alamazsın.":
    (money >= 30) ? "Satın alabilirsin.":
    "Para miktarını girmen gerekmektedir.";
```

## Member Access Operatörü (.)
Elimizdeki değerin türüne uygun fonsiyonları, metodları ve property'lere erişmemizi ve onları kullanabilmemizi sağlayan operatördür.


