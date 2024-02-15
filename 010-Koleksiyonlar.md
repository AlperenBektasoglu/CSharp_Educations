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

