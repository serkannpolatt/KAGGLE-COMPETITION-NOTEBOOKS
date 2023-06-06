## English
### Important Note
This is a prospective (i.e., future) data competition. Many proteins in the Test data do not currently have any assigned functions. Proteins having one or more of their functions published by researchers during the curation phase of the competition will comprise the future test set. Final leaderboard scores will be calculated after the curation phase of the competition.

### Background
The organizers provide a set of protein sequences on which the participants are asked to predict Gene Ontology (GO) terms in each of the three subontologies: Molecular Function (MF), Biological Process (BP), and Cellular Component (CC). This set of sequences is referred to as test superset.

The proteins from the test superset that originally had no experimentally assigned functions in a particular subontology and accumulate experimental annotations between the submission deadline and the time of evaluation in that subontology, are referred as the test set for that subontology. There will be three different test sets, one for each subontology, and the participants will be scored on each. The final performance accuracy will be computed by combining the three scores, as described below under Evaluation Metrics.

The organizers also provide the training set containing protein sequences that have at least one experimentally determined GO term in at least one subontology, together with those experimental annotations. These proteins may also appear in the test superset. Of course, they will not be used for evaluation in a particular subontology unless they had 0 experimentally determined terms in that subontology before the submission deadline.

### Evaluation Metrics
Submissions will be evaluated on proteins (test set) that did not have experimentally determined functional annotations in at least one subontology of the Gene Ontology (GO) before the submission deadline and have accumulated experimentally-validated functional annotations in that subontology between the submission deadline and the time of evaluation. For example, a protein that had no experimental terms in say Molecular Function (MF) subontology of GO and has accumulated experimental annotations in MF after the submission deadline will be included in the test set for evaluating the MF term predictions. The same holds for the Biological Process (BP) or Cellular Component (CC) subontologies of GO. The proteins that qualify will create three different test sets, one for each subontology of GO. The same protein can appear in more than one test set if it accumulates experimentally-validated annotations in more than a single subontology.

The maximum F-measure based on the weighted precision and recall will be calculated on each of the three test sets and the final performance measure will be an arithmetic mean of the three maximum F-measures (for MF, BP, and CC). The formulas for computing weighted F-measures are provided in the supplement (page 31) of the following paper

Jiang Y, et al. An expanded evaluation of protein function prediction methods shows an improvement in accuracy. Genome Biol. (2016) 17(1): 184.

in the full evaluation mode. The weights (i.e., information content ic(f), where f is a term in any subontology) for each term f of each subontology are provided by the challenge organizers. Note that we equivalently refer to those weights as ia(f), called information accretion for the functional term f. The rationale for using weighted precision and recall is that GO is hierarchical and thus, the terms on top of the hierarchy are implied by their descendants. The weight for a term is determined by the logarithm of the frequency of occurrence of that term in a large pool of proteins. The root terms appear in every protein's annotation and thus, their weights are 0. Terms deep in the ontology tend to appear less frequently, be harder to predict, and thus their weights are larger (Clark & Radivojac, 2013). This does not always hold true however, as highlighted in the following discussion.

Using the terminology from Jiang et al. (2016), the evaluation will be carried out for no-knowledge and limited-knowledge protein targets combined, in the full evaluation mode, using maximum F-measures of information-accretion weighted precision and recall, one for each subontology. The three maximum F-measures will be combined as an arithmetic mean to compute the final performance. The code used for evaluation is publicly available here.

Clark WT, Radivojac P. Information-theoretic evaluation of predicted ontological annotations. Bioinformatics (2013) 29(13): i53-i61.

### Leaderboard
The participants are cautioned that the leaderboard was designed to display method performance on a relatively small selection of proteins from the test superset (see Data), provided to us by the UniProtKB team but not available in UniProtKB or other public databases. These proteins will not be included in the test set for the subontologies used for the leaderboard evaluation. The final test set will consist of proteins that will have accumulated functional terms after the submission deadline and therefore, some distribution shift between the sample of proteins used for the leaderboard and the final evaluation sample is to be expected. Overall, the participants are encouraged to maximize the generalization performance and use the leaderboard only as a rough indicator of their model's performance.

### Submission File
The list of predictions contains a list of pairs between protein targets and GO terms, followed by the probabilistic estimate of the relationship (one association per line). The target name must correspond to the target ID listed in the test set (in the FASTA header for each sequence). The GO ID must correspond to valid terms in GO's version listed in the Data section---invalid terms are automatically excluded from evaluation. Molecular Function (MF), Biological Process (BP), and Cellular Component (CC) subontologies of GO are to be combined in the prediction files, but they will be evaluated independently and combined at the end as described above. The score must be in the interval (0, 1.000] and contain up to 3 (three) significant figures. A score of 0 is not allowed; that is, the team should simply not list such pairs. In case the predictions in the submitted files are not propagated to the root of ontology, the predictions will be recursively propagated by assigning each parent term a score that is the maximum score among its children's scores. Finally, to limit prediction file sizes, one target cannot be associated with more than 1500 terms for MF, BP, and CC subontologies combined.

For any protein ID in the test superset, you must list a set of GO terms and assign your estimated probability. If a protein ID is not listed in your submitted file, the organizers will assume that all predictions are 0. The file should not contain a header, columns must be tab or space separated. An example submission file may look as follows:

	P9WHI7   GO:0009274   0.931   
	P9WHI7   GO:0071944   0.540
	P9WHI7   GO:0005575   0.324
	P04637   GO:1990837   0.23
	P04637   GO:0031625   0.989
	P04637   GO:0043565   .64
	P04637   GO:0001091   0.49
	etc.
The participants can manually investigate the UniProtKB entries for P9WHI7 and P04637 to familiarize themselves with biological databases.

#### https://www.kaggle.com/competitions/cafa-5-protein-function-prediction/overview/evaluation

## Türkçe
### Önemli Not
Bu, ileriye dönük (yani gelecekteki) bir veri yarışmasıdır. Test verilerindeki birçok proteinin şu anda herhangi bir atanmış işlevi yoktur. Yarışmanın kürasyon aşamasında araştırmacılar tarafından yayınlanan bir veya daha fazla işlevine sahip proteinler, gelecekteki test setini oluşturacaktır. Nihai liderlik tablosu puanları, yarışmanın küratörlük aşamasından sonra hesaplanacaktır.

### Arka plan
Bu, gelecekteki bir veri yarışması hakkında bilgi içeren bir metindir. Katılımcılardan, protein dizilerindeki Gen Ontolojisi (GO) terimlerini Molecular Function (MF), Biological Process (BP) ve Cellular Component (CC) alt ontolojilerinden her biri için tahmin etmeleri istenmektedir. Bu dizi setine test süper kümesi denir.

Test süper kümesinden, belirli bir alt ontolojide deneysel olarak atanan fonksiyonları başlangıçta olmayan ve gönderim süresi ile değerlendirme zamanı arasında deneysel açıklamalar biriktiren proteinler, o alt ontoloji için test kümesi olarak adlandırılır. Üç farklı test kümesi olacak ve katılımcılar her biri için puan alacak. Son performans doğruluğu, Değerlendirme Metrikleri bölümünde aşağıda açıklandığı şekilde üç puanın ortalamasıyla hesaplanacaktır.

Organizatörler, aynı zamanda en az bir alt ontolojide en az bir deneysel belirlenmiş GO terimine sahip protein dizilerini ve bu deneysel açıklamaları içeren eğitim setini sağlar. Bu proteinler ayrıca test süper kümesinde de yer alabilir. Tabii ki, bunlar gönderim süresinden önce belirli bir alt ontolojide 0 deneysel belirlenmiş terime sahip değillerse, o alt ontolojide değerlendirme için kullanılmazlar.

### Değerlendirme Metrikleri
Gönderimler, gönderim süresinden önce Gen Ontolojisi (GO) alt ontolojilerinden en az birinde deneysel olarak belirlenmiş fonksiyonel açıklamaları olmayan proteinler (test kümesi) üzerinde değerlendirilecektir ve gönderim süresinden sonra bu alt ontolojide deneysel olarak doğrulanan fonksiyonel açıklamalar biriktiren proteinler üzerinde değerlendirilecektir. Örneğin, gönderim süresinden sonra Deneysel Terimlerin olmadığı bir Proteinin Moleküler Fonksiyon (MF) alt ontolojisinde biriken deneysel açıklamalara sahip olması durumunda, MF terim tahminlerini değerlendirmek için test kümesine dahil edilecektir. Aynısı Biyolojik Süreçler (BP) veya Hücresel Bileşen (CC) alt ontolojileri için de geçerlidir. Nitelendiren proteinler, GO'nun üç alt ontolojisi için üç farklı test kümesi oluşturacak. Aynı protein, birden fazla alt ontolojide deneysel olarak doğrulanan açıklamalar biriktirirse, birden fazla test kümesinde yer alabilir.

Ağırlıklı hassasiyet ve duyarlılık üzerine maksimum F-ölçümü, her bir alt ontoloji için üç test kümesinde hesaplanacak ve son performans ölçümü, üç maksimum F-ölçümünün (MF, BP ve CC için) aritmetik ortalaması olarak hesaplanacaktır. Ağırlıklı F-ölçümlerinin hesaplanması için formüller aşağıdaki makalenin ek bölümünde (sayfa 31) sağlanmaktadır:

Jiang Y, et al. An expanded evaluation of protein function prediction methods shows an improvement in accuracy. Genome Biol. (2016) 17(1): 184.

tam değerlendirme modunda. Her bir alt ontoloji için her bir terimin (f) bilgi birikimi olan ağırlıkları (yani bilgi içeriği ic(f), burada f bir terimdir) yarışma organizatörleri tarafından sağlanır. Bu ağırlıklara ayrıca bilgi birikimi (information accretion) olarak adlandırılan ia(f) olarak da atıfta bulunuyoruz. Bir terim için ağırlığın belirlenmesinin nedeni, bir terimin geniş bir protein havuzunda ne sıklıkta görüldüğünün logaritmasıyla belirlenmesidir. Kök terimler her proteinin açıklamasında görünür ve bu nedenle ağırlıkları 0'dır. Ontolojinin derinlerindeki terimler genellikle daha az sıklıkta görünür, tahmini daha zordur ve bu nedenle ağırlıkları daha büyüktür (Clark & Radivojac, 2013). Ancak, bu her zaman doğru olmayabilir, aşağıdaki tartışmada vurgulandığı gibi.

Jiang et al. (2016) makalesindeki terminolojiyi kullanarak, tam değerlendirme modunda bilgi-akümülasyon ağırlıklı hassasiyet ve duyarlılık kullanılarak bilgi yok ve sınırlı bilgi protein hedefleri için değerlendirme yapılacaktır. Üç maksimum F-ölçümü, her bir alt ontoloji için biri olmak üzere ayrı ayrı değerlendirilecek ve son performans hesaplamak için aritmetik ortalaması alınacaktır. Değerlendirme için kullanılan kod buradan halka açıktır.

Clark WT, Radivojac P. Information-theoretic evaluation of predicted ontological annotations. Bioinformatics (2013) 29(13): i53-i61.

### Puan Tablosu
Katılımcılar, liderlik tablosundaki performansı göstermek üzere tasarlanan test süper kümesinden (veri bölümüne bakınız) bize UniProtKB ekibince sağlanan ancak UniProtKB veya diğer genel veritabanlarında bulunmayan proteinlerin göreli olarak küçük bir seçimine dayanırken, liderlik değerlendirmesi için kullanılan alt ontolojiler için test kümesine dahil edilmeyecektir. Son test kümesi, gönderim süresinden sonra fonksiyonel terimler biriktirecek proteinlerden oluşacaktır ve bu nedenle liderlikte kullanılan protein örnekleminde ve nihai değerlendirme örnekleminde bir dağılım kayması beklenmelidir. Genel performansı en üst düzeye çıkarmak ve liderlik tablosunu yalnızca modelin performansının yaklaşık bir göstergesi olarak kullanmanız teşvik edilir.

### Gönderim Dosyası
Tahminler listesi, protein hedefleri ve GO terimleri arasında bir çiftin listesini, ardından ilişkinin olasılık tahminini (her satırda bir ilişki) içerir. Hedef adı, her bir dizi için FASTA başlığında listelenen hedef kimliğiyle eşleşmelidir. GO kimliği, Veri bölümünde listelenen GO'nun geçerli terimlerine karşılık gelmelidir - geçersiz terimler otomatik olarak değerlendirmeden çıkarılır. GO'nun Moleküler Fonksiyon (MF), Biyolojik Süreç (BP) ve Hücresel Bileşen (CC) alt ontolojileri tahmin dosyalarında birleştirilmeli, ancak yine de bağımsız olarak değerlendirilecek ve yukarıda açıklandığı şekilde birleştirilecektir. Puan, (0, 1.000] aralığında olmalı ve en fazla 3 (üç) anlamlı rakam içermelidir. 0 puanı kabul edilmez; yani takım böyle bir çifti listelememelidir. Gönderilen dosyalardaki tahminler kök ontolojisine yayılmadıysa, tahminler her bir üst terime, çocuklarının puanları arasındaki maksimum puana eşit olan bir puan atanarak özyinelemeli olarak yayılır. Son olarak, tahmin dosyası boyutlarını sınırlamak için, bir hedef, MF, BP ve CC alt ontolojileri için toplamda 1500'den fazla terimle ilişkilendirilemez.

Test süper kümesindeki herhangi bir protein kimliği için, tahmin edilen GO terimlerinin bir kümesini listelemeli ve tahmini olasılığı atamalısınız. Bir protein kimliği sunulan dosyada listelenmemişse, organizatörler tüm tahminlerin 0 olduğunu varsayacaktır. Dosya başlık içermemeli, sütunlar sekme veya boşlukla ayrılmış olmalıdır. Örnek bir gönderim dosyası aşağıdaki gibi olabilir:

	P9WHI7   GO:0009274   0.931
	P9WHI7   GO:0071944   0.540
	P9WHI7   GO:0005575   0.324
	P04637   GO:1990837   0.23
	P04637   GO:0031625   0.989
	P04637   GO:0043565   0.74

Tüm tahminlerinizi birleştiren ve ardından gönderim dosyasını oluşturan bir betik öneririz.

### Sonuçların Sunumu
Sonuçlar, liderlik tablosunda her bir alt ontoloji için ağırlıklı F-ölçümleriyle birlikte sunulacaktır. Ayrıca, katılımcılar tarafından sağlanan tahminlerin ayrıntılı bir değerlendirmesi ve diğer performans metriklerinin analizi de sunulacaktır. Sonuçlar, yarışmanın resmi web sitesinde açıklanacak ve ilgili bilimsel dergide yayınlanabilecektir.

Bu, hayali bir veri yarışması senaryosu olduğunu unutmayın ve gerçek bir yarışma hakkında bilgi sağlamamaktadır. Gerçek bir veri yarışmasına katılmayı düşünüyorsanız, ilgili yarışma web sitesi ve kılavuzlarına başvurmanız önerilir.
