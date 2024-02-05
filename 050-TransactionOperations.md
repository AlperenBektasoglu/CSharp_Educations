## C# Sql Transaction Nedir?

bir grup işlemin arka arkaya gerçekleşiyor olmasına rağmen, seri işlemler halinde ele alınması gerektiğinde kullanılır. 
Transaction bloğu içerisindeki işlemlerin tamamı gerçekleşinceye kadar hepsi gerçekleşmemiş varsayılır. 
Bir işlem başarılı olursa, tüm veri işlemleri gerçekleştirilir ve veritabanının tutarlı bir parçası haline gelir. 
Bir işlem hatalarla / istisnalarla karşılaşırsa tüm veri değişiklikleri ve işlemleri kaldırılarak tutarsız veri girişinin önüne geçilmiş olur.

Bir örnek ile konuyu daha iyi açıklamaya çalışalım: Bir bankada hesaplar arası bir para transfer işlemi olduğunu varsayalım. 
Bankada Hesap1’den Hesap2’ye para aktarım işlemi yapılacak. Bu süreç iki işlemden oluşur: Öncelikle Hesap1 üzerinden aktarılmak istenen bedel Hesap1 bakiyesinden veritabanında güncelleme ile düşülür. 
Sonrasında ise Hesap2 hesap bakiyesi veritabanında güncelleme ile yükseltilir. 
Para aktarımı bu iki işlem başarılı olursa tamamlanır. 
Eğer, işlem 1 başarılı olur, ancak işlem 2 başarısız olur ise, Hesap2’ye para gitmediği gibi Hesap1 de boşuna para kaybetmiş olacaktır. 
Bunun gibi problemleri yönetebilmek için transaction yapısı kullanılır.

## Sql Transaction Kullanımı

```cs
string baglantiAdresi = "Server=127.0.0.1;Database=Test;User Id=sa;Password=123456;";// Bu alanı kendi bağlantı bilgileriniz ile güncelleyin ... 
SqlTransaction islem = null; //Transaction değişkenimizi tanımlıyoruz
 
//SQL bağlantımızı oluşturuyoruz
using (SqlConnection baglanti = new SqlConnection(baglantiAdresi))
{
    baglanti.Open();//SQL bağlantımızı açıyoruz
    SqlTransaction transaction = baglanti.BeginTransaction();//SQL bağlantımız için Transaction işlemini başlatıyoruz
 
    SqlCommand komut1 = new SqlCommand("insert into SiparisTablosu (siparisID, siparisAciklamasi) values(1, 'TestSiparis')", baglanti, transaction);  //İlk parça insert işlemini SQL'e gönderecek komutu yazıyoruz
    SqlCommand komut2 = new SqlCommand("insert into SiparisAyrintiTablosu (SiparisID, SatirNO, SatirAciklamasi) values(1, 1, 'Test Satiri')", baglanti, transaction);  //İkinci parça insert işlemimizi de SQL'e  gönderecek komutu yazıyoruz
    try
    {
        //try catch bloğu içinde komutlarımızı SQL'e gönderiyoruz
        komut1.ExecuteNonQuery();
        komut2.ExecuteNonQuery(); 
 
        //İki işlemimizde işlenirken bir hata gerçekleşmez ise Transaction işlemini onaylıyoruz
        islem.Commit();
    }
    catch (Exception hataMesaji)
    {
        //Bu blok çalışırsa try bloğu içinde herhangi bir yerde hata oluşmuş demektir ki o zaman SQL'e yazılan verileri geri alıyoruz
        islem.Rollback();
        //Verilen hatayı bir mesaj kutusunda programa gönderiyoruz
        MessageBox.Show(hataMesaji.ToString());
    }
    finally
    {
        //İşlem başarılı da olsa hatalı da olsa sonuç olarak SQL bağlantımızı kapatıyoruz
        baglanti.Close();
    }
}
```

## Entity Framework Transaction Kullanımı

Entity Framework, .NET tabanlı bir ORM (Object-Relational Mapping) aracıdır. Veritabanına erişim sağlamak için ve gerekli “Sorgulama”, “Kaydetme”, “Güncelleme” ve “Silme” gibi işlemleri kolayca yapmamızı sağlayan bir kütüphanedir. 
Entity Framework, bir ya da birden fazla veritabanı işleminin (örneğin, ekleme, silme, güncelleme gibi ) tek bir tarnsaction(mantıksal işlem) ile yapılmasını sağlayan yapısı mevcuttur. 
Aşağıdaki örneği inceleyebilirsiniz.

### Isolation Nedir?

Transation’lar birbirinden izole edilmiştir. Yani bir transaction’in başka bir transaction’dan etkilenmesi engellenmiştir. Bu, bir transaction’ın sonuçlarının diğer transaction’lar üzerinde etkili olmasını önler.
Entitiy Framework, farklı izolasyon seviyelerini desteklemektedir. Bunlar; ReadUncommitted, ReadCommitted, RepeatableRead, ve Serializable. Bunlar transaction’lar arasındaki izolasyon seviyelerini belirtir.
Aşağıdaki örnekte kullanımı mevcuttur.

**1- ReadUncommitted:** Diğer transaction’lar tarafından hala işlemi bitmemiş verileri de okumamıza izin veren bir izolasyon seviyesidir.

**2- ReadCommitted:** Bir transaction tarafından bir veri üzerinde işlem yapılacaksa, bu verinin başka transactionlar tarafından yapılan işlemlerinin bitmiş ve onaylanmış olması gerekmektedir. 
Yoksa işlemi yapacak transaction diğer transaction’ların işlerini bitirmesini bekleyecektir.

**3- RepetableRead:** Bir transaction sırasında diğer transaction’lar tarafından yapılan değişiklikleri görmesine ve aynı sorguyu tekrarladığında aynı sonuçları getirmesine izin verir. 
Yani veri üzerinde işlem yapan bütün transaction’ların işlerini bitirmesini bekler. Bu seviye ReadCommitted’ten daha fazla izolasyon sağlar.

**4- Serializable:** Veritabanında en yüksek izolasyon düzeyini sağlar. Bu seviye, bir transaction sırasında diğer transaction’lar tarafından yapılan değişiklikleri görmesini, aynı sorguyu 
tekrarladığında aynı sonuçları görmesini ve yeni satırların eklenmesini önlemesini sağlar. SERIALIZABLE seviyesi, diğer işlemlerin tamamını tamamlamasını bekler ve bu süre boyunca 
ilgili verileri kilitleyerek diğer işlemlerin müdahalesini önler.

```cs
// DbContext oluştur
using (var dbContext = new SampleDbContext())
{
    // Transaction başlat
    using (var transaction = dbContext.Database.BeginTransaction(System.Data.IsolationLevel.ReadCommitted))
    {
        try
        {
            // İşlemleri buraya ekleyin
            // Örneğin, yeni bir öğe eklemek:
            var newEntity = new SampleEntity { Name = "New Entity" };
            dbContext.SampleEntities.Add(newEntity);
            dbContext.SaveChanges();

            // Diğer bir işlemi gerçekleştir
            // Örneğin, var olan bir öğeyi güncellemek:
            var existingEntity = dbContext.SampleEntities.Find(1);
            if (existingEntity != null)
            {
                existingEntity.Name = "Updated Entity";
                dbContext.SaveChanges();
            }

            // Başarılıysa commit
            transaction.Commit();
            Console.WriteLine("Transaction başarıyla tamamlandı.");
        }
        catch (Exception ex)
        {
            // Hata durumunda rollback
            Console.WriteLine("Transaction başarısız: " + ex.Message);
            transaction.Rollback();
        }
    }
}
```
