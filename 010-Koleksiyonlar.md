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
