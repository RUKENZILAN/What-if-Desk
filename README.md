# What-if-Desk
One-tap what-if analysis for leaders: see how team, pricing, churn and cost decisions change delivery dates and cash flow.

Page link: https://whatifdesk.vercel.app/


# English summary

** What-If Desk** is a mobile-friendly, bilingual (TR/EN) what-if analysis tool for managers. It is a single HTML file with no build step or server.

It has six tabs: **Team** (delivery date vs headcount and scope), **Churn** (cash flow vs churn, new customers and collection time), **Pricing** (revenue and cash vs price changes, with break-even churn sensitivity), **Marketing** (budget changes with diminishing returns, marginal CAC, LTV/CAC), **Payroll** (raises, headcount changes and severance) and **Supply** (supplier cost and payment terms).

Every parameter is a variable: use the slider or type any value in the box next to it, even outside the slider range. Company data (customers, revenue, expenses, cash, collection and payment terms) is shared by all tabs. Use the TR / EN toggle at the top right to switch language; your choice and values are stored in the browser only.

All figures are **sample data**. Results are decision-support estimates that depend entirely on your assumptions. The models intentionally leave out taxes, inflation, FX, seasonality and customer segments.

# What-If Desk

Yöneticiler için mobil uyumlu, iki dilli (TR/EN) **what-if (ya olursa) analiz aracı**. Tek dokunuşla bir karar simüle edilir: "Yazılım ekibine 2 kişi eklersek gecikme nasıl etkilenir?", "Churn 1 puan artarsa nakit akışı önümüzdeki çeyrekte nasıl değişir?"

Tek bir HTML dosyasıdır (`senaryo-masasi.html`). Sunucu, derleme adımı ya da harici veri gerektirmez. Tarayıcıda açmak yeterlidir.

> **Önemli:** Uygulamadaki tüm rakamlar **örnek şirket verisidir**. Kendi rakamlarınızı "Varsayımlar" bölümünden girin.

---

## Senaryolar

| Sekme | Soru | Ana çıktılar |
|---|---|---|
| **Ekip** | Ekibe kişi eklersek veya kapsam değişirse teslim ne zaman olur? | Tahmini teslim haftası, hedefe göre gecikme (iş günü), ek maliyet, kazanılan hafta başına maliyet, hedefi tutturmak için gereken en az kişi |
| **Churn** | Aylık churn, yeni müşteri veya tahsilat süresi değişirse nakit nasıl etkilenir? | Çeyrek sonu nakit, çeyrek net nakit akışı, 12. ay nakit farkı, yıllıklandırılmış gelir etkisi, runway |
| **Fiyat** | Fiyat artarsa veya düşerse gelir ve nakit ne olur? | 12 ay nakit farkı, 12. ay geliri, **başa baş churn duyarlılığı** |
| **Pazarlama** | Pazarlama bütçesi artarsa veya azalırsa? | Ek müşteri, ek müşteri maliyeti (marjinal CAC), geri ödeme süresi, LTV/CAC |
| **Maaş** | Maaş zammı veya kadro değişimi nakdi nasıl etkiler? | Aylık personel gideri, tazminat, aylık net akış, net akışı sıfırlayan en yüksek zam |
| **Tedarik** | Tedarikçi/altyapı maliyeti veya ödeme vadesi değişirse? | Maliyet etkisi, vade kazancı (tek seferlik), brüt marj |

Her sekmede ortak akış aynıdır:

1. **Soru:** seçimlerinize göre canlı güncellenen cümle.
2. **Hazır senaryolar:** tek dokunuşla yüklenen düğmeler (yatay kaydırılır).
3. **Sonuç kartı:** ana sonuç ve baz duruma göre fark.
4. **Ayarla:** her değişken için kaydırıcı ve değer kutusu.
5. **Göstergeler ve grafik:** baz ile senaryo yan yana.
6. **Yönetici özeti:** otomatik yazılan metin, "Kopyala" düğmesiyle yazışmaya aktarılır.
7. **Varsayımlar:** tüm parametreler ve modelin kısa açıklaması.

---

## Kullanım

- **Dil:** sağ üstteki TR / EN düğmesi. Seçim tarayıcıda hatırlanır.
- **Değer atama:** her değişkenin yanındaki kutuya istediğiniz sayıyı yazın. Kaydırıcı aralığının dışındaki değerler de kabul edilir. Geçersiz girişler (harf vb.) yok sayılır.
- **Ortak şirket verisi:** müşteri, gelir, gider, nakit, tahsilat ve ödeme vadesi tüm sekmelerde **ortaktır**. Bir sekmede değiştirdiğiniz değer diğer sekmelere de yansır.
- **Sıfırlama:** "Varsayılanlara dön" düğmesi o sekmenin varsayımlarını ve ortak şirket verisini örnek değerlere döndürür.
- **Saklama:** değerleriniz yalnızca bu tarayıcıda (`localStorage`) tutulur. Başka cihaza veya kişiye aktarılmaz.

---

## Değişkenler

### Ortak şirket verisi (Churn sekmesinde; diğer sekmelerde "Şirket verisi" bölümü)

| Değişken | Örnek değer |
|---|---|
| Mevcut müşteri | 2.400 |
| Aylık gelir, müşteri başı | ₺2.800 |
| Baz aylık churn | %2,0 |
| Aylık yeni müşteri | 70 |
| Doğrudan maliyet, gelire oranı | %24 |
| Aylık sabit gider | ₺4,3 Mn |
| Müşteri edinme maliyeti (CAC) | ₺5.000 |
| Mevcut nakit | ₺12 Mn |
| Baz tahsilat süresi | 30 gün |
| Baz ödeme vadesi (tedarikçi) | 0 gün |

### Ekip

Senaryo: eklenen kişi, kapsam değişimi, işe alım süresi.
Varsayımlar: mevcut ekip, kalan iş (hikâye puanı), kişi başı haftalık verim, hedef teslim haftası, koordinasyon kaybı, mentorluk yükü, tam verime çıkış süresi, yeni kişinin ilk hafta verimi, ekip verimi alt sınırı, aylık kişi maliyeti.

### Churn

Senaryo: aylık churn değişimi (yüzde puan), yeni müşteri değişimi, tahsilat süresine ek.

### Fiyat

Senaryo: fiyat değişimi, ne zaman başlar.
Varsayımlar: fiyat %1 başına churn duyarlılığı, fiyat %1 başına yeni müşteri duyarlılığı.

### Pazarlama

Senaryo: bütçe değişimi, ne zaman başlar.
Varsayımlar: getiri üssü (1 = doğrusal, 1'in altı = azalan getiri).

### Maaş

Senaryo: maaş zammı, kadro değişimi, ne zaman başlar.
Varsayımlar: personelin sabit giderdeki payı, kadro azaltmada tazminat (aylık maaş), kadro %1 değişince yeni müşteri etkisi.

### Tedarik

Senaryo: tedarik/altyapı maliyeti değişimi, ödeme vadesi uzaması, ne zaman başlar.
Varsayımlar: maliyet değişiminin fiyata yansıtılan payı.

---

## Modeller (kısaca)

**Ekip (haftalık simülasyon).** Yeni kişiler işe alım süresi dolunca katılır, ilk hafta seçilen verimle başlar ve doğrusal olarak %100'e çıkar. Bu sürede mevcut ekipten mentorluk payı düşülür. Ekip büyüdükçe kişi başı koordinasyon kaybı verimi düşürür (Brooks yasası); verim seçilen alt sınırın altına inmez. Teslim, birikmiş işin kalan işe ulaştığı (kesirli) hafta olarak hesaplanır. En fazla 104 hafta simüle edilir.

**Nakit (aylık simülasyon, 12 ay, Kasım 2026 başlangıçlı).**
- Müşteri sayısı: önceki ay × (1 − churn) + yeni müşteri.
- Gelir: müşteri sayısı × müşteri başı gelir. Nakde, tahsilat süresi kadar gecikmeyle döner.
- Giderler: sabit gider + doğrudan maliyet (gelirle orantılı, ödeme vadesiyle) + müşteri edinme harcaması.
- Ödeme vadesi uzarsa ödenmemiş fatura bakiyesi büyür; bu **tek seferlik** nakit rahatlaması yaratır ve vade eski haline dönerse geri verilir.
- "Önümüzdeki çeyrek" ilk 3 ay (Kasım, Aralık, Ocak) demektir.

**Fiyat.** Seçilen aydan sonra tüm müşterilerin geliri değişir. Her %1 fiyat artışı churn'ü ve yeni müşteri kazanımını seçilen duyarlılık kadar etkiler. *Başa baş duyarlılık*, zammın 12. ay nakdini baz durumun altına düşürmediği en yüksek churn duyarlılığıdır (ikili aramayla bulunur).

**Pazarlama.** Yeni müşteri = baz × (1 + bütçe artışı)^üs. Üs 1'in altındaysa her ek lira daha az müşteri getirir. Geri ödeme = ek müşteri maliyeti ÷ müşteri başı aylık brüt kâr. LTV = aylık brüt kâr ÷ aylık churn.

**Maaş.** Personel gideri = sabit gider × personel payı. Zam ve kadro değişimi bu tutarı çarpar. Kadro azaltılırsa ayrılanların maaşı kadar, seçilen ay sayısında tek seferlik tazminat çıkar. Kadro değişimi yeni müşteri kazanımına seçilen oranda yansır.

**Tedarik.** Doğrudan maliyet oranı seçilen yüzde kadar değişir. Maliyet artışının bir kısmı fiyata yansıtılabilir. Maliyet etkisi ve vade kazancı ayrı ayrı gösterilir.

---

## Sınırlar

- Bunlar **karar destek tahminleridir**, kesin öngörü değildir. Sonuçlar girdiğiniz varsayımlara bağlıdır.
- Modeller bilerek basit tutulmuştur: vergi, KDV, enflasyon, döviz, mevsimsellik, ürün karması ve müşteri segmentleri yoktur.
- Churn düşüşü ve fiyat indirimi aynı duyarlılıkla ters yönde işler (simetrik varsayım).
- Kadro değişiminin gelire etkisi tek bir katsayıyla temsil edilir.
- Para birimi Türk lirasıdır (₺). Büyük tutarlar "Mn / M" (milyon) ve "bin / K" olarak gösterilir.

---

## Teknik notlar

- Tek dosya, bağımlılık yok. Yalnızca Google Fonts (Bricolage Grotesque, IBM Plex Sans, IBM Plex Mono) bağlantısı vardır; bağlanamazsa sistem yazı tipleri kullanılır.
- Açık ve koyu tema desteklenir (cihaz ayarını izler).
- Telefon genişliğinde (~400 px) kullanım için tasarlanmıştır; sayfa yatay kaydırılmaz.
- Model fonksiyonları (`simTeam`, `simCashM`, `simPrice`, `simMkt`, `simPay`, `simSup`) arayüzden bağımsız, saf JavaScript fonksiyonlarıdır ve ilk `<script>` bloğundadır.
- Yeni bir senaryo eklemek için: model fonksiyonunu yazın, `DEF` ve `defs()` içinde değişkenlerini ve hazır senaryolarını tanımlayın, bir `render…` fonksiyonu ekleyin ve `GROUPS` ile `RENDER` listelerine kaydedin.

---


