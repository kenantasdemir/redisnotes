terminal 1(master)
<b><mark>redis-server --port 6379 --dbfilename db1.rdb</mark></b><br>
//yeni bir redis sunucu oluşturur ve 6379 portunda çalışır
//veritanı ismi olrak db1.rdb ayarlanır.

terminal 2(master)
redis-server --port 6380 --dbfilename db2.rdb

terminal 3(slave)
<b><mark>redis-cli -p 6379</mark></b><br>
//6379 portunda yayın yapan sunucuya bağlanır.
info
clear
info
clear
set k1 v1
get k1
keys *
set k2 v2

terminal 4(slave)
redis-cli -p 6380
// 6380 portunda yayın yapan sunucuya bağlanır.
info
clear
<b><mark>replicaof localhost 6379</mark></b><br>

info
clear
keys *


terminal 5(slave)
redis-cli -p 6381
keys *
info
replicaof localhost 6379
//6379 portunda yayın yapan master sunucuya bağlanır ve veri transferi yapar.
info
<b><mark>replicaof no one</mark></b><br>
//veri transferi için kurulan bağlantıyı sonlandırır.



































