set hello 1
set hello1 "test"
object refcount hello

 belirtilen anahtarın değerine ait referans sayısını (reference count) döndürür.

Redis'te, her anahtar için değerine referans sayısı atanır. Bu referans sayısı, anahtarı kullanan tüm bağlantı noktaları ve işlemler için tutulur. 
Anahtarın referans sayısı, belirli bir anahtarın kaç kez referans aldığını gösterir. 
Örneğin, bir anahtarın referans sayısı 3 ise, o anahtarın 3 farklı yerde kullanıldığı anlamına gelir.

OBJECT REFCOUNT komutu, belirtilen anahtarın referans sayısını döndürür. 
Örneğin, OBJECT REFCOUNT hello komutu, hello adlı bir anahtarın referans sayısını döndürür. 
Bu, hello anahtarının kaç kez referans alındığını ve kaç bağlantı noktası veya işlem tarafından kullanıldığını gösterir.

Bu komut, Redis içindeki bellek yönetimini anlamak ve performansı iyileştirmek için kullanışlıdır. 
Özellikle, çok fazla referans sayısına sahip anahtarları tespit etmek ve gereksiz bellek kullanımını önlemek için kullanışlıdır.

<b><mark>object refcount hello1</mark></b><br>

object encoding hello
//hello adlı anahtarın tuttuğu değerin türünü döner.
//bu örnekte hello anahtarı 1 değerini tutar. yani int

<b><mark>object encoding hello1</mark></b><br>

<b><mark>object idletime hello</mark></b><br>
belirtilen anahtarın son kullanımından itibaren ne kadar süredir kullanılmadığını döndürür.

Redis, bellek yönetimi için bir tembellik (idling) mekanizması kullanır. Bir anahtarın son kullanımından itibaren belli bir süre geçtikten sonra, 
Redis bellekten bu anahtarı kaldırır. OBJECT IDLETIME komutu, bir anahtarın son kullanımından bu yana geçen süreyi döndürür. 
Bu, bir anahtarın ne kadar süredir kullanılmadığını gösterir ve bellek yönetimini anlamak için kullanışlıdır.

Örneğin, OBJECT IDLETIME hello komutu, hello adlı bir anahtarın son kullanımından bu yana geçen süreyi döndürür. 
Eğer bu süre, Redis'in konfigürasyon dosyasındaki timeout ayarından daha fazla ise, Redis bu anahtarı bellekten kaldırır.

Bu komut, Redis'in bellek yönetimini anlamak ve gereksiz bellek kullanımını önlemek için kullanışlıdır. 
Özellikle, uzun süre kullanılmayan anahtarları tespit etmek ve gereksiz bellek kullanımını önlemek için kullanışlıdır.

object idletime hello1

lpush fruits "banana"
object refcount fruits
object encoding fruits
object idletime fruits


####################################################################################

set name "Joe"

get name

<b><mark>dump name</mark></b><br>

<b><mark>restore name 0 <paste code for key: name ></mark></b><br>

get name

del name

restore name 0 <paste code for key: name >

get name

info

####################################################################################

		----Redis Komut Geçmişi---

cd ~
pwd
ls

ls -lrta

<b><mark>tail -10 .rediscli_history</mark></b><br>



####################################################################################

set name1 1

set name2 2

set name3 e

set name4 4

debug populate 50

redis-cli --scan
//bütün keyleri verir.

redis-cli --scan --pattern '*'
//bütün keyleri verir.

redis-cli --scan --pattern 'k*'
//k ile başlayan keyleri verir.

redis-cli --scan --pattern '*key*'
//içinde key ifadesi geçen keyleri listeler

redis-cli --scan --pattern '*name*'
//içinde name ifadesi geçen keyleri listeler

redis-cli --scan --pattern '*' > keys.csv
//bütün keyleri keys.csv dosyasına yazar.

cat keys.csv

redis-cli -h


####################################################################################s


debug populate 50
keys *

redis-cli get mypasswd

redis-cli --scan --pattern '*key*'
redis-cli --scan --pattern '*key*' > keys.csv

####################################################################################


CODE: Dump and Restore Keys
set name "Joe"

get name

dump name

belirtilen anahtarın değerini, Redis'in dahili protokolü kullanarak, bir dize (string) olarak döndürür.

Bu komut, bir anahtarın değerini yedeklemek ve başka bir yerde yeniden kullanmak için kullanışlıdır. 
Örneğin, DUMP name komutu, name adlı bir anahtarın değerini bir dize olarak döndürür. 
Daha sonra, bu dizeyi başka bir Redis sunucusuna veya başka bir yerdeki başka bir programda kullanarak, name anahtarının değerini geri yükleyebilirsiniz.

DUMP komutunun çıktısı, Redis protokolünü kullanan özel bir dizedir. Bu dize, RESTORE komutu kullanılarak yeniden yüklenebilir. 
RESTORE komutu, DUMP komutu tarafından üretilen özel bir dizeyi alır ve onu belirtilen bir anahtarın değeri olarak atar.

Bu komut, Redis'te yedekleme ve geri yükleme işlemleri yapmak için kullanışlıdır. 
Ancak, çok büyük anahtar değerleri için yavaş çalışabilir ve bu nedenle, çok büyük verileri yedeklemede tercih edilmeyebilir.

restore name 0 <paste code for key: name >

get name

del name

restore name 0 <paste code for key: name >

get name

info


set name "Joe"
get name

dump name
"\x00\x03Joe\n\x00\xdcQY\xaa\x02\xc7\xfd("
restore name2 0 "\x00\x03Joe\n\x00\xdcQY\xaa\x02\xc7\xfd("
0 = expire yok


set isim "John"
get isim

dump isim
restore isim 0 "\x00\x04John\n\x00S\xe8\xb7Y\xc1\x8bt\x18" REPLACE
info

*********************************************************************


redis-cli --scan

vi readkeys.sh
#!/bin/bash
redis-cli --scan
:wq
readkeys.sh
chmod 755 readkeys.sh
./readkeys.sh


vi readkeys.sh
#!/bin/bash
redis-cli --scan > all.keys
:wq
./readkeys.sh
cat all.keys


vi readkeys.sh
#!/bin/bash
redis-cli --scan > all.keys
while read -r key
do
   value=$(redis-cli get "$key")
   echo $key '|' $value
done < all.keys
:wq
./readkeys.sh

#!/bin/bash
redis-cli --scan > all.keys
while read -r key
do
  value=$(redis-cli get "$key")
  echo $key '|' $value
done < all.keys



#################################################################################################################

CODE: Using URL, echo to list all keys

URL=redis://localhost:6379
echo "KEYS *" | \
redis-cli -u $URL | \
sed 's/^/GET /' | \
redis-cli -u $URL





set name1 1

set name2 2

set name3 e

set name4 4

debug populate 50

redis-cli --scan

redis-cli --scan --pattern '*'

redis-cli --scan --pattern 'k*'

redis-cli --scan --pattern '*key*'

redis-cli --scan --pattern '*name*'

redis-cli --scan --pattern '*' > keys.csv

cat keys.csv

redis-cli -h

#################################################################################################################



URL=redis://localhost:6379

echo "KEYS *" | \

redis-cli -u $URL | \

sed 's/^/GET /' | \

redis-cli -u $URL

#################################################################################################################


creating replicas

<b><mark>redis-cli --cluster create 127.0.0.1:7001 127.0.0.1:7002 127.0.0.1:7003 
127.0.0.1:7004 127.0.0.1:7005 127.0.0.1:7006 --cluster-replicas 1</mark></b><br>

#################################################################################################################


<b><mark>redis-cli --cluster check 127.0.0.1:7001</mark></b><br>

<b><mark>redis-cli -p 7001 cluster</mark></b><br>

<b><mark>redis-cli -p 7001 cluster nodes</mark></b><br>

exists fname lname

set 1  hello ex 120

ttl 1

expire 1 10

ttl 1

set 1 hello px 1000

ttl 1

pttl 1

get 1

set 1 hello px 100000

pttl 1

ttl 1

expire 1 10

set 1 hello px 1000000

pttl 1

<b><mark>pexpire 1 100</mark></b><br>

pttl 1



set k1 v1

set k2 v2

get k1

get k2

<b><mark>renamenx k1 k2</mark></b><br>

get k1

get k2

renamenx k1 k3

get k1

get k3

CODE: Deleting Keys Asynchronously via UNLINK
set k1 v1

set k2 v2

del k1 k2

set k1 v1

set k2 v2

<b><mark>unlink k1 k2</mark></b><br>
































