# Decision Tree ile is basvurularini degerlendirilmasi

## Karar Ağacları
Karar ağacları hem sınıflandırmada hemde bağlanım görevlerinde ve hatta çok cıktılı görevleri gerçekleştirebilen çok yönlü makine öğrenim algoritmasıdır.
> Karar ağacları ayrıca rasgele orman (random forest) temel bileşenidir.

## Nasıl Tahmin Yapar? Nasıl Çalışır?
Bir düğümün 3 niteliği vardır;
1. **Sample** : bir düğümün kac tane eğitim örneğinde uygulandığını sayar.
2. **Value** : bir sınıfdaki eğitim örneklerin kaç tanesinde bu düğümün kullanıldığı hakkında bilgi verir.
3. **Gini** : o düğümün *safsızlığını* ölçer. yani, düğümün uygulandığı tüm eğitim örnekleri aynı sınıfa ait ise o düğüm saftır (gini=0)
![Gini](https://yazilimkaravani.net/wp-content/uploads/2020/08/1gini_index-300x129.png)

## Ağacı nasıl oluşturur? Ağac oluşturma algoritmaları nelerdir?
Algoritmaların genel amacı şudur; *ağacı hangi özelliklerine göre ayırmalıyım ?*
### 1.Information Gain (ID3/C4.5)
* **Expected information** 
Sınıflandırma proplemi neyse, etikete göre bir ayırma yapılır.
![info]()

* **İnformation Needed**
Her bir özellik için ayrı ayrı information hesaplanır.
![infoNeed]()

* **İnformation Gain**
Son olarak her bir özelliğin ne kadar kazanç sağladığı bakılır.
![infoGain]()

**Ağacın en tepesinde bu değere göre ayırmaya başlar ve alt ağaçları teker teker ayrılır.**

### Gini Index (CART)
n kadar bütün olasılık değerleri karelerin toplamı 
![Gini]()

bir özelliğin gini değereri hesaplanır ve ağac ona göre bölünür.
![GiniGain]()

## Karar ağacları oluşturulurken oluşan proplemler
**1. Overfitting** : kısaca modelin çok iyi öğrenmesidir. Örneğin ağacın uzunlugu kısa olması gerekirken çok azınlık aykırı veri için yeni ve karmaşık dallanma oluşturmasıdır.

Bu proplemi 2 yöntemle çözülebilir,
**1. Prepruning (budama)** : Ağacı oluştururken oluşan gereksiz dallanmayı engellenmesi.

**2. Postpruning (budama)** : Ağacı oluşturduktan sonra en son budama işlemi yapılır.


## Avantajları 
+ Anlaması kolay ve yorumlaması basittir.
+ Çok az veri hazırlığı gerekir.
+ Çoklu çıkış proplemleri çözülebilir.

## Dezavantajları
+ Verilerdeki küçük değişikler tamamen farklı ağacın oluşmasına sebeğ olabilir.
+ Eğer bazı sınıflar baskınsa, önyargılı ağaclar oluşabilir.
+ karar ağacları, veri iyi genellemeyen karmaşık ağaclar oluşturabilirler.





