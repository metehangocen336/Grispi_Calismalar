Odev4 - Proje Özeti
🎯 Amaç

Bu projenin amacı, büyük dil modelleri (LLM) kullanılarak sohbet verilerinin
otomatik etiketlenmesi üzerine bir çalışma gerçekleştirmektir.
Proje kapsamında üretilen etiketler:

Duygu Analizi (Sentiment Analysis) → Kullanıcı mesajlarının duygusal tonunu belirlemek.

Konu/Niyet Etiketleme (Topic/Intent Labeling) → Mesajların hangi konu veya amaçla yazıldığını sınıflandırmak.

Yanıt Durumu Analizi (Answered Labeling) → Botun kullanıcı isteğini karşılayıp karşılamadığını tespit etmek.

📂 Proje Yapısı
1. LlmOutputsDenemeler Dizini

İlk denemeler Gemma ve LLaMA modelleri ile yapılmıştır.

500 konuşmadan alınan kısımlar işlenmiştir.

Ancak çıktılar istenen formatı karşılamadığı için yalnızca deneme olarak saklanmıştır.

2. Odev4V1 Dizini

GPT-5 nano modeli ile 100 konuşma analiz edilmiştir.

Konuşmalar 20’şerlik parçalara bölünerek işlenmiştir.

Modele sadece kullanıcı (user) mesajları gönderilmiştir.

Üretilen etiketler:

Duygu (Sentiment)

Konu/Niyet (Topic/Intent)

Answered (yanıt verildi mi?)

Değerlendirme:

Manuel etiketlerle kıyaslanmıştır.

LLM’in sadece kullanıcı mesajlarıyla çalışmasına rağmen yüksek doğruluk oranı yakaladığı görülmüştür.

Çıktılar CSV ve JSON formatlarında kaydedilmiştir:

labels.csv → Manuel etiketler

gpt-5-nano-out-1.csv → LLM çıktıları

LLM Karşılaştırma.json → Her konuşmadaki kullanıcı mesajları + manuel etiketler + LLM etiketleri

3. Odev4V2 Dizini

Tekrar 100 konuşma işlenmiştir.

Bu kez hem bot hem de user mesajları modele verilmiştir.

Üretilen etiketler:

Sentiment

Konu/Intent

Answered → Bu sürümde answered etiketi yalnızca teknik yanıtı değil, botun kullanıcının isteğini gerçekten yerine getirip getirmediğini analiz edecek şekilde tasarlanmıştır.

Eşik Değeri Kullanımı:

LLM çıktıları 0–100 arasında değerler üretmiştir.

50 üstü → cevaplandı

50 altı → cevaplanmadı

Manuel Etiketleme Zorluğu:

Bazı mesajlarda kararsızlık yaşanmıştır.

Bu nedenle, LLM hataları kısmen kabul edilebilir bulunmuştur.

Gözlemler:

LLM, farklı zamanlarda aynı konuşma için farklı yanıtlar üretebilmiştir.

Buna rağmen başarı oranı genel olarak sabit kalmıştır.

Çıktılar:

labels.xlsx → Manuel etiketler

gpt-5-nano-out-1.xlsx → LLM çıktıları

LLMkarşılaştırma.json → Konuşma + etiketler

📊 Sonuçlar

V1 Deneyi: Sadece kullanıcı mesajları verilmesine rağmen, duygu ve konu etiketlemede yüksek başarı sağlandı.

V2 Deneyi: Bot mesajlarının da dahil edilmesiyle özellikle answered etiketinde daha gerçekçi analizler elde edildi.

Doğruluk: Genel olarak LLM çıktıları, manuel etiketlere yakın yüksek doğruluk oranı gösterdi.

Esneklik: LLM’in farklı zamanlarda farklı sonuçlar üretebilmesine rağmen, ortalama performans sabit kaldı.

📌 Genel Değerlendirme

Bu proje, LLM’lerin sohbet verilerinden otomatik etiket üretme kapasitesini ortaya koymuştur.
Elde edilen bulgular:

LLM’ler sentiment ve intent etiketlemede güvenilir sonuçlar üretmektedir.

Answered etiketinde ise değerlendirme daha zordur ve hem manuel hem de LLM etiketlemede belirsizlikler görülebilir.