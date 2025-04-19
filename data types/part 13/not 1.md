# Redis Protocol

> Redis istemciler Redis server ile haberleşmek için RESP denen bir protokol kullanır.
(REdis Serialization Protocol).
> imlemente etmesi kolay
> parse etmek için hızlı
> kolay okunabilir.

> RESP integer string array gibi bir çok farklı veri tipine serialize edilebilir.

•RESP binary-safe'dir.


Redis Protocol-Özellikleri
  Request–Response Model

Client
<b><mark>komutları redis sunucusuna bulk stringlerden oluşan arrayler halinde gönderir.</mark></b><br>

Server
<b><mark>komut uygulamasına göre RESP türlerinden biriyle yanıt verir.</mark></b><br>


---

Redis Protocol

RESP'de, bazı verilerin türü ilk bayta bağlıdır. <br>

> Basit stringler için yanıtın ilk baytı "+" dır.
> Hatalar için yanıtın ilk baytı "-"
> integers için yanıtın ilk baytı ":" şeklindedir.
> Bulk stringler için yanıtın ilk baytı "$" dır.

