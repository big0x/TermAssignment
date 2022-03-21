
# Aspect-Oriented Programlama(AOP) - Pointcut ve Advice

Aspect, uygulamalarımızın *cross cutting concern* kısımlarını işleyen bir programlama paradigmasıdır ve paradigmanın çıkış noktası concernlere çözüm üretmektir. Bu yapının kullanılma motivasyonu, single responsibility ve don’t repeat yourself gibi prensiplere uygun olmasıdır.

Concern, uygulamalarımızın belli bölümlerinde core fonksiyonlarımızın dışında yapı ve kurallar dahilinde gerçekleşen **logging, performance, transaction management, security, caching, validation, exception handling** gibi sınıflandırdığımız çatıların her biridir. Cross cutting concern denmesinin sebebi uygulamızın istenilen yerlerinde kullanılması ve kullanılırken o bölgeden soyutlanmış yapılar olmasıdır.

 AOP frameworkü Spring'in temel bileşenlerinden biridir. Spring IoC container AOP'ye bağlı olmasa da, AOP çok başarılı bir ara katman yazılımı çözümü sağlamak için Spring IoC'yi tamamlar.

### Avantajları
-  Uygulamamızın daha esnek olması ve yönetimi kolaylığı,  
- Tekrar eden kod düzeninden kurtulma,  
- Daha temiz ve anlaşılabilir bir kod,  
- Core logic ve concernlerin birbirinden ayrılması.

## AOP Nerelerde Kullanılır

Aspect Oriented Programming uygulamanın ana işlevi dışında kalan, genel maksatlı yan işlevlerde kullanılır. Örnek vermek gerekirse:

**Logging** → Servisimize gelen request ve response’ların loglanması.  
**Transaction Management** → Ödemenin alınmasından itibaren çalışan kod döngüsünde oluşacan hata sonrası iade işleminin gerçekleştirilmesi.  
**Performance** → Metodların çalışma sürelerinin hesaplanması.  
**Validation** → Atılacak e-mail öncesi kullanıcı e-mail izin kontrolü.

### AOP Kavramları

Bazı temel AOP kavramlarını tanımlamak gerekirse:
>Bu AOP konseptleri Spring'e özgü değildir.

**Aspect** : Birden fazla nesneyi bağlayan concernlerin modülerize edilmesidir. Transaction yönetimi, J2EE uygulamalarında crosscutting concerne iyi bir örnektir. Spring AOP'de aspectler sınıflarda *@Aspect* anotasyonuyla implemente edilerek kullanılır.

**Advice** :  Uygulamaya dahil edilen yukarıdaki yan işlevdir. Yani ek davranıştır. AOP terminolojisinde bazen advice yerine concern kelimesi de kullanılır

**Join Point**:
Advice'ın hangi noktalara dahil edilebileceğidir. Bu noktalar metod girişi, metod çıkışı, bir event'in tetiklenişi olabilir.  AspectJ'de Join Point şöyle alınır:

```java
aspect AspectExample {
  before() : execution(* aspects.trace.demo.*.*(..))
  {
    logger.entering(thisJoinPointStaticPart.getSignature().getName(),
                    thisJoinPointStaticPart.getSignature().getDeclaringType());

  }

  after() : execution(* aspects.trace.demo.*.*(..))
  {
    logger.exiting(thisJoinPointStaticPart.getSignature().getName() ,
                   thisJoinPointStaticPart.getSignature().getDeclaringType()  );

  }
}
```
**Pointcut**:

Yukarıdaki Join Point'lerden hangisine advice eklenmesi gerektiğini belirten örüntüdür. Bazı pointcut örnekleri:

Parametreleri dikkate almadan ismi set olan tüm metodları ile eşleşir.
```java
call(* set(..))
```
Parametreleri dikkate almadan tüm metodlar ile eşleşir  

```java
execution(* *(..))
```
Point sınıfının setX ve setY isimli belirtilen imzaya sahip metodları ile eşleşir.  

```java
pointcut setter(): target(Point) &&
                   ( call(void setX(int)) ||
                     call(void setY(int)) );
```

**Weaving**  : Derleyici tarafından normal kodun ve AOP kodunun birleştirilerek derlenmesidir.

**Execute Around Idiom**  
Metodun girişinde ve çıkışında kod çalıştırmak anlamına gelir.

## Advice Tipleri

**@Before:** Method devreye girmeden önce çalışır.  
**@AfterReturning:** Method başarılı sonuçlandıktan sonra çalışır.  
**@AfterThrowing:** Methodun exception dönmesi durumunda çalışır.  
**@After:** Returning ve Throwing her iki durumdada çalışır. (finally)  
**@Around:** Method devreye girmeden önce ve metod bittikten sonra çalışır.

## Pointcut İfadeleri

Pointcut (kesim noktası) aspectimiz ile neyin eşleşmesi gerektiğini belirler.

 **target:** Metodumuzun çalışması hedeflenen beani ifade eder.  
 **execution:** Metodumuzun çalışacağı bölge belirtilir.  > **@annotation:**  Hedef anotasyon dahilinde çalışacağı anlamına gelir.

Pointcut ifadelerinin bir çok çalışma yöntemi vardır, kaynaklar bölümünden farklı çalışma yöntemlerini de inceleyebilirsiniz.  
Örnek bir Aspect performance log uygulaması:

```java
@Around("@annotation(LogExecutionTime) && target(bean)") 

public Object logPerformance(ProceedingJoinPoint jp, Object bean) throws Throwable {

	final StopWatch stopWatch = new StopWatch();

	stopWatch.start();

	Object result = jp.proceed();

	stopWatch.stop();

	final long executionTime = stopWatch.getTotalTimeMillis();

	final String methodName = jp.getSignature().getName();

	final String className = bean.getClass().getSimpleName();

	log.info("Execution time {} ms for method: {} in class: {}",
								executionTime, methodName, className);

return result;
}
```

**JoinPoint’i**  aşağıdaki advice türleriyle kullanın:

>**@Before**
>**@After**
>**@AfterReturning**
> **@AfterThrowing**

**ProceedingJoinPoint’i**  aşağıdaki advice türü ile kullanın:  
JoinPoint’ten farkı içindeki .proceed() ile return value yu handle edebiliriz.

>**@Around**
```java
@LogExecutionTime

public List<EmailDto> getAll() throws Exception {

	Thread.sleep(3000);

	final EmailDto emailDto1 = EmailDto.builder()

		.id(1L)

		.to("mehmet@demircan.com")

		.from("it@mnd.com")

		.content("Email 1")

		.build();

	final EmailDto emailDto2 = EmailDto.builder()

		.id(2L)

		.to("all@demircan.com")

		.from("ik@mnd.com")

		.content("Email 2")

		.build();

	return List.of(emailDto1, emailDto2);
}
```

## Kaynaklar
 
[**Spring AOP Tutorial**](https://www.tutorialspoint.com/springaop/index.htm)

[**Aspect-Oriented Programming**](https://en.wikipedia.org/wiki/Aspect-oriented_programming)

[**Introduction to Pointcut Expressions in Spring | Baeldung**](https://www.baeldung.com/spring-aop-pointcut-tutorial)




