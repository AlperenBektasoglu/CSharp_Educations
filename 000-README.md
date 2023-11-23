# CSharp_Educations
ENG: Repository for C# education documentations. This documentation is in Turkish.

TR: C# eğitim dökümanları reposudur. Bu dökümanlar Türkçedir.

-----------------------------------------
            #region Goto Komutu
            /* 
               C# goto deyimi koşulsuz olarak belirtilen etikete atlar. Etiket tanımlaması
               goto kullanımından öncede yapılabilir sonrada.
            */

            int sayı;
            baslangıc: // Etiket
            Console.Write("Notunuzu Giriniz: ");
            sayı = Convert.ToInt32(Console.ReadLine());

            if (sayı >= 0 && sayı < 50)
                Console.WriteLine("Kötü");

            if (sayı >= 50 && sayı < 60)
                Console.WriteLine("Geçer");

            if (sayı >= 60 && sayı < 70)
                Console.WriteLine("Orta");

            if (sayı >= 70 && sayı < 85)
                Console.WriteLine("İyi");

            if (sayı >= 85 && sayı <= 100)
                Console.WriteLine("Pekiyi");

            if ((sayı < 0 || sayı > 100))
            {
                Console.WriteLine("Yanlış Sayı Birimi Girdiniz.");
                goto baslangıc;
            }
            Console.ReadKey();
            Console.WriteLine("--------------------------------------");
            #endregion
