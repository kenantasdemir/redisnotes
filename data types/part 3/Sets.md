sadd cars toyota maserati ford
//cars isimli bir set oluşturur ve içine toyota maserati v ford elemanlarını ekler

sadd cars mazda

smembers cars
//cars isimli set verisin elemanlarını listeler.

sadd names Rob Robby Rim John
smembers names

sadd numbers 1 2 3 4 5 6
smembers numbers

**********************************************************************

scard cars
smembers cars

scard numbers
smembers numbers

sadd unique_ips 1.1.1.0
smembers unique_ips

sadd amazon:unique_categories electronics computers
smembers amazon:unique_categories

sadd amazon:unique_categories handmade gardening outdoor sports
smembers amazon:unique_categories

sadd twitter:hashtags help money training coding database
smembers twitter:hashtags


**********************************************************************

sadd subjects math
smembers subjects
sadd subjects english science physics
smembers subjects

sadd subjects bingo
semembers subjects

srem subjects bingo
//subjects isimli set veri yapısının içinden bingo isimli elemanı siler

spop subjects
//random eleman siler

<b><mark>spop subjects 2 </mark></b><br>
//set içinden 2 random eleman siler


**********************************************************************


smembers cars
sismember cars ford
//cars içinde ford isimli bir eleman var mı yok mu kontrol eder varsa true yoksa false döner

sismember cars FORD
//case-sensitive

sadd subjects math ai english
sismember subjects english
sismember subjects ai

smembers subjects

smismember subjects math ai technology
//math ai ve technology elemanllarının subjects isimli kümede bulunup bulunmadığını kontrol eder
//sismember komutundan farkı birden fazla elemanı tek seferde kontrol etmemize imkan tanımasıdır.

,
*********************************************************************

sadd unique_lottery_num 10 20 30 40 50
smembers unique_lottery_num

srandmember unique_lottery_num

<b><mark>srandmember unique_lottery_num 2</mark></b><br>
//unique_lottery isimli kümeden rastgele 2 eleman getirir.

*********************************************************************

sadd num:odd 1 3 5 7 9
sadd num:even 2 4 6 8 10

smembers num:odd
smembers num:even

smove num:odd num:even 1
smove num:odd num:even 3

<b><mark>smove num:odd num:even 5</mark></b><br>
//num:odd kümesindeki elemanı num:even kümesine taşır
//bu kullanımda 5 sayısı num:odd kümesi içindedir fakat bu komut ile num:even kümesine taşınmış oldu.

*********************************************************************


sadd num1 1 2 3 4 5
sadd num2 2 4 6 8 10

smembers num1
smembers num2

sunion num1 num2
//belirtilen num1 ve num2 kümelerinin birleşimini gösterir.

sunionstore all_num num1 num2
//belirtilen num1 ve num2 kümelerinin birleşimini all_num isimli yeni bir kümede saklar.
//num2 adlı set yapısı silinir.

smembers all_num


*********************************************************************


sadd k1 a b c d
sadd k2 c
sadd k3 a c e

sinter k1 k2 k3
//k1 k2 ve k3 anahtarlarındaki kesişim kümesini gösterir.

sinterstore sum k1 k2 k3
//k1 k2 ve k3 anahtarlarındaki kesişim kümesini sum isimli yeni bir küme içinde saklar
//diğer set yapıları korunur.

smembers sum


*********************************************************************

sadd k1 a b c d
sadd k2 c
sadd k3 a c e

sdiff k1 k2 k3
//k1 k2 ve k3 key değerleri arasındaki farlılıkları gösterir.
//k1 elemanında olup k2 ve k3te olmayanları görüntüler.


sdiffstore sum k1 k2 k3
//k1 k2 ve k3 anahtarları arasındaki farkları sum isimli yeni bir set veri yapısı içinde saklar
//k1 de olup k2 ve k3de olmayan elemanları sum isimli sete ekler.



SDIFF key1 key2
--Key1de olup key2de olmayan elemanları listeler.


SINTER key1 key2
--key1 ve key2 anahtarları üzerinde kesişen elemanları listeler.

<b><mark>SINTERCARD 2 key1 key2</mark></b><br>
--2 anahtarın kesişen elemanlarının sayısını döndürür.

SINTERSTORE key key1 key2
--kesişen elemanları key adlı anahtarda saklar

SISMEMBER myset "one"

SMEMBERS key

SMISMEMBER myset "one" "notamember"

SMOVE myset myotherset "two"

SPOP myset
--random eleman siler

SPOP myset 3
--random 3 eleman siler.

SRANDMEMBER myset
--random eleman Döner

SRANDMEMBER myset 3
--random 3 eleman Döner

SREM myset "one"

SUNION key1 key2
--key1 ve key2 adlı anahtarlar üzerindeki elemanları duplicate eleman olmadan birleştirir.

SUNIONSTORE key key1 key2
--key1 ve key2 adlı anahtarlar üzerindeki elemanları duplicate eleman olmadan birleştirir ve key adlı anahtara yazar.

































































































