

# Spring Anotasyonları : @Controller ve @Repository

Spring, en popüler Java EE frameworklerinden biridir. Java EE geliştiricilerinin basit ve reliable kurumsal uygulamalar geliştirmesini sağlayan açık kaynak kodlu bir frameworktür. Bu framework bize business nesnelerimizi yönetmek için çeşitli olanaklar sağlar. Klasik frameworklere ( JDBC, JSP, Java Servlet) ve hatta uygulama programlama arayüzlerine (API) göre uygulama geliştirmeyi çok daha kolay hale getirdi. Spring, kurumsal uygulama geliştirmek için AOP, Plain Old Java Object (POJO) ve Dependency Injection gibi bir çok yeni teknik kullanır.

Birçok Spring Anotasyonu bulunmaktadır. Bunlardan bazıları:
-   **@Repository**
-    **@Controller**
-   @Configuration
-   @ComponentScan
-   @Bean
-   @Component
-  @Autowired
-  @Required
-  @Service, vb. 

## @Repository
@Repository Anotasyonu bir sınıfın nesneler üzerinde temel işlemlerin gerçekleştirdiğini belirtmek için kullanılan anotasyondur. Bu temel işlemler depolama, alma, silme, güncelleme, arama gibi sıralanabilir. Spring, classpath scanning ile repository sınıflarını otomatik olarak algılar. @Repository anotasyonu , DAO sınıflarının veritabanı tablolarında CRUD (create, read, 
update, delete) operasyonlarını gerçekleştiren DAO modeline çok benzerdir. 
### Kullanım şekli
````java
@Repository
public class CarDao{ 
	..... 
}
````

Özet olarak :
-   Veritabanı sorgularının gerçekleştirildiği sınıfları belirten bir anotasyondur.  
    
-   Database kaynaklı exception yakalar. (Platform specific exceptions)
-   Anotasyon tanımından sonra, ilgili sınıf için otomatik olarak XML dosyasında bean tanımlaması eklenir.
-   Spring JPA veya JPA alternatifi database işlemlerini gerçekleştiren yapılar @Repository tanımlamasına sahip sınıflar üzerinden kullanılabilir.

## @Controller

@Controller Anotasyonu bir sınıfın *web request handler* olduğunu belirtmek için kullanılan anotasyondur. Bu anotasyon @RequestMapping anotasyonu ve onun handler metotlarıyla birlikte kullanılır. Sadece sınıflar için kullanılır. Çoğunlukla Spring MVC (Spring model-view-controller) uygulamalarında kullanılır. Spring bu anotasyonun kullanıldığı sınıflardaki metodları tarar ve @RequestMapping anotasyonunu algılar.

**Kullanım Şekli**
````java
@Controller
public class CarsController{ 
	..... 
}
````

Özet olarak : 

-   Sınıfın, dışardan gelen requestleri yakalaması gereken bir sınıf olduğu belirtilir.
-   Annotation taramaları esnasınasında @Controller ve onun altındaki @RequestMapping tanımları taranır.
-   Bu sebeple @RequestMapping ifadesini yalnızca @Controller tanımlı sınıflarda kullanabiliriz
-   @Controller sınıf seviyesinde bir anotasyonken, @RequestMapping fonksiyon seviyesinde bir anotasyondur.

