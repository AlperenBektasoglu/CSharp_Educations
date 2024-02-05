C# Sql Transaction Nedir?

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

Örnek - 1

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
