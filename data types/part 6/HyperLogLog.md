# HyperLogLog

pfadd hll1 1 2 3 4
//hll1 isimli yapısına 1 2 3 ve 4 elemanlarını ekler

pfadd hll1 1

pfcount hll1
//hll1 isimli veri yapısında bulunan elemanların sayını verir.

pfadd hll2 2 3 4 5
pfadd hll3 20 30 40

pfmerge hll hll1 hll2 hll3
//hll1 hll2 ve hll3 veri yapılarının elemanlarını yeni bir HyperLogLog yapısı olan hll içerisine ekler

pfcount hll


