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


