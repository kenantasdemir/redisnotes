hset user:1 name sam age 15 city atlanta

hset user fname "John" lname "Doe"
//user isimli bir hash oluşturur. bu hash içinde 2 field vardır. fname ve lname

hget user fname
//user isimli hash içindeki fname field verisinin değerini yazdırdık.

hget user lname
//user isimli hash içindeki lname field verisinin değerini yazdırdık.

hgetall user
//user isimli hash içindeki bütün fieldların değerini verir.

hset user age 40
//user isimli hash içine yeni field tanımı yapıldı.

hgetall user
//tekrardan hash içindeki fieldların değerine erişildi.

hset user status 1
//user isimli hash içerisine status isimli field eklendi. bu fieldın değeri 1 olarak ayarlandı.

hgetall user
//user isimli hash içerisindeki bütün fieldların değeri alındı.

hset user age 35

hgetall user

hget user age
hgetall user

#############################################################################################3


hgetall user

rename user user:101
//user isimli hash, user:101 olarak yeniden adlandırıldı.

hgetall user:101

hmget user:101 fname lname
//hmget ile user:101 isimli hash içind birden fazla fieldı tek seferde getirebilmiş olduk.

hmget user:101 age fname


<b><mark>hlen user:101</mark></b><br>
//user:101 isimli hashin içindeki field sayısını verir.

hgetall user:101

hgetall user:101


hmset user:101 f1 v1 f2 v2
//user:101 içindeki hash yapısına ardışıl olarak key-value çiftleri eklendi.


hgetall user:101

<b><mark>hdel user:101 f2</mark></b><br>
//user:101 isimli hash içerisindeki f2 isimli fieldı ve değerini siler

hgetall user:101


hdel user:101 f1 f2
//birden fazla alanı aynı anda silmek istersek field isimlerini girmemiz yeterli

hgetall user:101

#############################################################################################3

hgetall user:101

hexists user:101 fname
//user:101 isimli hash içinde fname isimli field var mı kontrol ettik. varsa true yoksa false

hexists user:101 fname1

hmget user:101 fname lname

hexists user:101 name
//name fieldı var mı yok mu kontrol eder
//varsa true yoksa false döner

#############################################################################################3

hgetall user:101

hkeys user:101
//user:101 hash yapısı içerisinde bulunan keyleri verir.

hvals user:101
//user:101 hash yapısı içerisinde bulunan keylerin değerlerini verir.

#############################################################################################3

hset user:101 score 10

hincrby user:101 score 10
//user:101 isimli hash yapısında score fieldının değerini 10 arttırır.

hincrby user:101 score -10
//user:101 isimli hash yapısında score fieldının değerini 10 azaltır.


hset user:101 commission 0.25

hincrbyfloat user:101 commission 1.2
//user:101 hash yapısı içerisinde commission değeri 1.2 arttırıldı.

hincrbyfloat user:101 commission -1.2
//user:101 hash yapısı içerisinde commission değeri -1.2 azaltıldı.

hgetall user:101

#############################################################################################3

<b><mark>hsetnx user:101 fname "John2"</mark></b><br>
//eğer user:101 isimli hash yapısında fname fieldı varsa eklemez. yoksa ekler.

hsetnx user:101 f1 v1
//if it doesnt exists

hgetall user:101


#############################################################################################3


hrandfield user:101
//user:101 isimli hash içeriisnden rastgele veri getirir.

hrandfield user:101 1
//user:101 isimli hash içerisinden 1 tane field getirilir.

<b><mark>hrandfield user:101 2</mark></b><br>
//pozitif tam sayı verilirse getirilen alanlar mutlaka farklı olmalıdır

hrandfield user:101 -2
//getirilen alanlar aynı olabilir


hrandfield user:101 2 withvalues
//user:101 isimli hash içerisinden 2 adet farklı fieldı değerleriyle birlikte getirir.

hrandfield user:101 -2 withvalues
//user:101 isimli hash içerisinden 2 adet fieldı değerleriyle birlikte getirir.

keys user:101
//user:101 içerisindeki bütün keyleri listeleriz.

hkeys user:101
//user:101 isimli hash içerisindeki field bilgilerini getirir.



NX
XX
GT
LT

--  HEXPIREAT
<b><mark>HEXPIREAT user 42354353452 NX FIELDS 2 name city</mark></b><br>

<b><mark>HEXPIRETIME mykey FIELDS 2 field1 field2</mark><br>
HMSET myhash field1 "Hello" field2 "World"

<b><mark>HPERSIST mykey FIELDS 1 field2</mark></b><br>

<b><mark>HPEXPIRE mykey 2000 FIELDS 2 field1 field2</mark></b><br>
--ms cinsinden

<b><mark>HPEXPIREAT mykey 1715704971000 FIELDS 2 field1 field2</mark></b><br>
<b><mark>HPTTL mykey FIELDS 2 field1 field2</mark></b><br>
<b><mark>HPEXPIRETIME mykey FIELDS 2 field1 field2</mark></b><br>


HSCAN myhash 0 NOVALUES

<b><mark>HSTRLEN myhash f1</mark></b><br>

<b><mark>HTTL mykey FIELDS 3 field1 field2 field3</mark></b><br>


Redis'teki scan komutları, verileri küçük 
parçalara böler ve her seferinde sadece bir 
kısmını döndürür, 
bu da veritabanı üzerinde daha düşük yük 
oluşturur.












