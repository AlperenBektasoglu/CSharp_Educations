# Class(Sınıf) Yapısı 
Nesne(object) ‘ler sınıfların birer örneğidirler. Bu durumda sınıf, nesnelerin 
nasıl inşa edileceğini tanımlayan bir kılavuzdur diyebiliriz. Sınıf soyut bir ifadedir, 
nesneler oluşuncaya kadar fiziksel olarak bellekte yer almazlar.

Class yapısının özellikleri: 
* Sınıflarda erişim belirleyicisi yazılır. Yazılmamış ise varsayılan olarak Internal'dır.
* Sınıf üyeleri için erişim belirleyicisi belirtilmediğinde varsayılan olarak Private olur.
* Sınıflar içerilerinde metod, property veya field barındabilirler.

## Field,Metod,Property Tanımı
* Field : Bir class yada struct içinde tanımlanan her tipten değişkendir.
* Metod : Bir class yada struct içinde tanımlanan fonksiyonlardır.
* Property :  Oluşturulan private field 'lara kontrollü bir şekilde erişim sağlanmak için 
              Property tanımlanmaktadır. Property tanımı ile bu alanları get edebilir, set edebilir 
              ya da her ikiniside aynı anda kullanabilirsiniz.
                                 
**Not:** Field tanımlamadan da property oluşturulabilir. Bu durumda property aynı zamanda field gibi davranır.

**Not:** Bu üç tanım classlar içinde ileride anlatılacak struct yapılar içinde mevcuttur.
