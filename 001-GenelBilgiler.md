# Giriş
## .Net Nedir? 
Microsoftun developerlar için geliştirdiği teknolojileri sunduğu bir çatıdır. 
.NET ile web, telefon ve Windows için uygulamalar geliştirilebilir.
.NET Framework bir omurgadır ve bu omurga içerisinde olabildiğince geniş bir kütüphane 
ve birbirleriyle birlikte çalışabilen bir grup programlama dili yer almaktadır. 
.NET Framework 60'tan fazla programlama dilini destekler. Bununla birlikte .Net Framework, 
bellek yönetimi, ağ oluşturma, güvenlik, bellek yönetimi ve tür güvenliği gibi çeşitli hizmetler sunar.

.NET'in yapısının temel olarak 2 bileşenden oluşur.

1- CLR (Common Language Runtime) -> Ortak Dil Çalışma Zamanı

2- FCL (Framework Class Library) -> Omurga Sınıf Kütüphanesi

### 1- Common Language Runtime (CLR, Ortak Dil Çalışma Zamanı)
.Net Framework’ün altında yatan temel yapı taşıdır. .Net dillerinin derlenmesiyle oluşan ara bir dil olan 
Common Intermediate Language (CIL, MSIL ya da kısaca IL. Ortak Ara Dil) Common Language Runtime tarafından 
çalışma-zamanında yorumlanarak işletim sistemlerinin anlayabileceği dil’e (örneğin; assembly) 
dönüştürülür. IL kodlarının çalışma-zamanındaki bu dönüşüm/derleme işine 
just-in-time (JIT) compile (gerektiğinde/zamanında derleme) adı verilmektedir.

Özet bir tanım yapmak gerekirse; geliştirdiğiniz uygulamanın bilgisayarın anlayabileceği bir hale dönüştürülmesidir 
diyebiliriz. Normalde Windows, Linux, MAC OS, Pardus gibi işletim sistemleri aynı program kodunu çalıştıramazlar. 
Her bir işletim sistemi için ayrı ayrı yazılıp derlenmesi gerekir. Bunun çözümü ise ortak bir ara dil kullanmak 
ve her bir platform için bu ara dile çevrilmiş program kodunu çalıştırabilecek bir altyapı hazırlamaktır. Bu görevi CLR üstlenir.

**Not:** CLR ile çalışan koda yönetilen kod, CLR'nin dışındaki koda ise yönetilmeyen kod adı verilir. 
CLR ayrıca hem yönetilen hem de yönetilmeyen kodların birlikte çalışmasına izin veren bir birlikte çalışabilirlik katmanı sağlar.

### 2- Framework Class Library (FCL, Omurga Sınıf Kütüphanesi) 
FCL (Framework Class Library), .NET ile uygulama geliştirirken kullanacağımız komutlar ve metotları bulunduran 
geniş içerikli bir kütüphanedir.

**Not:** Base Class Library (Temel Sınıf Kütüphanesi) tüm .Net dillerince kullanılabilen ve dosya okuma/yazmadan, 
grafik oluşturmaya, veritabanı etkileşimlerine kadar pek çok farklı noktada yazılım geliştiricilere destek sunan 
oldukça geniş bir kütüphanedir. Base Class Library çoğunlukla Framework Class Library ile karıştırılmaktadır. 
Aslında FCL, BCL’i de kapsayan ve içerisinde Microsoft ile başlayan namespace’lerin de bulunduğu bir süper settir.

## CLI nedir?
Farklı programlama dilleriyle yazılan programların yeniden düzenlenmeksizin değişik ortamlarda çalışması için bazı 
temel şartlara uymaları gerekmektedir. Microsoft,HP ve İntel ortaklıgı tarafından belirlenmiş bu standartlar,bilgi 
teknolojileri standartları konusunda uzman olan "ECMA"kurumunun imzasıyla yayınlanmıştır. .NET ortamı üzerinde 
çalışacak dillerin standartları,ECMA tarafından, Ortak dil yapısı - CLI ( Common Language Infrastructure)olarak belgelenmiştir.

CLI Şunları amaçlar ;
* Standart dil tanımlamaları (Common Language Specification - CLS )

* Dillerin desteklediği ortak veri türü yapısı (Common Type System - CTS)

* Bileşen yapısının nasıl destekleneceği (Component Structure)

* İstisnai durumların nasıl yöneticileği

## .Net CLI nedir?
.Net CLI (Command Line Interface) .Net komut satırı arayüzüdür. .Net CLI, .Net SDK ile birlikte gelir. 
VS kurulduğunda SDK da kurulduğu için .Net CLI da kurulmuş olacaktır. .NET CLI, farklı programlarda 
.NET uygulamaları geliştirmeye, oluşturmaya, çalıştırmaya ve yayımlamaya yönelik işlemler yapabilmemizi 
sağlayan komut satırı arabirimidir. .NET CLI ile farklı IDE'lerde .NET uygulamaları geliştirebilir veya 
çalıştırabilirsiniz.

**Not:** Visual Studio indirdiğinde Developer Command Prompt uygulamasıda iner. Developer Command Prompt 
geliştirme komutlarımızı yazabileceğimiz bir komut satırı arayüzüdür.

## ‘Yönetilen kod’ ve ‘yönetilmeyen kod” Nedir?
.NET çerçevesinde yazılan herhangi bir dil, yönetilen koddur. Yönetilen kod; belleği yöneten, güvenliği 
yöneten, diller arası hata ayıklamaya izin veren CLR'yi kullanır.

.NET çerçevesi dışında geliştirilen kod, yönetilmeyen kod olarak bilinir. CLR'nin kontrolü altında 
çalışmayan kodların yönetilmeyen kod olduğu söylenir. Yönetilmeyen kod , makine koduna göre derlenir 
ve bu nedenle doğrudan işletim sistemi tarafından yürütülür. Bundan dolayı, yönetilen kodun yapamadığı 
zararlı-güçlü şeyleri yapma becerisine sahiptir.

## .Net Framework Modülleri
Aşağıda .Net Framework modüllerinden bazıları tanımlanmıştır. Aşağıdaki .Net Framework modüllerinin de 
dışında modüller vardır(Entity Framework, LINQ vs). 

### ASP.NET Nedir?
ASP.NET, Microsoft tarafından tasarlanmış ve geliştirilmiş bir web çerçevesidir. ASP.NET, dinamik web sayfaları oluşturmak 
için kullanılan .NET Framework’ün bir parçasıdır. 

### ADO.NET Nedir? 
ADO.NET, uygulama ve veri kaynakları arasında bağlantı kurmak için kullanılan bir .Net Framework modülüdür. 

### Windows Presentation Foundation (WPF)
Windows Presentation Foundation (WPF), görsel olarak etkileyici kullanıcı deneyimleriyle Windows için 
masaüstü uygulamaları oluşturan bir User Interface (UI) frameworküdür. WPF, .Net Framework modülüdür.

### Windows Communication Foundation (WCF) 
Windows Communication Foundation, servis-yönelimli mimariyi temel alarak dağıtık uygulamalar geliştirmek için kullanılan, 
dağıtık mimari modelleri ve teknolojilerini tek çatı altında birleştiren ve içerisinde bir çok hazır bileşen barındıran 
bir frameworktür. WCF, .Net Framework modülüdür.

## .NET Core Nedir?
.NET Core, .NET Framework’ün açık kaynak kodlu, platform bağımsız bir yapıya dönüştürülmüş halidir. 
Açık kaynak kodlu olması sebebiyle GitHub üzerinde oldukça geniş bir topluluk da geliştirmesine katkı sağlamaktadır.

## .Net Framework ile .Net Core arasındaki farklar nedir?
Net Framework:

-> Açık kaynak değil.

-> Sadece windows ekosistemini destekler.

-> Önce geliştirildi.	

.Net Core: 					

-> Açık kaynaktır.

-> Bir çok ekosistemi destekler.(windows,linux,mac...)

-> Sonra geliştirildi.

## C# Nedir?
Microsoft tarafından .Net çatısı altında geliştirilen, modern programlama dilidir. C# orta seviyeli bir programlama dilidir.
C# küçük-büyük harfe duyarlı(Case Sensetive) ve tip güvenliği olan bir dildir.

**Not:** Bir programlama dili makine diline yakın ise düşük seviyeli, makine dilinden uzak ve insan diline yakın ise
yüksek seviyelidir.

## Compiler(Derleme) / Interpreter (Yorumlayıcılar)

### Compiler(Derleme) Nedir?
Derleyici, yüksek seviye bir programlama dilinde (high-level programming language) yazılmış bir kaynak kodun, başka bir hedef dile 
veya bilgisayarın/işlemcinin anlayabileceği makine diline tercümesini yapan bir programdır. C# derlenen bir dildir. Yazılan kodların
derlenmesi ile program çalıştırılabilir hale getirilir. (.exe , .dll uzantılı dosyalar derlenme sonucu oluşan dosyalardır.)

### Interpreter (Yorumlayıcılar) Nedir?
Kodu satır satır veya bloklar halinde çalıştırıp sırası gelmeyen satırları hiç çalıştırmayan bu satırlardaki hataları hiçbir zaman 
göremeyen ve kodun bütününe ait iyileştirmeleri yapamayan çeviricilere de yorumlayıcı (interpreter) adı verilmektedir. Hem derleyiciyi hem de
yorumlayıcıyı birlikte kullanan diller mevcuttur. Java buna örnek olarak verilebilir.

**Not:** Genel kanının tersine bir dilin derleyici veya yorumlayıcı özelliği yoktur. Yani C# dili için sadece derleyicisi bulunan bir dildir 
demek yanlış olur. Bu durum bütün diller için geçerlidir. Her dil için bir derleyici veya yorumlayıcı tasarlanabilir.

## Build, Rebuild ve Clean Kavramları Nedir?
Build: Derleme yapar.

Rebuild: Önceden derlenmiş dosyaları siler ve tekrar derler.

Clean: Önceden derlenmiş dosyaları siler.

**Not:** Derleme işlemi sonucunda oluşan dosyalar bin klasörü içinde oluşturulur.

## Paket/kütüphane ve Referans arasındaki fark Nedir?
Paketler/kütüphane, Nuget denilen bir havuzdan gelir. Referanslar ise önceden yazılmış dll dosyalarıdır.
Elinde fiziksel olarak bir dll dosyası var ise ve bunu projeye eklemen gerekiyor ise referans olarak eklersin.
Nuget dediğimiz havuzdan veri çekeceksen eğer o çektiğin veriyi paket olarak eklersin.

**Not:** Yazılımın çıktısını kullanacak taraf başka bir yazılımsa, kullanılacak yazılım dll uzantılıdır.

**Not:** Yazılımın çıktısını kullanacak taraf son kullanıcı ise, kullanılacak yazılım exe uzantılıdır.

**Not:** .cs uzantılı dosya c# dosyasıdır.

## Proje ve Solition Kavramları Nedir?
Proje: İçerisinde amaca dair kodsal çalışmaların yapıldığı bir bütündür.

Solition: İçerisinde bir veya birden fazla proje barındırabilien bir evrensel kümedir.
    
**Not:** Derleme proje bazlı yada solition bazlı yapılabilir.

## Main Fonsiyonu Nedir?
Uygulama ile işletim sistemi arasındaki iletişimi sağlayan foksiyondur. Uygulama çalıştığında main fonksiyonu içindeki kodlar yürütülür.
Her uygulamada, main fonksiyonu sadece 1 tane olmak zorundadır. CLI komutlarında run komutu ile main fonksiyona parametre geçilebilir.

```cs
dotnet run Alperen Bektaşoğlu  // (1.parametre: Alperen, 2.parametre: Bektaşoğlu)
```

**Video:** <a href="https://www.youtube.com/watch?v=slhmM7TF2R0&list=PLQVXoXFVVtp3e_urGZcMNAHx2Eo4Rm5Xk&index=28"> Main Fonsiyonu </a>

## Top-Level Statements (C# 9.0) Özelliği Nedir?
Yazılımcıların, Main foksiyonunun basmakalıp kodlarından sıyrılmasını sağlayan bir özelliktir.
Top-Level Statements özelliği C# 9.0 ile birlikte gelmiştir.
Bu özellik sadece Program.cs dosyasındaki main fonksiyonu için uygulanabilir.
Derleyici kodların main fonksiyonu içerisine yazılan kod olduğunu dosyanın isminden anlar.
Detaylı bilgi için aşağıdaki video'yu inceleyebilirsiniz.

**Video:** <a href="https://www.youtube.com/watch?v=23AaVL_mTBg&list=PLQVXoXFVVtp3e_urGZcMNAHx2Eo4Rm5Xk&index=29"> Top-Level Statements (C# 9.0) Özelliği </a>

 ## Debug İle Ve Debug Olmadan Proje Nasıl Ayağa kaldırılır?
 Debugsız modda çalıştırma, uygulamanın ayağa kalkma maliyetini düşürerek, uygulamanın daha hızlı ayağa kalkmasını sağlar.
 
 Debug modda çalıştırma: F5 
  
 Debugsız modda çalıştırma: Ctrl + F5

 ## Yorum Satırları Nedir?
Yorumlar, programa etki etmeyen ancak kendimizin veya kodu inceleyen bir başkasının nerede ne yapıldığını 
anlamasını sağlayacak yazılardır. Yorumlar tek satırlık yorumlar ve çok satırlık yorumlar olmak üzere ikiye ayrılır:

1- Tek satır için kullanılan açıklama satırı sembolü: //

```cs
// ...
```

2- Birden fazla satır için kullanılan açıklama satırı sembolü: /* */

```cs
/*
    ...
    ...
    ...
*/
```

## Region Nedir?
Kod dosyasını kategorik hale getirmemizi sağlayan bir ön işlemci komutudur.

```cs
#region RegionName
...
...
...
endregion
```

## Todo Nedir?
Önemli olan yorumları ve başka bir yazılımcının onca dosya arasından hızlıca bulması gereken yorumları todo komutu ile 
task liste aktarabiliriz. VS'da Task List ekranını açmak için gerekli yol: View -> Task List

```cs
//todo ÖnemliYorum
```

## Watch Penceresi Nedir?
Debug modda değişkenlerin değerlerini kolayca görmemizi sağlar. Bir değişkeni Watch penceresine eklemek için debug 
moddayken çalıştırıp değişkenin üzerine sağ tıklayarak add watch butonuna basmanız yeterlidir.
