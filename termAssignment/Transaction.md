
# Transaction
Transaction işlemi bir veya birden fazla fonksiyonun aynı süreçte işlem görmesidir.Bu sayede eğer istenmeyen bir durum oluştuğunda bütün bu süreci geri alabiliriz(_rollback_), yada hepsi aynı anda onaylayabiliriz. Transaction Handlingi try-catch bloklarıyla yönetebilirsin fakat bu yöntem istenmeyen, defensive programming prensibine aykırı durumlar ortaya çıkarabilir aynı zamanda kodun okunabilirliğini azaltır.
Bu işi Spring'e bırakmak her zaman daha kullanışlı ve garantidir. Spring java kodlarını anotasyonlar üzerinden yönetir. Transaction handling için ise ***@Transactional*** anotasyonu kullanılır. Hem class hem de fonksiyon seviyesinde yapılabilir.

# Özellikleri 

## **propagation**

Bu özellik ile yeni bir transaction açılıp açılmayacağına, mevcut bir transaction var ise kullanılıp kullanılmayacağına kara verilmesine sağlar.

**Propagation._REQUIRED:_** .Eğer mevcutta bir transaction var ise yeni bir transaction açmadan bu transactionu kullanır, eğer transaction yoksa yeni bir transaction açar. @Transactional keywordu yazıldığında davranış şekli otomatik olarak “REQUIRED” dır.

**Propagation._SUPPORTS:_** Eğer bir transaction var ise o transaction u kullanır .Yok ise transaction’sız çalışır. Yeni bir transaction da açmaz

**Propagation._MANDATORY_:**  Eğer bir transaction yok ise exception fırlatır

**Propagation._REQUIRES_NEW :_** Aktif bir transaction var ise bunu bekletir(*Suspend*), ve yeni bir transaction açar

 **Propagation._NOT_SUPPORTED:_**  Eğer bir transaction var ise o transaction’u suspend edilir ve yen bir transaction da açmaz

**Propagation._NEVER_:**  Eğer bir transaction var ise exception fırlatır

**Propagation._NESTED :_** Bu parametre JDBC teknolojisin geliştirdiği savepoint ile beraber kullanır.Eğer bir transaction var ise paralelde başka bir transaction açar(Nested transaction) ve bu transaction rollback olurken diğer transaction devam eder .Eğer transaction yok ise “**_REQIRED_**” olarak çalışır.  [Save point teknolojisi kullanıldığı için sadece JDBC kaynak işlemlerinde çalışır.](https://docs.spring.io/spring/docs/4.2.x/spring-framework-reference/html/transaction.html#tx-propagation)

## **readOnly**

Bu özellik true olarak set edildiğinde read-only transaction açılır. Veritabanında herhangi bir değişiklik yapılmayacak olan transactionlarda kullanılabilir.

## timeOut özelliği

Tanımlanan bu özellik sayesinde belirlenen süre içerisinde sorgunun sonucu gelmediğinde rollback işlemini gerçekleştirir.

## rollbackFor özelliği

Sizin belirlemiş olduğunuz class’a göre rollback işleminin yapılıp yapılmayacağını belirler.

> [Belirlenen sınıfın Throwable sınıfından türetilmesi gerekir](https://docs.spring.io/spring/docs/4.2.x/spring-framework-reference/html/transaction.html)

Uncheck exception olarak fırlatılan (örn :NullPointerException, ArrayIndexOutOfBound) gibi hata sınıfları bu durumdan etkilenmez ve transaction tarafından rollback edilir

rollbackFor özelliği array olarak kullanılma istenirse  **rollbackForClassName** olarak kullanılmalıdır.

Rollback yapılması istenmeyen classlar içinde  **noRollbackFor** ve array olarak verilecek claas name ler ise  **noRollbackForClassname** olarak kullanılmalıdır.Bu iki kullanımda da rollback yapmasını istemediğimiz class isimlerini yazıyoruz.

Örnek olarak bir kullanıcının başka bir kullanıcıya para gönderdiğini düşünelim.
````java
	@Transactional(propagation = Propagation.REQUIRED)

	public void saveSenderBalance(){

		User user = new User();

		user.setBalance(//Gönderilen miktarın bakiyeden düşmüş hali);

		userDao.save(user);

		saveRecipientBalance();

}

	@Transactional(propagation = Propagation.REQUIRED)

	public void saveRecipientBalance(){
	
		User user = new User();

		user.setBalance(//Gönderilen miktarın bakiyeye eklenmiş hali);

/*Bu kısımda bir hata olduğunu ve save işleminin yapılamadığını varsayalım.*/

		userDao.save(customer);

}
````
Transactional metodu bu transaction işlemi başarısız olduğu için tüm işlemi rollback ile geri alır ve göndericinin bakiyesi de böylece düşmemiş olur.

# Kaynak
[**Spring Framework Docs - Transaction**](https://docs.spring.io/spring-framework/docs/4.2.x/spring-framework-reference/html/transaction.html#tx-propagation)


