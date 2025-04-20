redis-server

redis-cli
shutdown nosave


<b><mark>shutdown nosave now</mark></b><br>
//bu komut çalıştırıldığında servera bağlantıyı hemen kapatması için istek gönderilir.

set key1 value1 ex 120 nx GET

PEXPIRE myKey 100
myKey anahtarına 100 milisaniye (0.1 saniye) sonra sona ermesi için bir süre atanı





info<br>
info memory<br>
info stats<br>
info replication<br>
<b><mark>info cpu</mark></b><br>
info cluster<br>

<b><mark>info keyspace</mark></b><br>

ping
ping "hello"

quit

set key value
get key

set name "Kenan"
get name

del name

set key1 value1
set key2 value2
set key3 value3

<b><mark>randomkey</mark></b><br>
//rastgele olarak bir key döner.

del key1 key2 key3

exists key1
exists key1 key2 key3

set 1 hello ex 120
ttl 1

expire 1 10

set 1 hello px 100000
pttl 1

expire 1 10
ttl 1

set 1 hello px 1000000
pttl 1

pexpire 1 100



set 1 hello ex 120
persist 1
ttl 1
