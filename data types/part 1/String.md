redis te tablo yapısı yok


string, list, hashes ,sets ,sorted sets

strings binary, so we can store any data type

•Sring is the basic but powerful data structure in Redis
•Strings are binary safe, so we can store any data type
•Strings can be used as generic data storage
•If our data does not fit in any of other Redis data type, we can store
the data into string data type
•We can serialize ANY TYPE OF DATA toastring
•String can behave as random access vector too
•Large amount of data can be encoded into small spaces in string
•Maksiumum string boyutu 512 MBdir.

Plain Strings
•Serving static contents like static website pages
•Redis.io website uses Redis database itself to serve all static pages

Caching
•Frequently used data can be cached into string
•With the help of expiry, set commands caching can be possible


<b><mark>set otp:use_100 12345 ex 120</mark></b><br>
//120 saniye sonra expired olacak
get otp:user_100
ttl otp:user_100
type otp:use_100
ttl otp:user_100

Counters
•Srings can be used to store stats
•Daily user visits, website stats and more

Master catalog/Configurations
•Store application configurations, and master catalogs
•app:config:title, config:countriesname, config: usertypes

set app:stats:daily_visitors 1000
get app:stats:daily_visitors

set app:config:title "KlickAnalytics"
get app:config:title

set app:users:types "Billable,Free"

set app:config::usertimeout 100000


##################################################

set app_message "asas"
//app_message isimli string oluşturur

del app_message
//app_message isimli stringi siler

keys *
//bütün stringleri döner

clear
//terminal ekranını temizler


set app:config:title "KlickAnalytics"
get app:config:title
//oluşturulan string verinin değerini elde eder.

set app:config:url "http://klickanalytics.com"
keys *
//bütün anahtarları döndürür.


set app:config:greetings "welcome to KlickAnalytics.com"
keys *


set shop:101:name "Pizza Store"
keys *

set shop:101:location "123 Broadway"
set shop:101:country "USA"
keys *

keys shop*
//isminde shop geçen stringlerin anahtarları döndürür.

get shop:101:name


<b><mark>Setex mykey 30 "hello world"</mark></b><br>
//30 saniye sonra expired olacak mykey adlı string oluşturur.

<b><mark>Getex mykey ex 60</mark></b><br>
//bir anahtarın değerini elde ederken expired olma süresini de değiştirdik.

<b><mark>Getex mykey px 60</mark></b><br>

<b><mark>SUBSTR mycustomkey 0 -1</mark></b><br>

<b><mark>GETRANGE key 0 -1</mark></b><br>

<b><mark>GETDEL mykey</mark></b><br>
//mykey adlı stringin değerini yazdırdıktan sonra siler.

<b><mark></mark></b><br>
//mycounter değerini önce get sonra set eder.

<b><mark>APPEND mykey "15"</mark></b><br>
//stringin sonuna ifade ekler
EXISTS mykey

SET sayi "20"
DECR sayi
DECRBY sayi 3

INCR sayi
INCRBY sayi 5



MSET key1 ohmytext key2 mynewtext
LCS key1 key2
//verilen iki string içinde birbirine benzeyen alt stringleri döner

<b><mark>LCS key1 key2 LEN</mark></b><br>
//birbirine benzeyen karakter sayısını döner

MGET key1 key2
MSET key1 "Cello" key2 "World"

MSETNX key1 "Hello" key2 "there"
PSETEX mykey 100000 "deneme"
PTTL mykey

//PSETEX, bir anahtarın değerini belirler ve bu anahtara milisaniye cinsinden bir süre tanımlar. 
//Süre dolduğunda anahtar otomatik olarak silinir.


SETNX key value
(Set if Not Exists)



































