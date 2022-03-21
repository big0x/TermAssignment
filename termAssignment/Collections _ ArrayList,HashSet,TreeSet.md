
# Collections : ArrayList, HashSet, TreeSet

İçerisinde birden fazla nesne barındırabilen ve gerektiğinde nesne ekleme-silme gibi işlemlere imkan sağlayan bir başka nesnedir. Koleksiyonun içerisinde barındırdığı nesnelere koleksiyonun elemanları denir. Java koleksiyon çatısı altında 3 ana koleksiyon tipi sunmaktadır. **SET, LIST, MAP** ve yine  
bunlara ait aynı isimde 3 interface bulunmaktadır. Bu interface-arabirimlerin nesneleri şunlardır:

**Set Nesnesi:**  Kendisine verilen elemanların her birinde sadece bir tanesini tutar. Kopya ya da tekrarlanan elemanları barındırmaz.

**List Nesnesi:**  Kendisine verilen elemanları sıralı şekilde tutar. Tekrarlanan elemanları barındırabilir.

**Map Nesnesi:**  Her biri birbirinden farklı anahtarlar ile eşleştirilen nesnelerden oluşur.

Koleksiyonlar Collection Interface’ini temel alırlar. Bu interface List ve Set interfacelerini *extends*ler. Bunlar java tarafından sağlanan ve nesneler üzerinde işlemler yapmamızı sağlayan en tepe interfacelerdir. En tepede Collection Interface'i ve bu interfacelerden türeyen List, Set, ve Set interface'inden türeyen SortedSet interface'i bulunmaktadır.

### Avantajları
-   Veri ekledikçe veya çıkardıkça, collection yapısının uzunluğunu otomatik olarak ayarlaması ve oldukça büyük bir esneklik sağlaması.
-   Listeleme, sıralama gibi çeşitli algoritmaları oturup sıfırdan yazmamıza gerek bırakmadan collections içerisinde bulunan algoritmaları kullanmamıza imkan sağlar.
-   Oluşturduğumuz uygulamaya sağlayacağı esneklik ve performans arttırıcılığı özelliği ile uğraşmamız gereken sıkıntıları otomatik olarak çözer.
-   Verileri bir araya toplayarak işlem yapmamızı kolaylaştırır.

### Dezavantajları
-   Uygulamanın derlenmesi esnasında, oluşturduğumuz koleksiyon yapılarının veri tiplerinin denetiminin gerçekleştirilmemesi.
-   Koleksiyon yapılarımızı oluştururken atayacağımız veri tipinin doğru bir şekilde seçilmesi gerekmektedir.

# ArrayList vs HashSet vs TreeSet

## ArrayList

ArrayList, java.util paketinde bulunur ve collections framework’unun bir parçasıdır. Dinamik dizi oluşturmaya olanak sağlar. **Temel dizilerden daha yavaş olsa bile, bu yapı, bir dizi üzerinde birçok işlemin gerekli olduğu uygulamalarda yardımcı olur.**

ArrayList, AbstractList soyut sınıfın inherite eder ve List interface'ini implemente eder.

ArrayList istenilen büyüklükle başlatılabilir, ancak nesneler eklenirse koleksiyon(collection) büyür veya nesneler çıkarılırsa koleksiyon(collection) küçülür. Özetle boyutu standart dizilerin aksine dinamiktir, boyutu artabilir veya azalabilir. ArrayList, primitive türdeki veriler için kullanılamaz. ArrayList farklı sınıflardan nesne saklayabilir. **ArrayList, ekleme sırasını, yani eklenen nesnenin sırasını korur.**

## TreeSet

Collection içerisinde yer alan **SortedSet** interface yapısının içerisinde yer alan bir kavramdır. İçerisinde benzersiz özelliklere sahip değerleri korur, bu değerleri hiyerarşik bir sıralama sistemine göre saklayan, **NavigableSet** interface yapısına göre hareket eden çeşitli collection özelliklerine ev sahipliği yapan bir sınıf sistemidir. Collection çatısı altında yer aldığı için birden fazla **constructor metot** tanımlamaları ile farklı kullanım şekillerine ev sahipliği yapar.

### Özellikleri

-   **SortedSet**  yapısına bağlıdır, bu yüzden tekrarlanan öğelere izin vermez.
-   TreeSet, verilerin  **eklenme sırasını**  korumaz, fakat TreeSet yapısındaki  **doğal sıralamaya**  göre sıralanır.
-   TreeSet  **nesnesini tanımlarken**  özel bir karşılaştırıcı kullanabiliriz.
-   Daha büyük miktardaki bilgileri depolamak için kullanılır. Bu durum verilerin  **daha hızlı**  ve  **kolay**  bir şekilde erişmemize imkan verir.


## HashSet

Uygulamalarımızda kullandığımız zaman bizler için depolama görevini üstlenen, karma tablo yapılarından oluşan ve bu tablo üzerinde verilerimizi **unique** yapıda **hashcode** değerler ile saklayan bir yapıdır.HashSet yapısı gereği girilen verileri **düzensiz** bir şekilde **sıralamaya** tabi tutar, böylelikle yapının performansını arttırır. Görsel üzerinde **index** bölümü oluşturmuş olmama rağmen HashSet yapıları verilerin index erişimine izin **vermemektedir** fakat yapı içerisinde bulunan ilk ve son elemana doğrudan erişim sağlayabiliriz.

### Özellikleri
-   HashSet yapılarını oluşturduğumuz zaman varsayılan  **kapasitesi**  16 olarak oluşur ve bu oluşan yapının  **yük faktörü**  0,75 olur.
-   İçerisinde  **null**  veri saklamamıza izin verir.
-   Yapı içerisine eklediğimiz verileri  **hashing**  adı verilen bir mekanizma kullanarak depolar.
-   **Senkronize**  bir yapısı bulunmaz.
-   İçerisine eklediğimiz veriler tamamen  **benzersiz**  yapıda olmak zorundadır.





