# Yapılacaklar

Kurallar ve formüller: [docs/TASARIM.md](docs/TASARIM.md).

## Nasıl kullanıyoruz
1. İşe başlamadan önce `git pull`.
2. Yalnız **kendi bölümündeki** maddeleri tikle (`- [ ]` → `- [x]`). Böylece aynı satırı iki kişi düzenlemez, çakışma olmaz.
3. Maddeyi bitirince kodla birlikte aynı commit'te tikle: `feat(draft): teklif geri sayımı #C3`.
4. Kendi dalında çalış (`ad/kisa-konu`), PR aç, bir kişi incelesin, **normal merge** (squash yok).
5. `git config user.email` = GitHub hesabının e-postası.
6. Başkasının bölümüne dokunman gerekirse önce ona yaz.

Milestone 1 (12 Kasım 2026, 23:00; geç teslim sıfır) **yalnız tasarım ve mimari** istiyor, kod yok. Kod bölümleri (A-E) Milestone 1'den sonra başlar.

---

## Milestone 1 · Tasarım ve mimari (12 Kasım 23:00)
Teslim dilleri İngilizce. Bütün ekranlar tek ortak Figma dosyasında; hoca "görüntüleyebilir" yetkisiyle eklenir.

**Ekranlar:** S1 Takım oluşturma · S2 Amblem editörü · S3 Ana menü · S4 Kaleci güçlendirmeleri · S5 Eşleşme · S6 Draft (açık artırma) · S7 Plan (diziliş, taktik) · S8 Maç anlatımı · S9 Penaltı ve maç sonu

### K1 · Tasarım dili · Sahibi: ______
- [ ] K1.1 · Renk paleti ve tipografi kararı (10 Kasım sabah, diğerleri buna göre çizer)
- [ ] K1.2 · Figma bileşenleri: oyuncu kartı, buton, geri sayım, bakiye rozeti, amblem çerçevesi
- [ ] K1.3 · `docs/design-justification.pdf` (1-2 sayfa: palet, tipografi, yerleşim, erişilebilirlik, hedef kullanıcı)

### K2 · Akış + S1-S3 · Sahibi: ______
- [ ] K2.1 · `docs/user-flow.pdf` (karar noktalarıyla: takım var mı, eşleşme bulundu mu, teklif kazanıldı mı, beraberlik → penaltı)
- [ ] K2.2 · S1-S3 wireframe
- [ ] K2.3 · S1-S3 mockup

### K3 · S4-S6 · Sahibi: ______
- [ ] K3.1 · S4-S6 wireframe
- [ ] K3.2 · S4-S6 mockup (draft ekranı en önemli ekran: kart, teklif, 3/5 sn sayaç, iki bakiye)

### K4 · S7-S9 · Sahibi: ______
- [ ] K4.1 · S7-S9 wireframe
- [ ] K4.2 · S7-S9 mockup

### K5 · Mimari + prototip · Sahibi: ______
- [ ] K5.1 · `docs/architecture-and-protocols.pdf` (MVVM; katmanlar; arayüzler: `GameService`, `AuctionEngine`, `MatchSimulator`, `TeamRepository`; protokoller: HTTPS, Firestore gerçek zamanlı dinleyici, Firebase Auth token)
- [ ] K5.2 · Figma prototip: S1 → S9 bağlantıları, teklif ve kart geçişleri, animasyonlar
- [ ] K5.3 · `README.md`: proje adı, 5 kişinin adı, Figma linkleri (wireframe, mockup, prototip)

### Herkes
- [ ] H1 · Kendi ekranlarının PNG dışa aktarımını `design/` altına kendi hesabıyla commit'ledi
  - [ ] K1 · [ ] K2 · [ ] K3 · [ ] K4 · [ ] K5

### Teslim (12 Kasım öğlen)
- [ ] T1 · Depo hocaya açık (public ya da hoca eklendi), Google Sheet'e depo linki yazıldı
- [ ] T2 · Figma dosyası "link olan görüntüleyebilir"; linkler gizli pencerede açılıyor
- [ ] T3 · README, 3 PDF ve linkler GitHub'da açılıyor
- [ ] T4 · Depo ZIP indirildi, `Team#_MTM4186_MS.zip` adıyla online.yildiz.edu.tr'ye yüklendi

---

## Kod: ortak hazırlık (Milestone 1'den sonra)
- [ ] O1 · GitHub deposu açıldı, 4 kişi Collaborator olarak eklendi (Milestone 1'de, ilk gün)
- [x] O2 · `flutter create`, klasör yapısı, `.gitignore`, `analysis_options.yaml` (Kadir Burak, Flutter 3.47.9)
- [ ] O3 · `main` dalı korumalı, PR'da 1 onay şartı (E)
- [ ] O4 · Model sınıflarının taslağı `main`'de; diğerleri bunlarla sahte veriyle başlar (A)
- [ ] O5 · Herkes `flutter doctor` temiz ve uygulamayı kendi cihazında çalıştırdı (herkes kendi satırını tikler)
  - [ ] A · [ ] B · [ ] C · [ ] D · [ ] E

---

## A · Oyun çekirdeği (`lib/core/`) · Sahibi: ______
- [ ] A1 · Modeller: `PlayerCard`, `Position`, `PlayStyle`, `Team`, `Formation`, `Tactic` (+ `fromJson` / `toJson`)
- [ ] A2 · Kurgusal oyuncu verisi: `assets/data/players.json`, 150-200 oyuncu (ad, mevki, stil, overall, DEF, ATK, PAS)
- [ ] A3 · Havuz üretici: 12 kart, mevki dağılımı değişken, 2-3 yıldız / 5-6 orta / 3-4 zayıf; tohumla tekrarlanabilir
- [ ] A4 · Açık artırma motoru (saf Dart, saat dışarıdan verilir): 3 sn açılış hakkı, 5 sn yenilenen pencere, son teklifi veren üst üste veremez, teklif yoksa bedava açılış sahibine
- [ ] A5 · Doluluk ve bakiye kuralları: 6 kart dolunca kalanlar karşıya, bakiye yetmezse teklif yok
- [ ] A6 · Birim testleri: A3-A5'in bütün kenar durumları
- [ ] A7 · Kaleci modeli ve 20 güçlendirmenin listesi (ad, etki, açılma koşulu)

## B · Simülasyon (`lib/core/sim/`) · Sahibi: ______
- [ ] B1 · Mevki cezası tablosu (doğal 0, komşu −3, bir hat −8, iki hat −15) + test
- [ ] B2 · Kimya hesabı (oyuncu başı 0-3, takıma 0..+4) + test
- [ ] B3 · Taktik eşleşmesi (Pres > Sahip olma > Kontra > Pres, ±1,5) + test
- [ ] B4 · Takım puanı fonksiyonu (A'nın modelleriyle)
- [ ] B5 · Poisson skor üretimi (μ = 1,6, β = 0,115), tohumla tekrarlanabilir
- [ ] B6 · Penaltı atışları (ATK + kaleci güçlendirmeleri)
- [ ] B7 · Kalibrasyon testi: 10 bin maçta Δ=5 → %70 ± 2, Δ=1 → %54 ± 2
- [ ] B8 · Anlatım üretici: dakikalı olay listesi (gol, kaçan pozisyon, kurtarış, kart) + Türkçe metin şablonları (en az 40 şablon)

## C · Draft ve maç ekranları (`lib/features/draft/`, `lib/features/match/`) · Sahibi: ______
- [ ] C1 · Kart widget'ı (FIFA tarzı: overall, mevki, stil, DEF / ATK / PAS)
- [ ] C2 · Draft ekranı iskeleti: ortadaki kart, iki takımın bakiyesi ve aldığı kartlar
- [ ] C3 · Teklif butonları (+1, +5, özel tutar) ve geri sayım çubuğu (3 sn / 5 sn)
- [ ] C4 · Teklif kapanınca kartın kazanana gitme animasyonu
- [ ] C5 · Maç ekranı: dakika çizgisi, mesaj akışı, canlı skor
- [ ] C6 · Penaltı ekranı ve maç sonu özeti
- [ ] C7 · Widget testleri (kart, geri sayım)

## D · Takım kimliği ve plan (`lib/features/team/`, `lib/features/plan/`) · Sahibi: ______
- [ ] D1 · Takım oluşturma: ad, kısaltma, doğrulama (uzunluk, küfür, gerçek kulüp adı engeli)
- [ ] D2 · Amblem editörü: şekil, desen, iki renk, simge, yazı; `CustomPainter` ile canlı önizleme; JSON kaydı
- [ ] D3 · Amblem parçaları: 8-10 şekil, 4 desen, 20-30 simge
- [ ] D4 · Plan ekranı: diziliş seçimi (2-3-1, 3-2-1, 2-2-2, 3-1-2)
- [ ] D5 · Oyuncuyu mevkiye sürükle-bırak; mevki cezasını ve kimyayı anlık göster (B'nin fonksiyonları)
- [ ] D6 · Taktik seçimi ve plan geri sayımı; rakibin oyuncuları görünür, dizilişi görünmez
- [ ] D7 · Kaleci ekranı: 3 güçlendirme seçimi

## E · Online ve uygulama iskeleti (`lib/app/`, `lib/services/`, `functions/`) · Sahibi: ______
- [ ] E1 · Navigasyon ve tema (açılış → takım → eşleşme → draft → plan → maç → sonuç)
- [ ] E2 · `GameService` arayüzü + sahte (yerel) uygulaması; herkes online beklemeden test eder
- [ ] E3 · Firebase projesi, anonim giriş, takım profilini kaydetme
- [ ] E4 · Eşleşme kuyruğu ve oda oluşturma (Firestore)
- [ ] E5 · Teklifleri sunucu doğrulasın (Cloud Functions): süre, bakiye, "üst üste teklif yok", kart sahipliği
- [ ] E6 · Simülasyonu sunucuda çalıştırıp sonucu iki tarafa yaz (hile olmasın)
- [ ] E7 · Bağlantı kopması: süre dolunca otomatik pas, maçtan düşen kaybeder
- [ ] E8 · Rakip bulunamazsa bot (A4 + B'nin fonksiyonlarıyla basit teklif stratejisi)

---

## Sonraki teslimler
- [ ] Final sunumu ve demo videosu
