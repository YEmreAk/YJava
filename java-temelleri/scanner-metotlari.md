---
description: Scanner metodu kullanıcıdan girdi almak amaçlı kullanılan bir metottur.
---

# 💠 Scanner Metotları

## 👀 Metotlara Hızlıca Bakış

* Herhangi bir obje türünde girdi alınabilmekte
* Obje türünü belirlemek için sınıfın içindeki alt metotları kullanıyoruz

| Metot | Döndürdükleri |
| :--- | :--- |
| `next()` | String |
| `nextLine()` | String |
| `nextByte()` | byte |
| `nextShort()` | short |
| `nextInt()` | int |
| `nextLong()` | long |
| `nextFloat()` | float |
| `nextDouble()` | double |
| `hasNext()` | boolean |
| `useDelimeter(<ayıraç>)` | void |
| `delimeter()` | String |
| `close()` | void |

### ⚾ `next` Metodu

Klavyeden alınan girdileri, ilk [**whitespace**](https://wiki.yemreak.com/programlama-notlari/java/diger-java-notlari/java-scanner-metodlari#java-whitespaces) ****girdisine kadar almakta ve bu girdiyi **string** türünde döndürmekte.

### 🏐 `nextLine` Metodu

Klavyeden alınan girdileri, ilk ENTER \(`"\n"`\) girdisine kadar almakta ve bu girdiyi **string** türünde döndürmekte.



### 🎳 `nextByte` `nextShort` `nextInt` `nextLong` `nextFloat` `nextDouble` Metodları

Klavyeden alınan girdileri `byte` / `short`/ `int` / `long` / `float` / `double` türünden alır.

> Farklı bir aralıkta sayı değeri girilirse, hata \(`exception`\) verir.



### 🏀 `hasNext` Metodu

Scanner tipinde tanımlamış olduğumuz değişkenin bir satır sonrasında veri olup olmadığını kontrol eder.

> Şekillendirilebilir. `hasNextInt()` bir sonraki satırda `int` olup olmadığını kontrol eder ve sonuca göre `true` / `false` döndürür.



### 🏓 `useDelimeter` Metodu

`next` metodun veri alma sınırını paremetre olarak aldığı değere göre belirler.

* Parametre olarak **string** tipinde değişken alır.
* Normalde `next` metodu whitespace karakterine geldiğinde veri almayı kesmektedir.
* Bu metotdan sonra `next` metodu **parametreye** denk geldiğinde veri almayı kesmiş olacak.



### 🏉 `delimeter` Metodu

Scanner tipinde tanımlanmış olan değişkenin sınırlayıcısını döndürür.

* Yani `useDelimiter("mi")` yapıtğımız bir objenin `delimiter` metodu `"mi"` _string_'ini döndürecektir.
* Varsayılan sınırlayıcı değiştirilmediyse `next` metodu `"\p{javaWhitespace}+"` _string_'ini döndürür.

> `"\p{javaWhitespace}+"` deyimi Java whitespace olarak aşağıda tanımlanmıştır.

### 🧶 `close` Metodu

Herhangi bir değer döndürmeyen bu fonskiyon, `Scanner` objesini kapatır.

## 🌌 Java Whitespaces

Javada tanımlı olan **whitespace**'ler:

* `"\n"` - Satır atlatma ENTER
* `"\t"` - Bir TAB kadar boşluk atlatma
* `"\r"` - Bir TAB kadar satır atlatma
* `" "`- Boşluk atma SPACE

