## Koleksiyonlar
Programlamadaki temel ihtiyaçlarımızın biri de verilerimizin toplu olarak tutulduğu yapılardır. Bu ihtiyaçlarımızı genellikle 
diziler ya da koleksiyonlar ile gideririz. .Net Platformu programcılar tarafından sıkça kullanılan yapıları (stack, queu...)  
sisteme entegre ederek, hazır bir şekilde geliştiriciye sunmaktadır. Platform tarafından verilerimizi toplu olarak tutmamızı sağlayan
bu çözümleri Koleksiyon Sınıfları başlığı altında ele alabiliriz.

### Koleksiyonların Sağladığı Avantajlar Nedir?
1. Diziler sabit boyutludur ve eleman sayısının önceden belirtilmesi gerekir. Koleksiyonlar ise dinamik yapıdadır yani sabit boyutlu değildir.
2. Eleman eklendikçe boyutu dinamik olarak artmaktadır.
3. Diziler aynı veri tipindeki elemanları içermektedir. Koleksiyonlarda ise böyle bir kısıtlama bulunmamaktadır.

### Koleksiyonların Dezavantajları Nelerdir?
1. .Net Platformunda kullanmış olduğumuz veri tipleri, Değer tipleri ve Referans tipleri olarak ikiye ayrılmaktadır. Bir Değer Tipinin, 
Referans Tipine dönüştürülmesi işlemine Boxing, tersi bir işlemede Unboxing denmektedir. Koleksiyonlar verileri object olarak tutmaktadır. 
Bu yüzden koleksiyonlara her veri eklediğimizde Boxing işlemi gerçekleşecektir. Yani verimiz object’e dönüştürülecektir. 
Koleksiyona eklenen verileri bir değişene aktarmak istediğimizde de Unboxing işlemi gerçekleşecektir. Koleksiyonun eleman 
sayısındaki artışa bağlı olarak boxing ve unboxing işlemleri artacaktır ve buna bağlı olarak da uygulamamızın performansı düşecektir.

### Koleksiyonların Namespaceleri Nelerdir ve Bu Namespacelerin Classları Nelerdir?
1. System.Collections.Generic: List, Stack, Queue, LinkedList, HashSet, SortedSet, Dictionary, SortedDictionary, SortedList ...
2. System.Collections: ArrayList, Stack, Queue, Hashtable, BitArray, SortedList  ...
3. System.Collections.Concurrent: BlockingCollection, ConcurrentBag, ConcurrentStack, ConcurrentQueue, ConcurrentDictionary, Partitioner ...

### Koleksiyon Tipleri Nelerdir?
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

### ArrayList Kullanımı
ArrayList sınırları dinamik olarak değişebilen diziler olarak tanımlanır. 
Farklı veri tipindeki öğeleri ArrayList’e ekleyebiliriz. Eklenen her veri object tipindedir.
Dolayısı ile her veri için boxing ve unboxing işlemleri uygulanır. Dizilerden çok daha performanslı çalışır.
ArrayList’e eklenen her bir elemana indeks numarasıyla erişe bilmekteyiz. ArrayList’in başlangıç kapasitesi 4’tür. 
Mevcut kapasite yeterli gelmediğinde, arkaplanda kapasite 2 katına çıkarılmaktadır.

````cs
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


