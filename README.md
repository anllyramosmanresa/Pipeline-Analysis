# SARS-CoV-2 Genomik Varyant Analizi ve Makine Öğrenmesi Modellemesi

## Proje Özeti
Bu proje; ham genomik dizileme verilerinin (*SRR17855325*) biyoinformatik boru hattı ile doğrulanmasını, varyant tespitini ve elde edilen veriler üzerinde makine öğrenmesi regresyon modellerinin performans değerlendirmesini kapsamaktadır.


## 1. Veri Teşhisi ve Hizalama (Alignment)
* **Başlangıç Problemi:** `SRR17855325` veri seti ilk etapta *E. coli* referans genomuna eşleştirilmeye çalışılmış, ancak **%0 hizalama (mapping)** elde edilmiştir.
* **Kök Neden Tespiti:** ENA (European Nucleotide Archive) meta verileri incelenerek örneğin aslında **SARS-CoV-2** virüsüne ait olduğu belirlenmiştir.
* **Hizalama Doğrulaması:** 
  * ***E. coli* Referansı:** %0.00
  * **SARS-CoV-2 Referansı:** %99.93 (Başarıyla doğrulandı)


## 2. Varyant Çağırma (Variant Calling)
*Doğru referans genom üzerinden yürütülen varyant analiz adımları sonucunda toplam **73 adet belirleyici varyant** tespit edilmiş ve makine öğrenmesi girdi formatına (CSV) dönüştürülmüştür.


## 3. Makine Öğrenmesi Performansı
*Elde edilen 73 varyantlık veri seti üzerinde regresyon modelleri çalıştırılmış ve platformlar arası karşılaştırma yapılmıştır:

* ExtraTrees Regressor (AITool): R^2 = 0.48
* Karşılaştırmalı İkincil Araç: R^2 = 0.28 - 0.32


##  4. Bulgular ve Değerlendirme
* **Eğitim/Test Bölünme Hassasiyeti:** Aynı veri seti kullanılmasına rağmen iki farklı araç arasındaki skor farklılığı, örneklem boyutunun kısıtlı olduğu ($N = 73$) durumlarda modellerin **train/test split** rasgeleliğine ne kadar duyarlı olduğunu göstermektedir.
* **Veri Ölçeği Karşılaştırması:** Bu yüksek varyans ve tutarsızlık durumu, daha önce analiz edilen **1.529 satırlık** geniş bakteri veri setinde gözlemlenmemiş olup; biyoinformatik verilerde veri hacminin model kararlılığı açısından önemini vurgulamaktadır.
