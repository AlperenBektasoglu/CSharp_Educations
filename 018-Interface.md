
## Interface (Arayüz)
Arayüzler, sınıflara rehberlik etmek üzere oluşturulan nesneye dayalı programlamanın en önemli özelliklerinden biridir. Sınıfların hangi metotları ve özellikleri içermesi gerektiği 
arayüzler içerisinde bildirilebilir. Arayüzler içerisinda sadece metotlar yada propertyler olabilir. Arayüzler içerisinde field'lar oluşturulamaz. Arayüzler içerisinde ki üye imzalarında 
erişim belirleyicisi kullanılmaz. Abstaction(sanallaştır) için sıklıkla arayüzler kullanılır.

Interfacelerin genel özelliklerini sıralayacak olursak;
1. Nesne oluşturulmaz ama referans noktası alınabilir.
2. Bir sınıf birden fazla interface implemente edebilir.
3. Interface içerisine sadece üye imzaları tanımlanabilir ve erişim tipi belirtilmez. C# 8.0 ile gelen "default interface methods" özelliği ile
arayüzler içerisinde metodların varsayılan gövdeleri oluşturulabilir.
4. Interface te name hiding problemi ile karşılaşılabilir. Name hiding'i anlamak için bu <a href="https://www.youtube.com/watch?v=863_jnRhqZ0">link</a>'ten videoyu açarak, 16:15 ten itibaren izleyebilirsiniz.

**Not:** Bir sınıf öncelikli olarak bir sınıftan miras alıyor ise ilk o miras aldığı sınıf belirtilmelidir. Daha sonra implement edilecek arayüzler yazılır.

```cs
class A : B, IOrnek1, IOrnek2 {

}
```
