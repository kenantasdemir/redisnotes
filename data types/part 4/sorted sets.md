zadd user:followers 10 adam 20 scott 30 amy
//user:followers isimli sıralı küme yapısına yukarıdaki elemanları ekler

XX listede olan elemanları günceller.yeni eleman eklemez
NX listeye yeni eleman ekler. güncelleme yapmaz

zrange users:followers 0 -1
//sıralı kümedeki elemanları baştan sona yazdırır
//0 ilk indeks -1 ise son indekstir.

zrange users:followers 0 -1 withscores
//elemanları score değerleriyle birlikte listeler.

************************************************************************************************

zadd users:followers 1 John 100 David
zrange users:followers 0 -1 withscores

zrange users 0 0
//0.indeksten itibaren 0.indekse kadar olan elemanları görüntüler.
//yani ilk elemanı verir

zrange users -1 -1
//son elemanı verir.

zrange users 0 0 rev
//son elemanı verir
//normalde zrange users 0 0 ilk elemanı verir. fakat rev parametresi reverse sıralama yapar.

zrevrange users:followers 0 -1
//zrevrange komutuyla elemanları sondan başlayarak listelenir

zrevrange users:followers 0 -1 withscores
//zrevrange komutuyla elemanları sondan başlayarak skorlarıyala birlikte listeler

************************************************************************************************

zincrby users:followers 5 adam
//zincrby komutu bir elemanın score bilgisini arttırmak için kullanılır (15 adam)

zrange users:followers 0 -1 withscores

zincrby users:followers -5 scott
//negatif değer verildği için elemanın değeri azaltılacaktır(10 adam)

zrange users:followers 0 -1 withscores

zincrby users:followers 5 hans
//elemanın skoru 5 arttırılır ve küme içindeki yeri değişir.

zrange users:followers 0 -1 withscores


************************************************************************************************4
Lexicographical order

zadd num1:ss 1 a 2 b 3 c 3 d
zrange num1:ss 0 -1 withscores

zadd num2:ss 1 a 2 b 3 c 4 c
zrange num2:ss 0 -1 withscores

zadd num3:ss 1 a 2 b 3 c 4 ca
zrange num3:ss 0 -1 withscores

zrevrange num3:ss 0 -1 withscores
//zrevrange komutu tersten sıralama yapar.

************************************************************************************************4
//rank starts with 0


zadd stocks:top 1 AAPL 2 MSFT 3 F 4 QQQ 5 C 6 IBM 7 TSLA 8 AMZN 9 NIO 10 SPCE
zrange stocks:top 0 -1 withscores
zrevrange stocks:top 0 -1 withscores

zrank stocks:top AAPL
//stocks:top kümesinde AAPL elemanının indeksini döndürür.

zrank stocks:top MSFT
zrank stocks:top F

zrevrank stocks:top AAPL
//elemanları tersten sıralar.
//AAPL en başta olduğu için bu elemanı en sona atar

<b><mark>zunion 3 kume1 kume2 kume3</mark></b><br>
//3 kümeyi birleştirir.

<b><mark>ZUNIONSTORE birlesik_kume 3 kume1 kume2 kume3</mark></b><br>
//3 kümeyi birlştirir ve birlesik_kume içine aktarır.

************************************************************************************************

zrem kume1 armut muz
//kume1 isimli kümei içerisine armut ve muz isimli elemanları siler.

zinter 2 kume1 kume2
//kume1 ve kume2 isimli 2 elemanın kesişimini verir.

zinterstore kesisim_kume 2 kume1 kume2
//kume1 ve kume2 isimli 2 elemanın kesişimini kesisim_kume isismli kumeye aktarır.

zadd myset 1 val1
zadd myset 2 val2
zcard myset
//myset isimli sıralı küme içindeki eleman sayısını verir.

<b><mark>zcount mykume 1 15</mark></b><br>
//mykume isimli sıralı küme içinde 1.indeks ile 15.indeks arasındaki verileri getirir. 

zrandmember mykume
//mykume isimli sıralı listeden rastgele bir eleman getirir.


zrandmember mykume 5 withscores
//mykume isimli sıralı listeden rastgele 5 eleman skorlarıyla birlikte getirir.

************************************************************************************************

zadd mykume 1 "one"
<b><mark>zscore mykume "one"</mark></b><br>
//verilen elemanın skorunu verir.

<b><mark>zmscore mykume "one" "two" "three"</mark></b><br>
//verilen elemanların skor bilgisini verir.

zintercard 2 mykume1 mykume2
//mykume1 ve mykume2 isimli sıralı kümenin kesişen elemanların sayısını getirir.

zpopmax products
//products adlı bir sıralı kümeden en yüksek puanlı öğeyi kaldırır ve geri döndürür. Eğer kümede hiç eleman yoksa nil döndürür.

zpopmax mykume1 1
//mykume1 isimli kümeden en yüksek skora sahip elemanı kaldırır.


zpopmax mykume1 5
//mykume1 isimli kümeden en yüksek skora sahip 5 elemanı kaldırır.



ZCARD myzset

ZCOUNT mysortedset 3 5
--score değeri 3 ile 5 arasındaki öğeleri sayısını verir.:


ZDIFF 2 zset1 zset2
--verilen setler arasındaki farkları listeler

ZDIFF 2 zset1 zset2 WITHSCORES
--verilen setler arasındaki farkları scorelarıyla listeler

ZDIFFSTORE out 2 zset1 zset2
--iki set arasındaki farkı out adlı sete aktarır.

ZINCRBY myzset 2 "one"
--one değerine sahip elemanın skorunu 2 arrttırır.

ZINTER 2 zset1 zset2 WITHSCORES

ZINTERCARD 2 zset1 zset2 LIMIT 1

ZINTERSTORE out 2 zset1 zset2 WEIGHTS 2 3
//zset1 2 ile zset2 3 ile çarpılır
//kesişen elamanların skorları toplanır.


ZLEXCOUNT key min max
zlexcount myzset (a [z
--alfabetik sıralama yapar. Sayıları da dahil eder.


ZMPOP 2 myzset MIN
zmpop 2 stocks:top user:followers MIN
--minimum skora sahip 2 elemanı çıkarır.

ZMSCORE myzset "apple" "banana" "cherry" "date"
--verilen öğelerin skorlarını sorgular

ZPOPMAX myzset
--verilen set içindeki en yüksek skor sahipp elemanı siler.

ZPOPMIN myzset
--verilen set içindeki en düşük skor sahipp elemanı siler.

ZRANDMEMBER dadi -5 WITHSCORES


ZRANGE zset (5 (10 BYSCORE

ZRANGE zset 10 5 REV BYSCORE

ZRANGEBYLEX myzset - [c
//ilk karakterden c karakteri de dahil olmak üzere alfabetik sıralama yapar

ZRANGEBYSCORE myzset 2 4
//2 ve 4 elemanları arasında skora göre sıralama yapar

ZRANGESTORE dstzset srczset 2 -1
//2. indeksten son indexe kadar elemanları dstzset adlı sete aktarır


ZRANK myzset "cherry"
--verilen öğenin indeks değerini döndürür.

ZREM myzset "two"

ZREMRANGEBYLEX myzset [alpha [omega
--alfabetik olarak siler

ZREMRANGEBYRANK myzset 0 1
--en düşük skorA sahip iki elemanı siler

ZREMRANGEBYSCORE myzset -inf 4
--skorları eksi sonsuz ile 4 arasında olan elemanları siler.

ZREVRANGE myzset 0 -1
--en yüksek skorten en düşük skor sıralar.

ZREVRANGEBYLEX myzset [c -
--Bu komut, öğelerin skorlarına değil, yalnızca üyelerinin alfabetik sıralamasına bakarak işlem yapar.
-- c'den başlayarak a'ya kadar olan karakterleri siler.

ZREVRANGEBYSCORE myzset +inf -inf
--skorları yüksekten düşüğe sıralar.

ZREVRANK stokcs:top AAPL
--elemanları skorları yüksekten düşüğe olarak sıralar.
-- AAPL elemanının indeks bilgisini sıralamaya sondan başlayarak verir.

ZSCORE myzset "one"
--verilen elemanın skorunu döndürür.

ZUNION 2 zset1 zset2
--verilen Setlerin kesişimini Duplikate eleman olmadan Döner

ZUNIONSTORE out 2 zset1 zset2 WEIGHTS 2 3
--kesişimdeki elemanları yeni Bir sete kaydeder.












































