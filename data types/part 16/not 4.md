ps -ef|grep redis
redis-cli -c -p 7002
<b><mark>CLUSTER NODES</mark></b><br>
<b><mark>CLUSTER SLOTS</mark></b><br>
//"cluster slots" komutu, Redis kümesindeki tüm düğümler arasında anahtar aralıklarının nasıl dağıtıldığını ve 
//anahtar alanlarının hangi düğümlere atanacağını gösteren bir anahtar dağıtım haritası (key distribution map) oluşturmak için kullanılır.

##############################################################################

redis-cli -c -p 7002 <br>

<b><mark>CLUSTER HELP</mark></b><br>
//cluster modu hakkında bilgi verir.
//cluster üzerinden kullanılabilecek komutları ve bunların açıklamasını listeler.

<b><mark>CLUSTER INFO</mark></b><br>
//cluster hakkında bilgiler verir.

<b><mark>CLUSTER MYID</mark></b><br>
//"cluster myid" komutu, Redis kümesi düğümünün benzersiz kimliğini (ID) döndürür. 
//Bu kimlik, düğümün bir küme üyesi olarak tanınmasını sağlar ve diğer düğümler tarafından tanınmasına yardımcı olur.

<b><mark>CLUSTER NODES</mark></b><br>
role <br>
info <br>
<b><mark>CLUSTER REPLICAS clusterid</mark></b><br>
//clusterid ile belirtilen clusterın replikalarını listeler.

##############################################################################

redis-cli -c -p 7002
set k2 v2
keys *
cluster keyslot k2
// belirtilen anahtarın hangi slot numarasına atandığını döndürür. 

cluster keyslot name
cluster keyslot name1
cluster keyslot name3
cluster help

cluster getkeysinslot 449 1
//cluster getkeysinslot komutu belirtilen slot numarasında depolanan anahtarların listesini döndürür.
//bu örnekte 449.slotta depolanan ilk anahtarı listeler.

cluster keyslot name1

##############################################################################

------------shutdown a cluster ----------------------

ps -ef|grep redis
redis-cli -p 7001
cluster nodes
quit
redis-cli -p 7004 -c
role
quit
redis-cli -p 7001 shutdown
//7001 portunda çalışan clusterı sonlandırır.

redis-cli -p 7002 shutdown
ps -ef|grep redis


##############################################################################

RedisSearch

"*"
"@movie_name:{heat}"   //RedisSearch biriminde bir key-value çifti tanılaması bu şekildedir.
"@movie_name:heat"
//Anahtarlar, çeşitli veri tiplerini içerebilir, örneğin bir dize, bir sayı, bir liste, bir küme, bir sözlük vb.

"*"
groupby 1 @category
//@category alanına göre gruplar. bu işlem sonucunda sadece 1 grup oluşur.

"*"
groupby 1 @category
reduce count 0 as count_of_movies
//ifadesi toplam belge saysını count_of_movies adlı bir değişkene atar
//0 ifadesi azaltma işlemine başlangıç değeri olarak verilecek sayıdır.

reduce sum 1 votes as total_votes
//"SUM" ifadesi, belirli bir sütunda toplama işlemi yapmak için kullanılır
//"1" ifadesi toplama işlemine eklenecek sayıdır. 
//"VOTES" ifadesi ise toplama işlemi yapılacak sütunun adıdır.
//"total_votes" değişkeni, oyların toplamı hakkında bilgi sağlayacak.

reduce avg 1 rating as avg_rating
//rating ifadesi ortalaması hesaplanacak alanı ifade eder.
//"1" ifadesi, her kayıt için hesaplanacak ortalama değerin bulunacağı alanı ifade eder. 
//"as avg_rating" ifadesi ise hesaplanan ortalama değeri "avg_rating" olarak kaydetmek için kullanılır.

sortby 4 @total_votes DESC @avg_rating DESC
// sonuçların 4. sütuna (total_votes) göre azaltılmasını istiyor. 
//aynı sütuna göre descending (azalan) sıralama yapılmasını sağlamak için "DESC" anahtar kelimesi kullanılır.
//aynı şekilde 5. sütuna (avg_rating) göre azaltma yapılır ve burada da yine descending sıralama yapılır. 
//Sonuçta elde edilen veriler, total_votes ve avg_rating sütunlarına göre sıralanmış olacaktır.


CLUSTER SHARDS
//kümenin parçalarıyla ilgili ayrıntıları döndürür.

CLUSTER SLAVES
//slave durumundaki düğümleri listeler.

CLUSTER MYID
//oanki düğümün id değerini verir.

CLUSTER LINKS 
//tüm cluster içinde kurulan master-slave bağlantıları hakkında array şeklinde bilgiler verir.

CLUSTER RESET
//Redis cluster düğümünü sıfırlamak için kullanılır
//bu komut eğer masterlar elinde key varsa çalışmaz
//bir ana düğümü sıfırlamak için önce anahtarlar FLUSHALL komutuyla kalıdırılmalıdır
//daha sonra CLUSTER RESET komutu kullanılmalıdır.

CLUSTER REPLICATE node-id
//bu komut bir düğümü node-id değeri ile belirtilen masterın kopyası haline gelir

CLUSTER REPLICAS node-id
//Komut, belirtilen ana düğümden kopyalanan kopya düğümlerin bir listesini sağlar.


Redis Cluster'da her düğüm, hangi master'ın belirli bir hash slotuna hizmet ettiğini takip eder.
"CLUSTER DELSLOTS" komutu, belirli bir düğümün işlediği slotları silerek Redis Cluster'ın yapılandırmasını değiştirir. 

CLUSTER DELSLOTS 0 1
"CLUSTER DELSLOTS" komutunu kullanarak slot 0 ve slot 1'i silmek isterseniz, bu komutu kullanabilirsiniz.

//Komut, yalnızca belirtilen tüm slotlar zaten bazı düğümlerle ilişkilendirilmişse çalışır.
//Aynı komut birden çok kez belirtilirse komut başarısız olur.


CLUSTER FLUSHSLOTS
//bir düğümdeki bütün slotları siler.
























