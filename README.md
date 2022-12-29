# MachineLearning-PCA-Algorithm
PCA Algorithm

Step1(Veri Seti Elde Et):
Öncelikle veri seti elde edilir. Daha sonra elde edilen veri seti X ve Y’ye bölünür. 
Y doğrulama seti, X ise eğitim seti olarak atanır. Başka bir deyişle X ile öğretilen değerler Y ile teyit edilir. 

Step2(Veriler ile Yapı Oluştur):
X bağımsız değişkenin 2 boyutlu matrisi alınır. Satırlar veri öğelerini, sütunlar da gerekli öğenin özelliklerini temsil eder. 
Sütun sayıları boyut sayısı ile eşit miktardadır. Her girişten ilgili sütunun ortalaması çıkarılır, bu işlem her sütun için tekrar edilir.

Step3(Veri Standardize Edilmesi):
Verilen x sütunlarına bakarak, daha yüksek varyansa sahip özellikler daha düşük varyansa sahip özelliklerden daha mı önemlidir?
Yoksa özelliklerin önemi varyanstan bağımsız mıdır ? Son durumda önem, özelliğin Y’yi ne kadar iyi tahmin ettiğini ifade eder.
Özelliklerin önemi özelliklerin varyansından bağımsızsa, bir sütundaki her gözlem o sütunun standart sapmasına bölünür.
(Ortalanmış ve standardize edilmiş matrise Z adlandırılması yapılacak.)

Step4(Z'nin Kovaryansını Hesapla):
Z matrisinin transpozu alınır (Z^T) ve transpozlu hali kendisi ile çarpılır.
Z kovaryansı = Zᵀ*Z şeklinde hesaplanır.
Ortaya çıkan matris bir sabite kadar Z’nin kovaryans matrisidir. 


Step5(Öz Vektör ve Öz Değer Hesabı):
Özvektörleri ve bunlara karşılık gelen ZᵀZ özvektörlerini hesaplanır. 
P özvektörler matrisi olmak üzere;
ZᵀZ’nin özdekompozisyonu, ZᵀZ’nin PDP⁻¹’ye ayrıştırıldığı yerdir. 
D ise özdeğeri olan köşegen matrisidir ve köşegen dışında değeri 0’dır.
D’nin köşegenindeki özdeğerler, P’de karşılık gelen değerlerle ilişkilendirilir. 
Yani D’nin ilk elemanı λ₁’dir ve karşılık gelen özvektör P’nin ilk sütunudur. 
Bu tüm D değerleri ve P’de denk gelen özvektör karşılıkları için geçerlidir.
PDP⁻¹ her zaman bu doğrultuda hesaplanır. 

Step6(Öz Vektörleri Sırala):
Özdeğerler alınıp (λ₁, λ₂, …, λp) büyükten küçüğe sıralanır. Bu şekilde P’deki özvektörler de sıralanmış olur. 
(Örneğin λ₂ en büyük özdeğer olsun, o halde P’nin ikinci sütun alınıp en başa konur.)
(Sıralanmış P özvektör matrisine P* olarak daha sonra ulaşılacak.)

Step-7(Yeni Özellikleri Hesapla):
Z* = ZP* eşitliği hesaplanır. Bu yeni Z* matrisi X’in ortalanmış ve standartlaştırılmış halidir 
ama Z*’de her bir gözlem orijinal değişkenlerin kombinasyonudur. Ağırlıklar özvektöre göre hesaplanır. 

(P* içindeki özvektörler bağımsız olduğundan, Z*’nin her sütunları da aynı zamanda birbirinden bağımsızdır.)

Step-8(Yeni Setten Önemsiz Verileri Çıkar)
Yeni setteki özelliklerden hangisi/hangileri tutulmalı bu belirlenir.
Her bir özdeğer kabaca karşılığı olduğu özvektörün önemidir. Bu sebeple açıklanmış olan varyans oranı, tuttuğunuz özelliklerin özdeğerlerinin toplamının, tüm özelliklerin özdeğerlerinin toplamına bölümüdür. 
Bunun için 3 farklı yöntem izlenir:
1.Yöntem: Kaç boyut tutulmak istendiğine karar verilir. 
2.Yöntem: Her özelliğin varyans oranı hesaplanır. Eşik değer(Threshold) seçilip eşik değere gelinene kadar özellik eklenir.
3. Yöntem: İkinci metod gibi her özelliğin varyans oranı hesaplanarak başlanır. Özellikler varyans oranına göre sıralanır ve daha fazla özellik tutuldukça açıklanan kümülatif varyans oranı çizilir. Yeni bir özellik eklemenin, önceki özelliğe göre oluşan varyansta önemli bir düşüşe sahip olduğu nokta tespit edilir ve bu noktaya kadar eklenen özellikleri seçerek, kaç özelliğin dahil edileceği belirlenir.
