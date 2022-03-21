# Bean Scope

Java Bean çokça karşımıza çıkan bir yapıdır. Aslında Java Bean’leri bildiğimiz Java sınıflarıdır. Ancak bir sınıfın bean sınıfı olabilmesi için bazı kurallara uyması gerekir.

1- java.io.Serializable arayüzünü implement  **etmelidir**.
2- Parametre almayan default constructor’ı  **olmalıdır**.
3- Tüm değişkenleri  **private tanımlanmalıdır**.
4- Private tanımlı değişkenlere erişim için get – set metotları  **olmalıdır**.
5- İçerisinde iş yapan başka bir metot  **olmamalıdır**.

Tüm bu özellikleri sağlayan sınıflara Java Bean sınıfları denir. Bean sınıfları çok katmanlı uygulamalarda katmanlar arasındaki iletişimi gerçekleştirmek için ve veri taşımak için kullanılır.

Beanlerimizin bir yaşam döngüsü vardır. Bu yaşam döngüsü çerçevesinde istediğimiz işlemleri yapması için Beanimizin kapsamını yani scope’unu belirlememiz gerekmektedir. Spring Beanlerimizdeki scopeleri Spring IoC container tarafından yönetilir ve beanlerimizdeki nesnelerin ne zaman ve nasıl oluşturulacağını belirler.
#### Kullanımı
Anotasyon olarak @Scope(“——“) olarak Bean’in en başına konulur.

```
@Scope("scope_türü")
public class Örnek{
...
}
```


### Scope Çeşitleri
Aşağıda, bir bean için tanımlanan farklı scopeları bulabilirsiniz :
| **Scope** | **Açıklaması**     |
|:--------:| :-------------:|
| **singleton** |Varsayılan olarak her bean Singleton’dur. Bu 		  Bean’den sadece bir tane üretilir.|
| **prototype** | Bean’e istek geldiğinde oluşturulur. Her istekte farklı bir instance oluşturulur. |
|**request**| Web uygulamaları için kullanılır. Her HTTP isteği geldiğinde instance oluşturulur.|
|**session**|Web uygulamaları için kullanılır. Her HTTP session oluştuğunda instance oluşturulur.|
|**globalSession**|Web uygulamaları için kullanılır. Her HTTP isteği geldiğinde sadece bir tane instance oluşturulur.|

## Singleton Scope

Bir bean default olarak singleton scope’a sahiptir. Bean singleton scope ile tanımlandığı zaman mevcut application context‘imiz içerisinde o bean’den yalnızca ve yalnızca tek bir adet initialize edileceğini garanti ederiz. Bu bean ile yapılacak olan tüm request’ler cache’lenmiş olan aynı nesne üzerinden yapılır. Bean nesnemiz üzerinde yapılan bir değişiklik bean’i kullanan tüm yerlerde etkilecektir. Scope notasyonun singleton için iki farklı kullanımını aşağıda görebilirsiniz.
```java
@Bean
@Scope("singleton")
//@Scope(value = ConfigurableBeanFactory.SCOPE_SINGLETON)
public Bean bean(){
	return new bean();
}
```

## Prototype Scope

Prototype ile belirlenmiş bir bean, container içerisinde çağırıldığı her request’te yeniden oluşturulacaktır. Scope notasyonun iki farklı kullanımını aşağıda görebilirsiniz.

```java
@Bean  
@Scope("prototype")  
//@Scope(value = ConfigurableBeanFactory.SCOPE_PROTOTYPE)  
public  Bean bean(){  
	return  new  bean();  
}
```
## Request Scope

Request scope değeri her bir http request’i bir adet bean oluştururur. Örnek bir bean’i şu şekilde oluşturabiliriz :

```java
@Bean  
@Scope(value  =  WebApplicationContext.SCOPE_REQUEST, proxyMode =  ScopedProxyMode.TARGET_CLASS) 
//@RequestScope  
public  Bean bean(){  
	return  new  bean();  
}
```

Web application context’inin örneklenmesi esnasında aktif bir request olmadığından dolayı proxyMode tanımının yapılması gereklidir. Spring framework, dependency olarak inject edilecek bir proxy oluşturur ve bir request’e ihtiyaç duyulduğunda ilgili scope’a sahip olan bean’i örnekler. Ayrıca, yukarıdaki @Scope tanımı için bir kısayol görevi gören @RequestScope notasyonunu da kullanabiliriz.

## Session Scope
Session scope değeri her bir http session’ı için bir adet bean oluşturur. Örnek bir bean’i şu şekilde oluşturabiliriz:

```java
@Bean  
@Scope(value  =  WebApplicationContext.SCOPE_SESSION, proxyMode =  ScopedProxyMode.TARGET_CLASS)  
//@SessionScope  
public  Bean bean(){  
	return  new  bean();  
}
```
## Application Scope

Bir application scope, ServletContext’in yaşam döngüsü için bean örneğini oluşturur. Bu singleton scope’a benzer ancak aralarında farklılıklar mevcuttur. Bir bean application scope değerine sahipken bu bean çoklu servlet tabanlı uygulamalar ile de paylaşılabilirken, singleton scope değerine sahip bir bean yalnızca mevcut application context’i içerisinde tanımlıdır.
```java
@Bean  
@Scope(value  =  WebApplicationContext.SCOPE_APPLICATION, proxyMode =  ScopedProxyMode.TARGET_CLASS)  
//@ApplicationScope  
public  Bean bean(){  
	return  new  bean();  
}
```
## WebSocket Scope

WebSocket scope’a sahip bean’ler tipik olarak singleton scope yapısındadır ve herhangi bir WebSocket oturumundan daha uzun yaşar. Bu nedenle, WebSocket scope’una sahip bean’ler için bir proxyMode tanımı gerekir. Singleton davranış sergilediğini, ancak yalnızca bir WebSocket sesion’ı ile sınırlı olduğunu da söyleyebiliriz.
```java
@Bean  
Scope(scopeName =  "websocket", proxyMode =  ScopedProxyMode.TARGET_CLASS)  
public  MyBean myBean(){  
	return  new  MyBean();  
}
```
