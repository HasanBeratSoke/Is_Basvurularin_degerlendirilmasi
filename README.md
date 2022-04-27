# Decision Tree ile is basvurularini degerlendirilmasi

## Karar Ağacları
Karar ağacları hem sınıflandırmada hemde bağlanım görevlerinde ve hatta çok cıktılı görevleri gerçekleştirebilen çok yönlü makine öğrenim algoritmasıdır.
> Karar ağacları ayrıca rasgele orman (random forest) temel bileşenidir.


![tree](https://scikit-learn.org/stable/_images/iris.svg)

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

![info](https://github.com/HasanBeratSoke/Is_Basvurularin_degerlendirilmasi/blob/main/expected%C4%B0nfo.png)

* **İnformation Needed**
Her bir özellik için ayrı ayrı information hesaplanır.

![infoNeed](https://github.com/HasanBeratSoke/Is_Basvurularin_degerlendirilmasi/blob/main/info.png)

* **İnformation Gain**
Son olarak her bir özelliğin ne kadar kazanç sağladığı bakılır.

![infoGain](https://github.com/HasanBeratSoke/Is_Basvurularin_degerlendirilmasi/blob/main/gain.png)

**Ağacın en tepesinde bu değere göre ayırmaya başlar ve alt ağaçları teker teker ayrılır.**

### 2.Gini Index (CART)
n kadar bütün olasılık değerleri karelerin toplamı 

![Gini](https://github.com/HasanBeratSoke/Is_Basvurularin_degerlendirilmasi/blob/main/gini.png)

bir özelliğin gini değereri hesaplanır ve ağac ona göre bölünür.

![GiniGain](https://github.com/HasanBeratSoke/Is_Basvurularin_degerlendirilmasi/blob/main/giniGain.png)

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

## Scikit learn kullanımı
- kütüphane import edildi.
```python
from sklearn import tree
```
- ekiketleri ve varileri ayrıldı.
```python
y = df['IseAlindi']
X = df.drop(['IseAlindi'], axis=1)
```
- tree olusturma
```python
# decision tree olusturma
clf = tree.DecisionTreeClassifier()
clf = clf.fit(X,y)
```
- eğitildikten sonra ağac şeklinde de çizebilirsiniz.
```python
tree.plot_tree(clf)
```
```[Text(239.14285714285714, 195.696, 'X[5] <= 0.5\ngini = 0.469\nsamples = 16\nvalue = [6, 10]'),
 Text(191.31428571428572, 152.208, 'X[1] <= 0.5\ngini = 0.48\nsamples = 10\nvalue = [6, 4]'),
 Text(143.4857142857143, 108.72, 'X[0] <= 0.5\ngini = 0.245\nsamples = 7\nvalue = [6, 1]'),
 Text(95.65714285714286, 65.232, 'X[4] <= 0.5\ngini = 0.5\nsamples = 2\nvalue = [1, 1]'),
 Text(47.82857142857143, 21.744, 'gini = 0.0\nsamples = 1\nvalue = [1, 0]'),
 Text(143.4857142857143, 21.744, 'gini = 0.0\nsamples = 1\nvalue = [0, 1]'),
 Text(191.31428571428572, 65.232, 'gini = 0.0\nsamples = 5\nvalue = [5, 0]'),
 Text(239.14285714285714, 108.72, 'gini = 0.0\nsamples = 3\nvalue = [0, 3]'),
 Text(286.9714285714286, 152.208, 'gini = 0.0\nsamples = 6\nvalue = [0, 6]')]
 ```
 ![GiniGain](https://github.com/HasanBeratSoke/Is_Basvurularin_degerlendirilmasi/blob/main/tree.png)


### Kaynakça
+ https://scikit-learn.org/stable/modules/tree.html#complexity
+ https://en.wikipedia.org/wiki/Decision_tree
+ https://www.youtube.com/watch?v=z_PCJeDOFOk
