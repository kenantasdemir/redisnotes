redis-cli --cluster check 127.0.0.1:7001
//redis kümesindeki 127.0.0.1:7001 redis sunucusunun düzgün çalışıp çalışmadığın kontrol eder.

redis-cli -c -p 7001
//port numarası 7001 olan redis sunucusuna bağlanır.
// -c parametresi redis sunucusunun cluster modunda çalıştığını belir.
quit

redis-cli -p 7001 cluster nodes
//clusterdaki tüm düğümlerin bilgilerini döndürür.

redis-cli -c -p 7002
info
quit
redis-cli -p 7001 cluster nodes


#################################################################

redis-cli -c -p 7001
info
shutdown
quit
clear
ps -ef|grep redis
redis-cli -c -p 7001

#################################################################

redis-server n1_redis.conf &
ps -ef|grep redis 
//sistemde çalışan redis ile ilgili işlemleri listeler.

redis-cli -p 7001 -c
role
quit
redis-cli -p 7005 -c
info
quit
ps -ef|grep redis
redis-cli -c -p 7006
role
shutdown
ps -ef|grep redis
redis-cli -c -p 7001
role
quit
redis-cli -c -p 7005


#################################################################

redis-cli --cluster check 127.0.0.1:7001
redis-cli -c -p 7001
quit

redis-cli --cluster check 127.0.0.1:7001
quit

redis-cli -p 7001 cluster nodes


redis-cli -c -p 7002
info
quit

redis-cli -p 7002 cluster nodes <br>



<b><mark>
Redis Cluster'da keyslot kavramı, bir anahtarın hangi slot'ta yer alacağını belirler. </mark></b><br>
<b><mark>
Redis Cluster, verilerin daha küçük parçalara (slot'lara) 
bölünmesini sağlar ve her bir slot, belirli bir küme düğümüne atanır. </mark></b><br>

<b><mark>Bu, Redis Cluster'ın yatay olarak ölçeklenmesini mümkün kılar.
</mark></b><br>


CLUSTER KEYSLOT keyname
keyname: Slotunu öğrenmek istediğiniz anahtarın adı.

























