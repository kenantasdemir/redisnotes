lpush dept "Sales"
//dept isimli listenin soluna "Sales" elemanı eklendi

lpush dept "Admin" "HR"
//dept isimli listenin soluna "Admin" ve "HR" eklendi

keys *
get dept
//listelere klasik veri yapılarından farklı olarak bu şekilde ulaşılamaz.

//liste veri tüürndeki yapılara ulaşmak için bu komut kullanılabilir.
scan 0 match * type list count 5
//tipi liste olan yapılardan 5 tanesi getirilecektir.


herhangi bir anahtarın türünü öğrenmek için type ardından da o anahtarın adını girmelisiniz.
type dept



lrange dept 0 -1
//dept isimli listenin tüm elemanlarını yazdırır.
//-1 son eleman anlamına gelir

lpush dept programming

lrange dept 0 -1

rpush dept "Marketing"
//dept isimli listenin sağına "Marketing" elemanını ekler

lrange dept 0 -1
//listenin elemanlarını yazdırır.

lrange dept 1 -1
//1.indeksten başlayarak sonra indekse kadar ki elemanları yazdırır.

lrange dept -3 -1
//dept isimli listenin son 3 elemanını getirir.

lrange dept 0 -1

---

<b><mark>lindex dept 0</mark></b><br>
//dept isimli listenin 0.indeksindeki elemanı getirir.

lindex dept 1
lindex dept 2

lindex dept -1
lindex dept -2
lindex dept 10
//nil
//eğer olmayan bir indeksi almaya çalışırsak nild döner

lindex dept -10
//nil

lpush MSFT:close_prices 10 10.20 11.00 20.00
//MSFT:close_prices isimli listeye çoklu eleman ekleme


lrange MSFT:close_prices 0 -1

lindex MSFT:close_prices -1
//listenin son elemanını verir.

lindex MSFT:close_prices 0
//listenin ilk elemanını verir

del MSFT:close_prices
//listeyi siler

rpush MSFT:close_prices 10 10.20 15.00
lrange MSFT:close_prices 0 -1


lindex MSFT:close_prices -1
lindex MSFT:close_prices -2
//listenin sondan bir önceki elemanını verir.


######################################################################################

lrange dept 0 -1

<b><mark>linsert dept before "Admin" "Legal"</mark></b><br>
//dept isimli listede Legal değerini Admin değerinden önce eklemek için kullanılır.<br>

lrange dept 0 -1

linsert dept before 0 "Test"
//-1 (eklemedi)


<b><mark>linsert dept after "Sales" "Social"</mark></b><br>
//dept isimli listede Sales değerinden sonra Social elemanını eklemek için kullanılır.

lrange dept 0 -1


######################################################################################

lpush num 1 2 3 4 5 6 7 8 9 10
lrange num 0 -1

//del num listedeki elemanları siler

lpop num
//num listesindeki ilk elemanı siler

lrange num 0 -1

rpop num
//num listesindeki son elemanı siler

lrange num 0 -1

lpop num 2
//num isimli listenin solundan 2 eleman çıkarır ve ekrana çıkarılan elemanları yazdırır.

rpop num 1

lrange num 0 -1


######################################################################################

lpush num 1 2 3 4 5 6 7 8 9 10
lrange num 0 -1

ltrim num 0 -1
lrange num 0 -1

ltrim num 1 -1
//en son eklenen 1 elemanı siler
lrange num 0 -1

ltrim num 2 -1
//en son eklenen 2 elemanı siler
lrange num 0 -1

---

rpush num 1 2 3 4 5

lrange num 0 -1

<b><mark>lset num 2 30</mark></</b><br>
//num isimli listede 2.indeksteki elemanın değerini 30 olarak değiştirir.

lrange num 0 -1

lset num 4 50
lrange num 0 -1

lset num -1 50
//num isimli listenin sonuncu elemanı 50 olarak değiştirir.

lset num -1 100
lrange num 0 -1


lset num 100 199
//index out of range


######################################################################################


rpush app:config:lst_supported_lang "English" "Japanese" "Arabic" "Chinese"
lrange app:config:lst_supported_lang 0 -1

llen app:config:lst_supported_lang
//listedeki eleman sayısını döndürür.



######################################################################################


rpush mykey a b a a c d e f a
lrange mykey 0 -1

<b><mark>lpos mykey "a"</mark></b><br>
//listedeki "a" elemanın konumunu verir.

lpos mykey "a" rank 1
lpos mykey "a" rank 2
lpos mykey "a" rank 3

lpos mykey "a" rank -1
//"a" öğesinin sonuncu sıradaki pozisyonunu bulmak için kullanılır. bulursa konumunu verir bulamazsa -1 döndürür.

<b><mark>lpos mykey "a" count 0</mark></b></br>
//aranan öğenin kaç adet bulunacağını sınırlandırır<br>
//boş liste döner

lpos mykey "a" count 1
lpos mykey "a" count 2
//mykey adlı listeden tekrar eden 2 tane "a" elemanının indeksini döndürür.
lpos mykey "a" count 3
lpos mykey "a" count 4
lpos mykey "a" count 5

lpos mykey "a" rank 1 count 0
//count 0 parametresi verildiği için tüm listenin taranması gerekir
//rank 1 ile "a" karakterinin listenin sıralamasına göre kaçıncı sırada olduğunu verir.

lpos mykey "a" rank -1 count 0
///-1.indeksten başlayarak tarar.
//count: sıralama pozisyonundan itibaren aranacak eleman sayısı, burada 0 sadece sıralama pozisyonunu döndüreceği anlamına gelir.

lpos mykey "a" rank -1 count 1
lpos mykey "a" rank -1 count 2

lpos mykey "a" rank 1 count 2 maxlen 1
//1.indeksten başlayarak 2 adet elemanı arar.
//maxlen değeri 1 verildiği için listenin ilk elemanı kontrol edilecektir.

lpos mykey "a" rank 1 count 0 maxlen 5000

######################################################################################33

rpush mykey "one" "one" "two" "three" "one"
lrange mykey 0 -1

<b><mark>lrem mykey 0 "two"</mark></b><br>
//0 indeksten tarayarak two elemanını bulur.
//listedeki two elemanını siler.
//silinen eleman sayısını döner

lrange mykey 0 -1

lrem mykey 1 "one"
lrange mykey 0 -1

rpush mykey "five"
lrange mykey 0 -1

lrem mykey -1 "one"
lrange mykey 0 -1

######################################################################################

rpush jobs:pending "job1" "job2" "job3"
lrange jobs:pending 0 -1

<b><mark>lmove jobs:pending jobs:completed left right</mark></b><br>
//jobs:pending listesinin ilk elemanını jobs:completed listesinin en başına taşır
//jobs:completed listesinin en sondaki elemanını jobs:completed listesinin sonuna taşır

lrange jobs:pending 0 -1
lrange jobs:completed 0 -1
 
lmove jobs:pending jobs:completed left right
lrange jobs:pending 0 -1
lrange jobs:completed 0 -1

lmove jobs:pending jobs:completed left left
//jobs:pending listesinin ilk elemanını jobs:completed listesinin en başına taşır
//jobs:completed listesinin ilk elemanını jobs:completed listesinin en başına taşır
lrange jobs:pending 0 -1
lrange jobs:completed 0 -1

xxxx

rpush orders:pending 1 2 3 4 5

lmove orders:pending orders:completed left right
lrange orders:pending 0 -1
lrange orders:completed 0 -1

lmove orders:pending orders:completed right left
lrange orders:pending 0 -1
lrange orders:completed 0 -1

---

LPOP mylist
//soldan ilk elemanı silver

LPOP mylist 2
Soldat iki elemanı siler



LREM list -2 "hello"
--listenin sonundaki 2 "hello" ifadesiini siler.

LTRIM mylist 1 -1
-- 1.indeksteki eleman ve son eleman arasındaki elemanları saklar geri kalanı siler
-- bu örnekte 0.indeksteki eleman silinecek

RPUSH mylist "one" "two" "three" "four" "five"
RPOP mylist

RPOP mylist 2
<b><mark>RPOPLPUSH mylist myotherlist</mark></b><br>
//source listenin sağından bir eleman çıkarır ve destination listenin soluna ekler.


LPUSHX myotherlist "Hello"
//liste varsa ekler

RPUSHX myotherlist "World"
--liste Hali hazırda mevcut ise çalışır


















