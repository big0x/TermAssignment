
# LinkedList

Java Linked List, oluşumlarında node (düğüm) ismi verilen bir elemanda verilerini kayıt altına alan ve bu verileri RAM üzerinde tutan özel bir veri saklama yapısıdır. Hafızada verileri tutma şekli olarak dizilere benzese bile aralarında önemli ölçüde performans farkı mevcuttur. 

## LinkedList Metotları

  - Add (parametre) ve Add (indis numarası, parametre)
  Tanımlamış olduğumuz Linked List yapımıza  iki türde veri eklemesi gerçekleştirebiliriz. Bunlardan ilkinde  bir sonraki indise  veri eklerken, bir diğerinde  belirtilen indis numarasına  ekleme işlemi gerçekleştirir.


```java
		LinkedList<String> cars = new LinkedList<String>();
		    cars.add("Volvo");
		    cars.add("BMW");
		    cars.add("Ford");
		    cars.add("Mazda");
```
-   **AddLast(parametre) ve AddFirst(parametre):**  Linked List yapımızın içerisinde başına ve sonuna almış olduğu parametreyi eklemek istediğimiz zaman kullanacağımız metot yapılarıdır.
-   **Remove(parametre):**  Parametre olarak aldığı  indis numarasını  ya da  veriyi  liste üzerinde arar ve bulduğu takdirde veriyi siler.
-   **RemoveLast() ve RemoveFirst():**  Bu metot yapımız listemizin başında ya da sonunda bulunan değeri silmek için kullanılır.
-   **Get(parametre), getLast() ve getFirst():**  Get metodu almış olduğu parametre değerindeki  indis numarasına  giderek orada bulunan veriyi getirir.  *GetLast*  ve  *GetFirst*  metotları ise başlangıç indisini ve listenin son indisinden verileri getirmeye yarar.
- **Clear():** Liste yapımızın içeriğin komple temizlemek istediğimiz zaman kullanabileceğimiz bir metot.
- **Count:** Liste yapımız içerisinde bulunan toplam eleman sayısının bilgisini bizlere veren metot.
-   **Contains(parametre):**  Parametre olarak almış olduğu değeri liste üzerinde arar. Eğer liste üzerinde belirtilen parametre değeri varsa “*true*” yoksa “*false*” değerini döndürür.
-   **Sort():**  *Collections kütüphanesi*  içerisinde yer alan bu metodumuz liste içerisindeki verileri  küçükten büyüğe  doğru sıralar.
-   **Size():**  Listemizin içerisinde bulunan  eleman sayısını  bize geri değer olarak döndüren metodumuz.
-   **toArray():**  Liste yapımızın elemanlarının  birer kopyasını içeren  bir dizi döndürür. Bazı işlemlerin daha hızlı bir şekilde gerçekleşmesi ya da veri aktarımının sağlanması için kullanılan metottur.
-   **lastIndexOf(parametre):**  Parametre olarak aldığı veriyi liste yapının içerisinde en son gördüğü  indis numarasını  geri döndürür. Eğer parametredeki değer liste içerisinde bulunmuyorsa geriye  *-1* değerini  döndürür.

## Avantajları ve Dezavantajları

**Java Linked List Avantajları**, içerisinde yer alan veriler ile birlikte hafızayı dinamik bir şekilde kullanmasıdır. Bu sayede hafızadan silinecek bir veri için hafıza üzerinde alan boşaltacak veya yeni eklenecek bir veri için sadece eklenecek veriye yetecek kadar hafıza üzerinde yer kaplayacaktır.

Böylelikle programlarımıza esneklik ve dinamiklik katacaktır.

**Java Linked List Dezavantajları**, ulaşılmak istenilen rastgele bir veriye ulaşmanın maliyeti normal bir dizi sistemine göre daha çok maliyetlidir. Düğüm yapılarının etkisiyle dizilere göre hafızada daha fazla yer kaplar.

Bunun sonucunda dizi yapılarının programımıza yüklediği yükün daha fazlasını Linked List kullanarak sağlamış oluruz.

### ArrayList ve LinkedList
ArrayList sınıfının içinde düzenli bir dizi bulunur. Bir eleman eklendiğinde, diziye yerleştirilir. Dizi yeterince büyük değilse, eskisinin yerine yeni, daha büyük bir dizi oluşturulur ve eski dizi kaldırılır.

LinkedList, öğelerini "containers" da  saklar.  Listede ilk containera bir bağlantı bulunur ve hercontainer listedeki bir sonraki containera bir bağlantı içerir.  Listeye bir eleman eklemek için eleman yeni bir containera yerleştirilir ve bu container listedeki diğer containerlar ile birine bağlanır.

>==**Verileri depolamak ve bunlara erişmek için "ArrayList"**==

>==**Verileri işlemek için "LinkedList"**==
