# Proje Özeti

## 🎯 Amaç
Bu projenin amacı, büyük dil modelleri (LLM) kullanılarak sohbet verilerinin otomatik etiketlenmesi üzerine bir çalışma gerçekleştirmektir. Proje kapsamında üretilen etiketler:

* **Duygu Analizi (Sentiment Analysis):** Kullanıcı mesajlarının duygusal tonunu belirlemek.
* **Konu/Niyet Etiketleme (Topic/Intent Labeling):** Mesajların hangi konu veya amaçla yazıldığını sınıflandırmak.
* **Yanıt Durumu Analizi (Answered Labeling):** Botun kullanıcı isteğini karşılayıp karşılamadığını tespit etmek.

---

## 📂 Proje Yapısı

### `LlmOutputsDenemeler/` Dizini
* İlk denemeler **Gemma** ve **LLaMA** modelleri ile yapılmıştır.
* 500 konuşmadan alınan kısımlar işlenmiştir.
* Ancak çıktılar istenen formatı karşılamadığı için yalnızca deneme amaçlı saklanmıştır.

### `Calismalar1/` Dizini
* **GPT-5 nano** modeli ile 100 konuşma analiz edilmiştir.
* Konuşmalar 20’şerlik parçalara bölünerek işlenmiştir.
* Modele **sadece kullanıcı (user)** mesajları gönderilmiştir.
* **Üretilen Etiketler:** Duygu (Sentiment), Konu/Niyet (Topic/Intent), Answered (Yanıt verildi mi?).
* **Değerlendirme:** * Manuel etiketlerle kıyaslanmıştır. 
  * LLM’in sadece kullanıcı mesajlarıyla çalışmasına rağmen yüksek doğruluk oranı yakaladığı görülmüştür.
* **Çıktılar:**
  * `labels.csv` → Manuel etiketler (Referans veri)
  * `gpt-5-nano-out-1.csv` → LLM çıktıları
  * `LLM_Karsilastirma.json` → Her konuşmadaki kullanıcı mesajları + manuel etiketler + LLM etiketleri

### `Calismalar2/` Dizini
* Tekrar 100 konuşma işlenmiştir.
* Bu kez hem **bot** hem de **kullanıcı (user)** mesajları modele verilmiştir.
* **Üretilen Etiketler:** Sentiment, Konu/Intent, Answered.
  * *Not:* Bu sürümde "Answered" etiketi yalnızca teknik yanıtı değil, botun kullanıcının isteğini gerçekten yerine getirip getirmediğini analiz edecek şekilde tasarlanmıştır.
* **Eşik Değeri Kullanımı:**
  * LLM çıktıları 0–100 arasında değerler üretmiştir.
  * **50 ve üstü** → Cevaplandı
  * **50 altı** → Cevaplanmadı
* **Manuel Etiketleme Zorluğu:** Bazı mesajlarda insan tarafında da kararsızlık yaşanmıştır. Bu nedenle, LLM hataları kısmen kabul edilebilir bulunmuştur.
* **Gözlemler:** LLM, farklı zamanlarda aynı konuşma için farklı yanıtlar üretebilmiştir. Buna rağmen başarı oranı genel olarak sabit kalmıştır.
* **Çıktılar:**
  * `labels.xlsx` → Manuel etiketler
  * `gpt-5-nano-out-1.xlsx` → LLM çıktıları
  * `LLM_karsilastirma.json` → Konuşma + Tüm etiketler

---

## 📊 Sonuçlar

* **V1 Deneyi:** Sadece kullanıcı mesajları verilmesine rağmen, duygu ve konu etiketlemede yüksek başarı sağlandı.
* **V2 Deneyi:** Bot mesajlarının da dahil edilmesiyle özellikle "Answered" etiketinde daha gerçekçi analizler elde edildi.
* **Doğruluk:** Genel olarak LLM çıktıları, manuel etiketlere yakın ve yüksek bir doğruluk oranı gösterdi.
* **Esneklik:** LLM’in farklı zamanlarda farklı sonuçlar üretebilmesine rağmen, ortalama performansın sabit kaldığı gözlemlendi.

---

## 📌 Genel Değerlendirme

Bu proje, LLM’lerin sohbet verilerinden otomatik etiket üretme kapasitesini açıkça ortaya koymuştur. Elde edilen temel bulgular şunlardır:
1. LLM'ler **sentiment (duygu)** ve **intent (niyet)** etiketlemede güvenilir sonuçlar üretmektedir.
2. **Answered (yanıtlanma durumu)** etiketinde ise değerlendirme daha zordur; yoruma açık olduğu için hem manuel etiketlemede hem de LLM tarafında belirli belirsizlikler görülebilmektedir.
