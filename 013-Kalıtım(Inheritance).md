# Kalıtım (Inheritance)
C# Kalıtım, nesne yönelimli programlamanın en önemli özelliklerinden birisidir. Kalıtım sayesinde sınıf yapılarımız 
birbirinden türetilebilir. Yani bir sınıftan yeni bir sınıf oluşturma işlemine kalıtım denir. Bir sınıf herhangi 
bir üst sınıftan türetildiği zaman, türemiş olduğu sınıfın içerisindeki public ve protected erişim belirleyicilerine sahip
bütün üyelere sahip olur. Bir sınıf sadece tek bir sınıftan kalıtım alabilir. Kalıtımsal tüm ilişkiler : operatörü tarafından yapılmaktadır.

**Not:** C# programlama dilinde kalıtım sınıflara özel bir niteliktir. Record'lar da sınıf olduğundan kalıtım alabilmektedirler.
Lakin bir sınıf bir sınıftan, bir record ise bir recordan kalıtım alabilir.

**Not:** Mevcutta olan yada senin yeni oluşturduğun bütün sınıflar Object sınıfından miras almaktadır.

### Base Class ve Derived Class Nedir?
* Kalıtım veren sınıfa Base / Parent Class denir.
* Kalıtım alan sınıfa Derived / Child Class denir.
* Peki, atalar bütün torunlarının Base Class'ı mıdır? Hayır değildir.
A class -> B class -> C class kalıtım versin. Bu durumda C nin base classı B classıdır. B classının da base classı A classıdır.



