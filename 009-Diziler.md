
## Diziler (Arrays)
* Diziler, koleksiyonların temelini teşkil ederler ve koleksiyonların gelişmelerine katkıda bulunmaktadırlar.
* Diziler referans tiplidir. Özlerinde classdır.
* Dizi içine her türlü değer koyulabilir(referans/değer tip). 
* Dizi içindeki bütün elemanlar aynı tipte olmak zorundadır.
* Dizi boyutu sabittir ve kodlarken belirtilmesi gerekir.
* Bütün dizilerin birinci elemanı 0. indeksten başlar.

```cs
int[] example1; // example1 adında int tipinde bir dizi için referans tanımlaması yapıldı. (Referans tanımlaması yapıldı ama bellekte(heap) alan açılmadı!)
example1 = new int[10];  // example1 adındaki dizi için bellekte(heap) 10 tane int tipinde değer tutacak alan açıldı.

int[] example2 = new int[10]; // Yandaki şekilde de tanımlanabilirdi.

/*
Not: Yukarıdaki iki kodda da int türünden iki dizi tanımlandı ve dizinin her bir elemanına int türünün 
     varsayılan değeri atandı. Varsayılan değerler, sayısal türler için 0, object türü için NULL (yokluk),
     string türü için "", char için ' ' (boşluk) ve bool için false değerleridir.
*/

Console.WriteLine(example2[3]); // Çıktı: 0

/*
Not: Bütün dizilerin birinci elemanı 0. endeksidir. dizi isimli dizinin birinci elemanına dizi[0], 
     10. elemanına dizi[9] yazarak erişebilir ve bu dizi elemanlarını bir değişkenmiş gibi kullanabiliriz.             
*/

int[] example3 = new int[20];
example3[5] = 30; //6. Sıradaki elemana 30 değeri atanıyor.
Console.Write(example3[5]); // Çıktı: 30
```

Dizilere başlangıç değerleri de atanabilir. Atama için { } işaretçileri kullanılır.
```cs
string[] example1 = { "Bir", "İki", "Üç" };
string[] example2 = new string[] { "Bir", "İki", "Üç" };
string[] example3 = new string[3] { "Bir", "İki", "Üç" };
```

           
**Not:** Bir dizi elemanına erişirken üst dizi indeksinden daha yukarıda bir değer verilirse program hata verir.
Örneğin yukarıdaki dizi de "example3[4] = 100;" ifadesi yazıldığında program taşma hatası verir.
              
**Not:** Bir dizinin boyutu sabit olabileceği gibi değişkende olabilir. Ancak önemli olan 
bir dizinin boyutu girildikten sonra dizi boyutu tekrar değiştirilemez.
             
**Not:** Dikkat edilmesi gereken bir nokta şudur ki, new operatörü ile türetilmeyen dizilere erişilemez.
```cs
int[] example1 = new int[10];  // example1 dizisine ulaşılabilir.
int[] example2; // example2 dizisine ulaşılamaz.
```    
**Not:** Foreach mekanizması sadece dizi elemanlarını okuma için kullanılır. Dizi elemanları üzerinde düzenleme 
 işlemlerine izin verilmez. Bu tür engelleme ReadOnly (Sadece okunabilir) olarak bilir.
             
**Not:** Yukarıdaki anlatımda tek boyutlu dizi örnekleri verildi. Tabi çok boyutlu diziler de var. Çok boyutlu diziler, 
Multi-Dimensional Array (Düzenli Diziler / Matris Dizileri) ve Jagged Array (Düzensiz Diziler) olmak üzere ikiye ayrılır.

**Not:** Multi-Dimensional Array (Düzenli Diziler / Matris Dizileri): Bütün satırların aynı kolon sayısına sahip 
olduğu dizilerdir.

**Not:** Jagged Array (Düzensiz Diziler): Jagged diziler, her satırının kolon sayısı farklı olan (Aynıda olabilir) dizilerdir diyebiliriz.













        
            /*

             */
