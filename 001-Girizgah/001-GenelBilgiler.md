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
Net Framework’ün altında yatan temel yapı taşıdır. .Net dillerinin derlenmesiyle oluşan ara bir dil olan 
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









