set title "Hello"
get title

append title " Redis"
//daha önceden oluşturulan title key değerine yeni " Redis" ekler

get title

strlen title
// title anahtarının değerinin uzunluğunu verir.

set website:stats:daily_visitors_log "100"
get website:stats:daily_visitors_log

append website:stats:daily_visitors_log "200"
get website:stats:daily_visitors_log


set website:stats:daily_visitors_log "100"
append website:stats:daily_visitors_log " 200"

get website:stats:daily_visitors_log

append website:stats:daily_visitors_log " 3000"
get website:stats:daily_visitors_log

##########################################################################


mset k1 v1 k2 v2 k3 v3
//key value çiftleri oluşturuldu

keys *
//bütün key değerleri yazdırıldı

mget k1 k2 k3
//yukarıdaki keylerin değerlerini döner.

msetnx k1 v10 k2 v2 k3 v3
//herhangi bir anahtar önceden ayarlanmışsa hata döner
get k1
//v1


##########################################################################


set key1 val1
get key1

getset key1 val1.2
//eski değeri döner fakat overwrite eder
get key1

keys *key2*
//içinde "key2" ifadesi bulunan keyler getirilir

getset key2 1
//nil

set app:daily_tokens 10
get app:daily_tokens

decr app:daily_tokens
//key değerini 1 azaltır

decr app:daily_tokens
decr app:daily_tokens

getset app:daily_tokens 10


##########################################################################


set website "KlickAnalytics.com"
get website

getrange website 0 1
//key değerine karşılık gelen string ifadenin ilk 2 karakterini(0.indeksten başlayarak 1.indekse kadar) getirir.

getrange website 0 0

getrange website 0 2
getrange website 0 3
--sıfır ve üçüncü indeksler arasındaki veriyi getirir.
getrange website 0 4
getrange website 5 13
getrange website 0 100

getrange website -1 0
//key değerine karşılık gelen string ifadenin ilk karakteri ve son karakteri arasındaki stringi getirir.

getrange website 15 17


eğer sondan başlayarak aralık belirtmek istersek son karakterin indeks numarası -1 dir.

getrange website -3 -1
//key değerine karşılık gelen string ifadenin son 3 karakterini getirir.

##########################################################################

set name "Hello World"
get name

setrange name 6 "Redis"
//key değerine karşılık gelen string ifadede 6.indeksten itibaren Redis dizgesini ekler. eğer 6.indekste halihazırda bir karakter varsa üzerine yazar.

strlen name

get name

setrange name 6 " Redis World"
setrange name2 6 " Wonderful world"

get name2

##########################################################################

set num 1
get num

<b><mark>expire num 10</mark></b><br>
//key değeri ve karşılık gelen string ifade 10 saniye sonra silinecek

ttl num
//time to left --> silinmesine ne kadar kaldığını gösterir.

setex num 120 1
//anahtara 1 değeri verir. 120 saniye sonra silinecek

ttl num

setex app:config:timeout 100 1
ttl app:config:timeout 

psetex num 10000 1
//anahtara 1 değeri atar. aynı zamanda anahtar 10.000 ms sonra silinir

ttl num

##########################################################################

set num1 100
get num1

keys *

setnx num1 200
//num1 anahtarı yoksa oluşturur ve 200 değeri atar
//num1 anahtarı zaten varsa hiç bir işlem yapmaz
keys *
get num1

setnx num2 200
get num2

setnx user:101:login_attempt 1
get user:101:login_attempt

##########################################################################


set mykey 123456
get mykey
object encoding mykey
//mykey adlı anahtarın türünü döndürür.

set mykey "test string"
object encoding mykey

strlen mykey
//anahtara karşılık gelen değerin uzunluğunu dönderir.

set mykey "this is a long string defined for redis databasae structure"
<b><mark>object encoding mykey</mark></b><br>
//mykey isimli anahtarın depolama türünü ve yapısı hakkında bilgi verir.


##########################################################################


Ayrıca string veri türünü kullanarak json veri oluşturulabilir.

set json '{"fname":"John","lname":"Doe"}'
get json













