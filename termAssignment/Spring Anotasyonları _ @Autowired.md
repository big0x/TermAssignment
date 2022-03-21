
# Spring Anotasyonları : @Autowired

Bean konfigürasyonlarını genellikle Spring Bean Konfigürasyon dosyasında yapılır ve referans özelliğini kullanarak diğer beanlere injection edilir. Ama Spring frameworkü, bean injection konfigürasyonlarını açıkça belirtmediğimiz yerlerde de *autowiring* özelliğini kullanır. *@Autowired* anotasyonu sayesinde bir bean içerisindeki değerleri başka beanin içerisine enjekte edebilir değerlerini koruyarak kullanabiliriz. *@Autowired* anotasyonunu bir değişken, setter ya da yapılandırıcı metot üzerinde kullanılabilmekteyiz.

Bu şekilde Xml bağımlılığını minimum seviyeye indirebiliriz. Autowiring yapmanın çeşitleri bulunmaktadır. Bunlar:

| Tip | Açıklama |
|:--------:| :-------------:|
| No | Varsayılandır. Bağımlılıklar tek tek yazılır. |
| Name | Bileşen özelliklerine otomatik olarak bağlanır. Aynı adda olan bean’e bağlanır. |
| Type | Aynı tip ve türden olan bileşenler bağlanır. |
| Constructor | Constructorlar üzerinden bileşenler bağlanır. |
| Autodetect | Varsayılan olarak constructor üzerinden bağlanır. Eğer constructor yoksa byType olarak bağlanır. |

Örnek vermek gerekirse:
Bir sistemde müşteri ve base user sınıfı oluşturup farklı şekilde @Autowired
anotasyonunun kullanımına bakalım.

**User**
````java
@Data
@AllArgsConstructor
@NoArgsConstructor
public class User {
	private int id;
    private String email;
    private String password;
}
````

**Customer**

````java
public class Customer {
    private int id;
    private User user;
    }
````

## **Constructor tipinde Autowiring**
Aşağıda müşteri nesnesi oluşturulurken base customer nesnesine constructor yoluyla autowiring yapılır:
````java
public class Customer {

    private int id;
    private User user;

    public Customer() {
    }

    @Autowired
    public Customer(User user) {
        this.user = user;
    }
}
````

## **Property-based tipinde Autowiring**
````java
public class Customer {

    private int id;

    @Autowired
    private User user;
}
````

## **Setter tipinde Autowiring**

````java
@Autowired
public void setUser(User user) {
    this.user = user;
}
````


