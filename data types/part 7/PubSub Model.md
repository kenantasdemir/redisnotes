subscribe ch1
//ch1 isimli kanal oluşturuldu.

publish ch1 msg1
//ch1 isimli kanala msg1 bilgisi gönderildi.

publish ch1 msg2

telnet
o localhost 6379
subscribe ch1
unsubscribe ch1

*************************************************************************

# Patternd subscription

publish news:tech "tech1"
publish news:biz "biz1"

subscribe news:tech news:biz

-----------------------------------

<b><mark>psubscribe news:*</mark></b><br>

publish news:biz "biz1"

-----------------------------------

psubscribe news:* top*

publish topnews "top1"
publish news:biz "biz3"

*************************************************************************

publish news1 "news1"

subscribe news1

<b><mark>pubsub channels *</mark></b><br>

publish news1 "news2"

publish news2 "news2"

subscribe news2 "news2"

pubsub channels *

subscribe topstocks

publish topstocks "top1"

<b><mark>pubsub channels news*</mark></b><br>
pubsub channels top*



*************************************************************************


smembers users
sismember users user1
sadd users user1
srem users user1

rpush msg:room:lobby "user1:testmessage"
rpush msg:room:lobby "user2:testmessage"

lrange msg:room:lobby 0 -1

rpush msg:direct:user1:user2 "user1: test message"
rpush msg:direct:user2:user1 "user2: test message"


lrange msg:direct:user1:user2 0 -1

--

smembers room:lobby
smembers room:admin
smembers room:special


sadd room:lobby user1 user2
smembers room:lobby
smembers room:admin

subscribe room:lobby

sadd room:lobby user1
unsubscribe room:lobby

srem room:lobby user1

smembers room:lobby


















