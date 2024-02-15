# Koleksiyonlar
Programlamadaki temel ihtiyaçlarımızın biri de verilerimizin toplu olarak tutulduğu yapılardır. Bu ihtiyaçlarımızı genellikle 
diziler ya da koleksiyonlar ile gideririz. .Net Platformu programcılar tarafından sıkça kullanılan yapıları (stack, queu...)  
sisteme entegre ederek, hazır bir şekilde geliştiriciye sunmaktadır. Platform tarafından verilerimizi toplu olarak tutmamızı sağlayan
bu çözümleri Koleksiyon Sınıfları başlığı altında ele alabiliriz.

## Koleksiyonların Sağladığı Avantajlar Nedir?
1. Diziler sabit boyutludur ve eleman sayısının önceden belirtilmesi gerekir. Koleksiyonlar ise dinamik yapıdadır yani sabit boyutlu değildir.
2. Eleman eklendikçe boyutu dinamik olarak artmaktadır.
3. Diziler aynı veri tipindeki elemanları içermektedir. Koleksiyonlarda ise böyle bir kısıtlama bulunmamaktadır.

## Koleksiyonların Dezavantajları Nelerdir?
1. .Net Platformunda kullanmış olduğumuz veri tipleri, Değer tipleri ve Referans tipleri olarak ikiye ayrılmaktadır. Bir Değer Tipinin, 
Referans Tipine dönüştürülmesi işlemine Boxing, tersi bir işlemede Unboxing denmektedir. Koleksiyonlar verileri object olarak tutmaktadır. 
Bu yüzden koleksiyonlara her veri eklediğimizde Boxing işlemi gerçekleşecektir. Yani verimiz object’e dönüştürülecektir. 
Koleksiyona eklenen verileri bir değişene aktarmak istediğimizde de Unboxing işlemi gerçekleşecektir. Koleksiyonun eleman 
sayısındaki artışa bağlı olarak boxing ve unboxing işlemleri artacaktır ve buna bağlı olarak da uygulamamızın performansı düşecektir.

## Koleksiyonların Namespaceleri Nelerdir ve Bu Namespacelerin Classları Nelerdir?
1. System.Collections.Generic: List, Stack, Queue, LinkedList, HashSet, SortedSet, Dictionary, SortedDictionary, SortedList ...
2. System.Collections: ArrayList, Stack, Queue, Hashtable, BitArray, SortedList  ...
3. System.Collections.Concurrent: BlockingCollection, ConcurrentBag, ConcurrentStack, ConcurrentQueue, ConcurrentDictionary, Partitioner ...

## Koleksiyon Tipleri Nelerdir?
.Net Platformu 3 koleksiyon tipini desteklemektedir. 
1. Genel Amaçlı Koleksiyonlar: Her tipten veriyi saklamak için kullanılabilirler.
* ArrayList
* Dictionary
* HashTable
* Queue
* SortedList
* Stack

2. Özel Amaçlı Koleksiyonlar: Belirli bir veri tipi veya çalışma şekli için optimize edilmişlerdir.
* CollectionsUtil
* ListDictionary: Anahtar-Değer çiftlerini bir bağlı liste içinde saklar. Küçük veri kümeleri için tercih edilir.
* HybridDictionary: Belirli bir büyüklüğü geçene kadar Anahtar-Değer çiftlerini ListDictionary koleksiyonunda tutmaktadır, 
                    geçtikten sonra otomatik olarak bir Hashtable koleksiyonuna geçiş yapar.
* NameValueCollection: Anahtar-Değer çiftlerinin her ikisininde string tipinde olduğu durumlarda tercih edilebilir.
* StringCollection: Karakter katarlarını saklamak için optimize edilmiş bir koleksiyondur.
* StringDictionary: Anahtar-Değer çiftlerinin her ikisininde string tipinde olduğu bir hash tablodur. 
                    Anahtar-Değer çiftleri küçük harflere çevrilerek saklanır.

Aşağıda en çok kullanılan koleksiyon yapıları anlatılmıştır:

## ArrayList Kullanımı
ArrayList sınırları dinamik olarak değişebilen diziler olarak tanımlanır. 
Farklı veri tipindeki öğeleri ArrayList’e ekleyebiliriz. Eklenen her veri object tipindedir.
Dolayısı ile her veri için boxing ve unboxing işlemleri uygulanır. Dizilerden çok daha performanslı çalışır.
ArrayList’e eklenen her bir elemana indeks numarasıyla erişe bilmekteyiz. ArrayList’in başlangıç kapasitesi 4’tür. 
Mevcut kapasite yeterli gelmediğinde, arkaplanda kapasite 2 katına çıkarılmaktadır.

```cs
ArrayList liste1 = new ArrayList();
liste1.Add(5);
liste1.Add("Alperen");
liste1.Add(10);
liste1.Add(new Exception());

Console.WriteLine(liste1[1]); // 1. indisteki elemanı döndürür.

liste1.Remove("Alperen"); // Remove() metoduna parametre olarak girilen ifade koleksiyon içerisinden silinir.
liste1.Clear(); // Clear() metodu koleksiyon içerisindeki tüm öğeleri silmektedir.
int elemanSayisi = liste1.Count; // Koleksiyon içerisinde yer alan elemanların sayısını döndürmektedir.
int kapasite = liste1.Capacity; // Koleksiyonun kapasitesinin döndürmektedir.
bool varmi = liste1.Contains(456); // Koleksiyon içerisinde parametre olarak girilen öğeyi arar. Öğe bulunursa TRUE, bulanamazsa FALSE döndürür.
liste1.Sort(); // Metodu: Koleksiyon içerisindeki öğeleri artan sırada sıralamaktadır. Sıralama işlemi için öğelerin karşılaştırılabilir olması gerekmektedir.

string[] dizi = new string[20];
liste1.CopyTo(dizi, 2); // CopyTo(dizi,i) metodu, koleksiyon içerisindeki tüm öğeleri, diziye i.indeksten başlayarak kopyalayacaktır.           

// Daha fazla Metot ve Özellik için: https://www.srdrylmz.com/c-arraylist-sinifi/
```

## GenericList Kullanımı
Generic List, sınırları dinamik olarak değişebilen diziler olarak tanımlanır. 
Aynı veri tipindeki öğeleri Generic List’e ekleyebiliriz. Bu yönü ile ArrayListlerden ayrılırlar. 
ArrayList ile aynı metodlara sahiptir.
               
**Not:** Tipi kendimiz belirlediğimiz yapılara generic diyoruz. 

```cs
List<int> liste1 = new List<int>();
liste1.Add(200);
liste1.Add(100);
liste1.Add(300);
liste1.Sort();
```

## Hashtable Kullanımı
Bir koleksiyondaki elemanlara bir anahtar değer ile erişmek isteyebiliriz. Bu durumu System.Collections isim alanında bulunan Hashtable sınıfı kullanarak çözebiliriz. 
Hashtable sınıfında koleksiyonlar, bir anahtar (key) ve değer (value) ikilisi olarak saklanır. Verdiğimiz ‘Key’ değeri unique olmak ve null olmamak zorundadır. 
Bir Hashtable koleksiyonu oluşturup,  Anahtar-Değer çifti eklemek istediğimizde arkaplanda gerçekleşen işlemler;
1. Öncellikle depolama işlemi için kullanılacak bir hash tablosu oluşturulur.
2. Anahtar kullanılarak hash kod denilen benzersiz bir değer üretilir (Hashing). Bu değer anahtar ile ilişkili verilerin, hash tablosunda saklanacağı indeksi belirtecektir.
3. Anahtar ile ilişkili veriler, hash tablosunda Hash kodunun belirttiği indekse eklenir.

**Not:** Arkaplanda gerçekleşen tüm bu işlemler büyük veri kümelerini içeren koleksiyonlar da arama süresini ciddi anlamda düşürmektedir.

Hashtable Koleksiyonu Metotları ve Özellikleri: https://www.srdrylmz.com/c-dictionary-sinifi/

```cs
 Hashtable Arac = new Hashtable();
Arac.Add("41 ABC 123", "Alfa Romeo");  // Arac.Add(Anahtar(key),Değer(value));
Arac.Add("56 ABC 456", "Audi");
Arac.Add("25 ABC 789", "Mercedes-Benz");

foreach (DictionaryEntry oge in Arac) // DictionaryEntry sınıfı ile koleksiyonda ki Anahtar-Değer çiftlerine ulaşabiliriz.
    Console.WriteLine("Anahtar:{0} - Değer:{1}", oge.Key, oge.Value);

string plaka = "41 ABC 123";
string model = "Audi";
Console.WriteLine(Arac[plaka]);
bool keyVarMı = Arac.ContainsKey(plaka); // ContainsKey() metodu key değerinin koleksiyonda olup olmadığına bakar.
bool valueVarMı = Arac.ContainsValue(model); // ContainsValue() metodu value değerinin koleksiyonda olup olmadığına bakar.
Console.WriteLine("Eleman sayısı: " + Arac.Count); // Count Özelliği
Arac.Remove("56 ABC 456"); // Remove Metodu
Arac.Clear(); // Clear Metodu

// Keys Özelliği: Anahtarları (Keys) içeren bir koleksiyon döndürmektedir.
ICollection Koleksiyon_1 = Arac.Keys;

// Values Özelliği: Değerleri (Values) içeren bir koleksiyon döndürmektedir.
ICollection Koleksiyon_2 = Arac.Values;
```

## Dictionary Kullanımı
Standart dizilere eklenen elemanlar, belleğe sıralı bir şekilde yerleştirilmektedir. Sıfırdan başlanarak her bir elemana birer 
indeks değeri verilip, elemanlara o indeksler aracılığıyla erişmemiz sağlanmaktaydı. Koleksiyon sınıflarından biri olan ArrayList 
içinde aynı durum söz konusu.  ArrayList’e eklenen her bir elemana indeks numarasıyla erişe bilmekteyiz.
Dictionary koleksiyonunda ise veriler Anahtar(Key) ve Değer(Value) yapısı ile tutulur. Koleksiyon içerisinde yer alan Anahtarlar 
birbirinden farklı olmalıdır. Dictionary sınıfından bir nesne oluştururken, anahtar ve değerin veri tiplerini belirtmemiz gerekmektedir.

Dictionary Koleksiyonu Metotları ve Özellikleri: https://www.srdrylmz.com/c-dictionary-sinifi/

### Hashtable ile Dictionary Arasındaki Farklar Nelerdir?
Hashtable:
* Generic değildir.
* System.Collections namesapce'i içindedir.
* Hashtable'da, aynı türdeki veya farklı türdeki anahtar/değer çiftlerini saklayabilirsiniz.
* Hashtable'da, anahtarın ve değerin türünü belirtmeye gerek yoktur.
* Boxing ve Unboxing olayları nedeniyle veri alımı Dicitionary'ye göre daha yavaştır.
* Hashtable'da, verilen Hashtable'da bulunmayan bir anahtara erişmeye çalışırsanız, o zaman boş değerler verecektir.
* Depolanan değerlerin sırasını korumaz.

Dicitionary:
* Generictir.
* System.Collections.Generic namesapce'i içindedir.
* Dicitionary'de, aynı türden anahtar/değer çiftlerini saklayabilirsiniz.
* Dicitionary'de, anahtarın ve değerin türünü belirtmelisiniz.
* Boxing ve Unboxing olayları olmadığı için veri alımı Hashtable'dan daha hızlıdır.
* Dicitionary'de, verilen bir anahtara erişmeye çalışırsanız ve o anahtar dictionary'de yok ise, hata verecektir.
* Her zaman saklanan değerlerin sırasını korur.

```CS
Dictionary<int, string> Ogrenci = new Dictionary<int, string>();
Ogrenci.Add(134, "Tolga Demirer");
Ogrenci.Add(158, "Ümit Özkan");
Console.WriteLine(Ogrenci[158]);
```

## SortedList Kullanımı
Verileri Key Value olarak tutar. Tutulan veriler sıralı olarak saklanır. 
Her eklenen elemandan sora yeniden sıralanır. Verdiğimiz ‘Key’ değeri unique olmak ve null olmamak zorundadır.
Sıralama işlemini, Anahtar(Key) değerlerine göre yapar. Sıralamayı küçükten büyüğe yapar. SortedList generic yada
nongeneric şekilde oluşturulabilir.

SortedList Koleksiyonu Metotları ve Özellikleri:  https://www.muratoner.net/csharp/csharp-sortedlist-kullanimi-ve-ornekleri
              
**Not:** Hastable sınıfında olduğu gibi SortedList sınıfında da Anahtar-Değer çiftlerini bir DictionaryEntry yapısında tutabiliriz.

```cs
SortedList SiraliKoleksiyon_1 = new SortedList(); // Non-Generic
SortedList<int, string> SiraliKoleksiyon_2 = new SortedList<int, string>(); // Generic

SiraliKoleksiyon_1.Add(41, "Kocaeli");
SiraliKoleksiyon_1.Add(54, "Sakarya");
SiraliKoleksiyon_1.Add(25, "Erzurum");
```







