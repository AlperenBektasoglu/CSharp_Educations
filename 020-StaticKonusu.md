
# Static Konusu
## Static Elemanlar
* Bir sınıf içerisindeki metotlar, alanlar(field), özellikler (property) static olarak tanımlanabilir.
* Bir class'ta static üye için bellekte sabit bir yer açılır.
* Bir sınıf içerisindeki static olmayan üyelere o sınıftan oluşturduğumuz nesneler üzerinden erişiriz.
* Static olan üyelere ise nesne oluşturmadan, sınıf ismi ile erişiriz.
* Static olmayan üyeler static üyelere erişebilir ama static üyeler sadece static üyelere erişebilir.
* Sınıflarda static olarak tanımlanabilir.

**Not:** Static olmayan elemanlar nesneye özgü bilgileri tutarken static olan elemanlar uygulama çalıştığı sürece 
kendilerine en son atanan değeri tutarlar.

## Static Sınıflar
* Oluşturduğumuz sınıf içerisinde sadece static üyeler bulunuyorsa, sınıfı static olarak tanımlayabiliriz. 
* Sınıfların static olarak tanımlanması bir zorunluluk değildir, sadece okunabilirliği arttıran bir yaklaşımdır. Sınıfının static olduğunu gören bir programcı,
sınıf içerisinde sadece static elemanların bulunduğunu anlayacaktır.
* Static sınıflardan nesne oluşturulamaz. (new Matematik(); YANLIŞ)
* Static sınıf türünden referanslar oluşturulamaz. (Matematik m; YANLIŞ)
* Static sınıfların içinde static olmayan üyeler tanımlanamaz.
* Static sınıflarda kalıtım yoktur.
