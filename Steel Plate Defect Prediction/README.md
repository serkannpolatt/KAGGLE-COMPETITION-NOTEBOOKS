## English
## Steel Plate Defect Prediction


### Overview
Welcome to the 2024 Kaggle Playground Series! We plan to continue in the spirit of previous playgrounds, providing interesting an approachable datasets for our community to practice their machine learning skills, and anticipate a competition each month.

**Your Goal:** Predict the probability of various defects on steel plates. Good luck!

### Evaluation
Submissions are evaluated using area under the ROC curve using the predicted probabilities and the ground truth targets.

To calculate the final score, AUC is calculated for each of the 7 defect categories and then averaged. In other words, the score is the average of the individual AUC of each predicted column.

### Submission File
For each id in the test set, you must predict the probability for each of 7 defect categories: Pastry, Z_Scratch, K_Scatch, Stains, Dirtiness, Bumps, Other_Faults. The file should contain a header and have the following format:

	id,Pastry,Z_Scratch,K_Scatch,Stains,Dirtiness,Bumps,Other_Faults
	19219,0.5,0.5,0.5,0.5,0.5,0.5,0.5
	19220,0.5,0.5,0.5,0.5,0.5,0.5,0.5
	19221,0.5,0.5,0.5,0.5,0.5,0.5,0.5
	etc.

### Timeline
- Start Date - March 1, 2024
- Entry Deadline - Same as the Final Submission Deadline
- Team Merger Deadline - Same as the Final Submission Deadline
- Final Submission Deadline - March 31, 2024

All deadlines are at 11:59 PM UTC on the corresponding day unless otherwise noted. The competition organizers reserve the right to update the contest timeline if they deem it necessary.

### About the Tabular Playground Series
The goal of the Tabular Playground Series is to provide the Kaggle community with a variety of fairly light-weight challenges that can be used to learn and sharpen skills in different aspects of machine learning and data science. The duration of each competition will generally only last a few weeks, and may have longer or shorter durations depending on the challenge. The challenges will generally use fairly light-weight datasets that are synthetically generated from real-world data, and will provide an opportunity to quickly iterate through various model and feature engineering ideas, create visualizations, etc.

### Synthetically-Generated Datasets
Using synthetic data for Playground competitions allows us to strike a balance between having real-world data (with named features) and ensuring test labels are not publicly available. This allows us to host competitions with more interesting datasets than in the past. While there are still challenges with synthetic data generation, the state-of-the-art is much better now than when we started the Tabular Playground Series two years ago, and that goal is to produce datasets that have far fewer artifacts. Please feel free to give us feedback on the datasets for the different competitions so that we can continue to improve!


## Türkçe
## Çelik Plaka Arıza Tahmini

### Genel Bakış
2024 Kaggle Oyun Alanı Serisine hoş geldiniz! Topluluğumuzun makine öğrenimi becerilerini geliştirmesi için ilginç ve ulaşılabilir veri kümeleri sunarak önceki oyun alanlarının ruhunu sürdürmeyi ve her ay bir yarışma öngörmeyi planlıyoruz.

**Hedefiniz:** Çelik levhalardaki çeşitli kusurların olasılığını tahmin edin. İyi şanlar!

### Değerlendirme
Gönderimler, tahmin edilen olasılıklar ve temel gerçek hedefler kullanılarak ROC eğrisinin altındaki alan kullanılarak değerlendirilir.

Nihai puanı hesaplamak için, 7 kusur kategorisinin her biri için AUC hesaplanır ve ardından ortalaması alınır. Başka bir deyişle puan, tahmin edilen her sütunun bireysel AUC'sinin ortalamasıdır.

### Gönderim Dosyası
Test setindeki her kimlik için, 7 kusur kategorisinin her birinin olasılığını tahmin etmeniz gerekir: Pasta, Z_Scratch, K_Scatch, Lekeler, Kirlilik, Çarpmalar, Diğer_Hatalar. Dosya bir başlık içermeli ve aşağıdaki formatta olmalıdır:

    id,Pasta,Z_Scratch,K_Scatch,Lekeler,Kirlilik,Darbeler,Other_Faults
    19219,0.5,0.5,0.5,0.5,0.5,0.5,0.5
    19220,0.5,0.5,0.5,0.5,0.5,0.5,0.5
    19221,0.5,0.5,0.5,0.5,0.5,0.5,0.5
    vesaire.

### Zaman çizelgesi
- Başlangıç ​​Tarihi - 1 Mart 2024
- Son Başvuru Tarihi - Son Başvuru Tarihi ile aynı
- Ekip Birleşmesi Son Tarihi - Son Başvuru Son Tarihi ile aynı
- Son Başvuru Tarihi - 31 Mart 2024

Aksi belirtilmediği sürece tüm son tarihler ilgili günde 23:59 UTC'dedir. Yarışma organizatörleri gerekli görmeleri halinde yarışma takvimini güncelleme hakkını saklı tutar.

### Tabular Oyun Alanı Serisi Hakkında
Tabular Playground Serisinin amacı, Kaggle topluluğuna, makine öğrenimi ve veri biliminin farklı yönlerinde becerileri öğrenmek ve geliştirmek için kullanılabilecek çeşitli oldukça hafif zorluklar sunmaktır. Her yarışmanın süresi genellikle yalnızca birkaç hafta sürecektir ve mücadeleye bağlı olarak daha uzun veya daha kısa sürelere sahip olabilir. Zorluklar genellikle gerçek dünya verilerinden sentetik olarak oluşturulan oldukça hafif veri kümelerini kullanacak ve çeşitli model ve özellik mühendisliği fikirlerini hızlı bir şekilde yineleme, görselleştirmeler oluşturma vb. için bir fırsat sağlayacaktır.

### Sentetik Olarak Oluşturulmuş Veri Kümeleri
Oyun Alanı yarışmaları için sentetik verileri kullanmak, gerçek dünya verilerine (adlandırılmış özelliklere sahip) sahip olmak ile test etiketlerinin kamuya açık olmamasını sağlamak arasında bir denge kurmamıza olanak tanır. Bu, geçmişte olduğundan daha ilgi çekici veri kümelerine sahip yarışmalara ev sahipliği yapmamıza olanak sağlıyor. Sentetik veri oluşturma konusunda hala zorluklar olsa da, en son teknoloji, iki yıl önce Tablolu Oyun Alanı Serisini başlattığımız zamana göre çok daha iyi ve bu amaç, çok daha az yapaylık içeren veri kümeleri üretmektir. Gelişmeye devam edebilmemiz için lütfen farklı yarışmalara ilişkin veri kümeleri hakkında bize geri bildirimde bulunmaktan çekinmeyin!