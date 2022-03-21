# Method Overriding ve Method Overloading

![Java Overriding ve Overloading Arasındaki Fark](https://emrecelen.com.tr/wp-content/uploads/2021/07/java-overriding-ve-overload-arasindaki-fark.png)

## Method Overriding
Uygulamalarda kullandığımız inheritance sayesinde üst sınıftan, alt sınıfa geçecek metotların o sınıf yapısına uygun bir şekilde tekrardan gövdesinin değiştirilmesine olanak sağlar. Kullanırken dikkat edilmesi gerekenler:
-   Üst sınıf içerisinde yer alan private metotlar override işlemine tabi tutulmaz. Aksi takdirde hata alınır.
-   Override ettiğimiz bir metodun erişim belirleyicisinin seviyesini düşüremeyiz fakat yükseltebiliriz.
-   Üst sınıftan miras aldığımız bir metodun dönüş tipini veya parametrelerini değiştiremeyiz.
-   Static ve Final olarak tanımlı metotları override edemeyiz.
-   Üst sınıfımızdaki ve alt sınıfımızda bulunan override edeceğimiz metot isimleri aynı olmalıdır.
-   Constructor (Yapıcı / Kurucu) metotlar override edilemez.

### Neden kullanmalıyız?
-   Temiz, sade ve anlaşılır kod satırları oluşturmamıza imkan sağlar.
-   Bir sınıfın hangi yapıda duruş sergileyeceğini ve metotların işlevlerinin nasıl uygulanacağını tanımlamamıza imkan sağlar.


## Method Overloading

Uygulamalarımızda oluşturmuş olduğumuz metotların yapısal olarak yeniden yazılmasına, esneklik sahibi olmasına ve daha fazla işlevsel bir hal almasına olanak sağlayarak aynı isimde birden fazla metodumuzun oluşmasına imkan verir. Kullanırken dikkat edilmesi gerekenler:

-   Overload yapacağımız metotların isimlerinin aynı olması gerekmektedir.
-   Metotlarımızın sahip oldukları parametreler birbirinden farklı olmalıdır.  **Örneğin:**  metot(**parametre 1**) ve metot (**parametre 1**,  **parametre 2**) şeklinde olmalıdır.
-   Overload işlemine tabi tuttuğumuz metot yapılarının dönüş tipleri birbirinden farklı olabilir.  **Örneğin:**  **void**  metot(prm1) ve  **int**  metot(prm1,prm2) şeklinde dönüş tiplerini değiştirebiliriz.
-   Devamı olarak ekstra bir tanımlama yapmak gerekir, oluşturmuş olduğumuz metot yapılarının dönüş tiplerini sadece değiştirmemiz yetmez,  **ekstra olarak**  bir parametre tanımlaması veya çıkartması yapmamız gerekmektedir.

### Neden kullanmalıyız?

Method overloading işlemi sayesinde metodumuzu aşırı yükleyerek tek bir isimle farklı parametreler bile kullanılsa işlemi gerçekleştirmemiz mümkün. Metot  farklı parametreler ile aşırı yüklenerek Java geliştiricilerine büyük kolaylık sağlar

## Method Overriding ve Method Overloading Arasındaki Farklar

Method Overriding | Method Overloading
-------- | -----
Run-time polimorfizmidir.| Compile-time polimorfizmidir.
Superclass veya üst class tarafında kullanılan bir metodun özel kullanımı için uygundur. | Kodun okunabilirliğini arttırır.
Birbirine inheritance olan 2 sınıfta gerçekleştirilir. | Bir sınıfın içinde gerçekleşir.
Inhertance durumu zorunludur. | Inheritance gerekli değildir.
Metodlar aynı isme ve aynı signlara sahip olmalıdır. | Metodlar aynı isme ve farklı signlara sahip olmalıdır.
Return tipi aynı veya ortak değişken olmalıdır. | Return tipi aynı olmak zorunda değildir parametre değişimi yeterlidir.
