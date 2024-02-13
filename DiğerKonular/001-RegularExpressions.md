
## Regular Expressions (Düzenli İfadeler)
Regular Expressions (Düzenli İfadeler) kelimesinin kısaltması olan regex, e-posta adresi, tarih, telefon numarası gibi kullanıcı tarafından girilen ve 
belirli bir düzen içeren girdilerin kontrolünün sağlanması ve herhangi bir kod, metin içerisinde istenilen yazı veya kod parçasının aranıp bulunmasını, 
yönetilmesini sağlayan kendine ait söz dizimi olan bir yapıdır.

```cs
string text = "12321dssdvdfbfg12321";
string regexPattern = "^91";
Regex regex = new Regex(regexPattern);
Match match = regex.Match(text);
Console.WriteLine(match.Success);
```

**Not:** Regular Expressions'lar ile ilgili daha detaylı bilgi için aşağıdaki linke tıklayarak, Sıradaki 11 videoyu inceleyebilirsiniz.
Link: https://www.youtube.com/watch?v=zeOJWTtCUNs&list=PLQVXoXFVVtp3e_urGZcMNAHx2Eo4Rm5Xk&index=353
