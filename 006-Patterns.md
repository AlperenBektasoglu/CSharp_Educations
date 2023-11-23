
## Type Pattern
is operatörünün desenlendirilmiş halidir.
is operatörü ile belirlenen türün dönüşümü sağlanabilir.
```cs
object x = "Alperen";
if(x is string){} // is operatörü

if(x is string xx){} // Type Pattern - Burada oluşturulan xx simli değişkene if'in dışından da erişilebilir ama kullanırken hata alınır.
```

## Constant Pattern
Elimizdeki veriyi sabit değerler ile karşılaştırabilmemizi sağlar. Bu pattern ile is operatörünün, == operatörü gibi 
çalışabilmesi sağlanmış olur.
```cs
if(x is "Alperen"){} 
```

## Var Pattern
Elimizdeki veriyi 'var' değişkeniyle elde etmemizi sağlar. Bu pattern'nin type pattern'den farkı, oluşturulan yeni
değişkenin if dışında kullanılırken hata almamasını sağlar.
````cs
object x = "Alperen";
if(x is var xx){}
```

