
# ArrayList
ArrayList, java.util paketinde bulunur ve collections framework’unun bir parçasıdır. Dinamik dizi oluşturmaya olanak sağlar. **Temel dizilerden daha yavaş olsa bile, bu yapı, bir dizi üzerinde birçok işlemin gerekli olduğu uygulamalarda yardımcı olur.**

ArrayList, AbstractList soyut sınıfın inherite eder ve List interface'ini implemente eder.

ArrayList istenilen büyüklükle başlatılabilir, ancak nesneler eklenirse koleksiyon(collection) büyür veya nesneler çıkarılırsa koleksiyon(collection) küçülür. Özetle boyutu standart dizilerin aksine dinamiktir, boyutu artabilir veya azalabilir. ArrayList, primitive türdeki veriler için kullanılamaz. ArrayList farklı sınıflardan nesne saklayabilir. **ArrayList, ekleme sırasını, yani eklenen nesnenin sırasını korur.**

ArrayList bir sınıf olduğu için bu sınıfa ait metotları nesne üzerinde kullanabiliriz. Örneğin  _add()_ metodu ile ArrayList’e elemanlar ekleyebiliriz.

ArrayList, dizilerden farklı olarak bellekte sabit yer ayırma yerine, saklanmak istenen veri uzunluğunda esneklik sağlar. Dolayısıyla ArrayList  _add()_  metodu ile eleman eklemeye devam edebiliriz.

## ArrayList Metodları

Örnek vermek için bir liste oluşturalım:
````java
ArrayList<String> cars = new ArrayList<String>();

cars.add("BMW");
cars.add("Mercedes");
cars.add("Opel");
````

### Get() Metodu

ArrayList’de birçok farklı metot vardır. Elemanlara erişmek için dizi(array)lerden farklı olarak yine metot kullanırız. Bunun için get() metodunu kullanırız. Aşağıdaki tanımladığımız ArrayList’in elemanlarını yazdırmak için get() metodu kullanılmaktadır.
````java
System.out.println(cars.get(0));

System.out.println(cars.get(1));

System.out.println(cars.get(2));
````

### Set() Metodu

ArrayList elemanlarını değiştirmek için set(indis, değer) biçiminde set metodunu kullanırız. Aşağıdaki örnekte 2 indisine sahip elemanı, set() metodunu kullanarak "Ford" ile değiştirdikten sonra yeniden yazdırıyoruz.

````java
`cars.set(2, "Ford");

System.out.println(cars.get(2));
````

### Size() Metodu

Dizilerde bir elemanın uzunluğunu bulmak için  _.length_  değerini kullanırken, ArrayList’lerde listenin boyutunu bulmak için size() metodunu kullanırız.

````java
for(int i = 0; i < cars.size(); i++){

...

}
````

veya 
````java
for(String car : cars)
System.out.println(car);
````

### Remove() Metodu

ArrayList’lerde listenin bir elemanını silmek için kullanılan metottur. Parametre olarak silinmek istenen elemanın indisi kullanılır.

````java
cars.remove(1);
````


### Clear() Metodu

ArrayList’in içeriğini temizlemek için clear() metodunu kullanırız.

````java
cars.clear();
````

## Vector  Ve Aralarındaki Farklar

Vector sınıfı Java Collections Framework’ un bir üyesidir. Klasik programlama eyleminde array (dizi) çok önemli bir rol oynar. Ancak, array’in uzunluğu; yani bileşenlerinin sayısı array bildiriminde belirleniyor ve bu uzunluk daha sonra değiştirilemez. Bazı durumlarda, bu kısıtlama ciddi bir handikap oluşturur. Java 2'den sonra bu sorunu çözmek için Vector sınıfını ve benzer işi yapan ArrayList sınıfını ortaya koydu. Her iki sınıfta, diziye yeni öğeler eklenir ya da varolan öğeler silinirse, dizinin uzunluğu kendiliğinden değişir. Tabii, bu değişimin bellek kullanımı ve zaman açısından bir bedeli  vardır. Vector ya da ArrayList sınıfına ait nesneler bu işleri kendiliğinden yaparlar. ArrayList ve Vector'ü ayıran şeyler ise:

ArrayList | Vector
:--------: | :-----:
ArrayList asenkrondur. | Vector ise senkrondur.
Öğe sayısı kapasitesini aşarsa ArrayList, geçerli dizi boyutunun %50'sini artırır. | Toplam öğe sayısı kapasitesini aşarsa dizi boyutunu iki katına çıkarır.
ArrayList eski bir sınıf değil. JDK 1.2'de tanıtılmıştır. | Vector, eski bir sınıftır.
ArrayList senkronize olmadığı için hızlıdır. | Vector yavaştır çünkü senkronizedir, yani multithread bir ortamda, mevcut thread nesneyi serbest bırakana kadar diğer threadleri çalıştırılabilir veya çalıştırılamaz durumda tutar.
ArrayList, öğeler arasında geçiş yapmak için Iterator arabirimini kullanır.| Bir Vector, öğeleri geçmek için Iterator arabirimini veya Enumeration arabirimini kullanabilir.


