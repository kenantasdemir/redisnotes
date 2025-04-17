<b><mark>set key val exat 1624737950</mark></b><br>
//timestamp cinsinden expiration süresi verildi.
tll key
//anahtarın expire olma süresini görüntüler.

<b><mark>set key1 val1 px 10000</mark></b><br>
//10000 ms saniye expire olacak.

set key2 val2 ex 60
//60 saniye içine expire olacak


flushdb 
//tüm key value çiftlerini siler.

<b><mark>set key1 val1 keepttl</mark></b><br>
//keepttl parametresi sayesinde bir anahtarın sona erme süresini değiştirebiliriz.

xx --> if it present
//eğer set işlemi sadece var olan bir anahtarın değerini değiştirecekse bunu kullanmalısınız. var olan değerin üzerine yazar.

nx --> if it doesnt exists
// yeni bir anahtar için değer atanacaksa bu kullanılmalıdır.

set anahtar deger xx

exists myanahtar
//myanahtar adlı bir key var mı kontrol eder varsa 1 yoksa 0 döner

set mykey 10
incr mykey
//mykey isimli anahtarın değerini 1 arttırır.

decr mykey
//mykey isimli anahtarın değerini 1 azaltır.

incrbyfloat mykey -.3
//mykey adlı anahtarın değerini 3/10 azaltır.


set score 10
get score

type score
//score isimli nesnenin tipini dönderir.

del score

clear

set student:101:score:math 10
get student:101:score:math
type student:101:score:math

incr student:101:score:math
//anahtarın değerini bir arttırmak için kullanılır

decr student:101:score:math
//anahtarın değerini 1 azaltmak için kullanılır.

set customer:101:balance 100
get customer:101:balance

incr customer:101:balance
decr customer:101:balance

incrby customer:101:balance 100
//key değerine her seferinde 100 ekler.

decrby customer:101:balance 15
//key değerini 15 azaltır.


######################################################################################3

set num 1
set num 1.5

get num
type num

incrby num 1

incrbyfloat num 1
incrbyfloat num 1.2
//key değeri 1.2 artacak

decrbyfloat num 0.5
//key değeri 0.5 azalacak

incrbyfloat num -0.5

set app:fees:cc 1.0
incrbyfloat app:fees:cc 0.2
incrbyfloat app:fees:cc 2.0
incrbyfloat app:fees:cc -1.5





















