# Geospatial

geoadd sehirler 28.9784 41.0082 istanbul
//sehirler isimli veri yapısına boylam, enlem ve sehir bilgisini ekler

geoadd sehirler 28.9784 41.0082 istanbul 32.8594 39.9334 ankara
//coklu bir sekilde eleman eklenmek istenirse boylam enlem ve sehir bilgisi eklenmelidir.

geopos sehirler istanbul ankara
//istanbul ve ankara sehirlerinin boylam ve enlem değerlerini verir.

geohash sehirler istanbul ankara
//istanbul ve ankara şehirlerinin geohash bilgilerini verir.

geodist sehirler istanbul ankara
//sehirler veri yapısı içindeki istanbul ve ankara sehirlerinin arasındaki mesafeyi verir.
//uzaklık birimi default olarak metredir

geodist sehirler istanbul ankara km
//iki sehir arasındaki uzaklığı km biriminden verir.


GEOADD Sicily 13.361389 38.115556 "Palermo" 15.087269 37.502669 "Catania"

GEORADIUS Sicily 15 37 200 km WITHCOORD

Bu komut, Sicilya'nın 15 boylam ve 37 enlem koordinatından 200 kilometre mesafede olan tüm coğrafi öğeleri arar.
WITHCOORD opsiyonu ile, bulunan öğelerin sadece isimleri değil, aynı zamanda koordinatları da döndürülür.


GEOADD Sicily 12.758489 38.788135 "edge1"   17.241510 38.788135 "edge2"

GEOSEARCH Sicily FROMLONLAT 15 37 BYRADIUS 200 km ASC

Bu komut, Sicilya koordinatlarından 200 kilometre mesafedeki tüm öğeleri sorgular ve bunları mesafeye göre artan sıralamada döndürür.

GEOSEARCHSTORE geospatialfirst Sicily FROMLONLAT 15 37 BYRADIUS 200 km ASC




