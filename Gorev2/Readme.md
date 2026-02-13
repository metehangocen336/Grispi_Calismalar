Odev4 Projesi – LLM Etiketleme ve Analiz
Proje Yapısı
Odev4/
│
├─ .env
├─ 20-sohbet-trendyol-mila.json
├─ islemler.ipynb
├─ kontrol.ipynb
├─ konuPrompt.txt
├─ konuDetayPrompt.txt
├─ sentimentPrompt.txt
├─ turrrPrompt.txt
├─ yanit_durumu_prompt.txt
├─ Ilm_basari_oranlari.png
├─ Ilm_karsilastirma.json
├─ manuel_labels.csv
├─ manuel_labels.xlsx
├─ gpt-5-nano-out1.csv
├─ gpt-5-nano-out1.xlsx
│
├─ Odev4V1/
│   ├─ etiket_csvler/
│   │   ├─ etiket_tablosu_intent_detay.csv
│   │   ├─ etiket_tablosu_intent.csv
│   │   ├─ etiket_tablosu_sentiment.csv
│   │   ├─ etiket_tablosu_tur.csv
│   │   └─ etiket_tablosu_yanit_durumu.csv
│   │
│   ├─ kontrol_sonuclari/
│   │   ├─ intent_detayKontrol.txt
│   │   ├─ intentKontrol.txt
│   │   ├─ sentimentKontrol.txt
│   │   ├─ turKontrol.txt
│   │   └─ yanit_durumuKontrol.txt
│   │
│   ├─ pie_charts/
│   │   ├─ etiket_pie_intent_detay.png
│   │   ├─ etiket_pie_intent.png
│   │   ├─ etiket_pie_sentiment.png
│   │   ├─ etiket_pie_tur.png
│   │   └─ etiket_pie_yanit_durumu.png
│   │
│   └─ table_images/
│       ├─ etiket_tablosu_intent_detay.png
│       ├─ etiket_tablosu_intent.png
│       ├─ etiket_tablosu_sentiment.png
│       ├─ etiket_tablosu_tur.png
│       └─ etiket_tablosu_yanit_durumu.png
│
└─ Odev4V2/
    └─ (Yapı Odev4V1’e benzer, ancak **tüm etiketler (`tur`, `intent`, `intent_detay`, `sentiment`, `yanit_durumu`) zorunlu seçeneklerle sınırlı**)

📝 Proje Hakkında

Bu proje, LLM (GPT-5 Nano) kullanarak mesajların otomatik etiketlenmesini ve manuel etiketlerle karşılaştırılmasını amaçlar.

Sürüm Farkları:

Odev4V1:

Sadece tur, intent, intent_detay serbest üretilir.

sentiment ve yanit_durumu sınırlıdır; model daha kısıtlı tahmin yapar.

LLM’in tahminleri, manuel etiketlerle karşılaştırılabilir.

Odev4V2:

Tüm etiketler (tur, intent, intent_detay, sentiment, yanit_durumu) zorunlu seçeneklerle sınırlıdır.

LLM, verilen seçenekler arasından en uygun tahmini yapmak zorundadır.

Yakın kategoriler veya alt kategori yorumlamalarından kaynaklanan küçük farklar görülebilir.

📊 Dosya Açıklamaları
1. etiket_csvler/

Tüm mesajlar için LLM ve manuel etiketlerin dağılımını CSV formatında gösterir:

intent, intent_detay, sentiment, tur, yanit_durumu

2. kontrol_sonuclari/

Manuel etiketler ve LLM tahminleri arasındaki farkları gösterir.

Örnek: intent_detayKontrol.txt → farklı satırlar ve etiketler listelenir.

3. pie_charts/

Her etiketin dağılımını görsel olarak pasta grafiği ile gösterir.

Örnek: etiket_pie_intent.png

4. table_images/

Her etiketin dağılımını tablo formatında görselleştirir.

Örnek: etiket_tablosu_sentiment.png

5. LLM Çıktıları

gpt-5-nano-out1.csv ve .xlsx → LLM tarafından üretilen tüm etiketler.

💻 Kullanım

Etiket Üretimi:

islemler.ipynb → LLM tahminlerini üretir ve CSV/Excel’e kaydeder.

Etiket Karşılaştırması:

Grafik ve Tablo Görselleştirme:

pie_charts/ ve table_images/ klasörleri → Otomatik olarak oluşturulur ve dağılım analizini görselleştirir.