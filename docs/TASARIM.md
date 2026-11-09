# Oyun tasarımı (kör draft 7'ye 7)

Ekibin ortak başvuru belgesi. Kural değişirse önce burası güncellenir, sonra kod.

## Akış
1. **Hazırlık:** Kullanıcının takımı kendisi: takım adı, kısaltma, amblem. Kaleci sabit ve takıma ait; maça girmeden açılmış 20 güçlendirmeden 3'ü seçilir.
2. **Eşleşme:** online 1v1.
3. **Draft:** 12 kart, kör, sırayla açılır (kaleci yok). Herkes 6 kart alır.
4. **Plan:** süreli (öneri 45-60 sn). Diziliş, oyuncu yerleşimi, taktik. Rakibin oyuncuları görünür, dizilişi görünmez.
5. **Maç:** simülasyon; dakika dakika metin anlatımı. Beraberlikte penaltı.

## Draft kuralları
- Bakiye 30. En düşük teklif 1, artış en az 1; istenen miktarla atlanabilir (örn. doğrudan 5).
- Her kartta açılış hakkı sırayla değişir (ilk kartın sahibi rastgele).
- Kart açılınca **3 sn** yalnız açılış hakkı sahibi teklif verebilir.
- Ardından **5 sn** pencere: iki taraf da teklif verebilir, her teklif süreyi 5 sn'ye yeniler. Teklif sırası yok; yalnız **son teklifi veren üst üste teklif veremez**.
- Hiç teklif gelmezse kart **bedava** açılış hakkı sahibine gider.
- Süre dolunca kart son teklifi verene gider, teklif bakiyesinden düşer.
- Biri 6 kartı doldurursa kalan kartlar diğerine gider.
- Parası yetmeyen teklif veremez; kalan kartların dağılımını parası olan yönetir.
- Artan paranın maç sonunda değeri yoktur.

## Havuz
- 12 kart; DEF / ORTA / FORVET kabaca eşit ama her maç 4-4-4 değil (3-5-4 gibi). Yapı oyuncuya söylenmez.
- Güç dağılımı: 2-3 yıldız (85-90), 5-6 orta (75-82), 3-4 zayıf (65-72).
- Oyuncular **kurgusal**; gerçek oyuncu, kulüp, foto, FIFA reytingi yok. Benzetme isim de yok.

## Kart
- Alanlar: ad, mevki, oyun stili (Hızlı / Teknik / Fizik / Lider), overall, DEF, ATK, PAS.
- Mevkiler: STP, BEK, DOS, OOS, KANAT, SANTRAFOR.

## Takım puanı
```
puan = mevki cezalı overall ortalaması + kimya (0..+4) + taktik (±1,5) + kaleci katkısı
```
- **Mevki cezası:** doğal 0 · komşu −3 (kanat ↔ bek, OOS ↔ santrafor, DOS ↔ STP) · bir hat öte −8 · iki hat öte −15 (santrafor → defans).
- **Kimya:** oyuncu başı 0-3: doğal mevki +1, dizilişte bağlı komşuyla uyumlu stil +1, dizilişin o mevkiden istediği stil +1. Toplam 0-18 → takım puanına 0..+4 (doğrusal).
- **Taktik:** Pres > Topa sahip olma > Kontra > Pres. Kazanan +1,5, kaybeden −1,5, aynıysa 0.
- **Dizilişler (öneri):** 2-3-1, 3-2-1, 2-2-2, 3-1-2.

## Simülasyon
- Δ = puan_A − puan_B. Gol sayıları Poisson:
  `λ_A = 1,6 · e^(0,115·Δ/2)`, `λ_B = 1,6 · e^(−0,115·Δ/2)`
- Hedef (100 bin maçlık Monte Carlo ile ayarlandı): Δ=1 → %54, Δ=2 → %58, Δ=5 → %70, Δ=10 → %85. Beraberlik ~%21 → penaltı.
- Penaltı: 5'er atış, sonra tek tek; atış başarısı şutörün ATK'sına ve kaleci güçlendirmelerine bağlı.
- Önem sırası: draft > düzen ve kimya > şans.

## Anlatım
- Önce skor hesaplanır. Goller rastgele dakikalara dağıtılır, aralara kaçan pozisyon ve kurtarışlar eklenir.
- Golcü ATK ağırlıklı, asistçi PAS ağırlıklı seçilir. Metin şablondan: "34' Kaan uzaktan vurdu, top ağlarda!"

## Kaleci
- Sabit, takıma ait. Güçlendirmeler oynadıkça açılır; hiçbir birleşim "asla gol yemeyen" kaleci yapmaz.

## Takım kimliği
- Ad 3-20 karakter, kısaltma 2-4 harf; küfür filtresi + gerçek kulüp adı engeli.
- Amblem hazır parçalardan: şekil, desen, iki renk, simge, yazı. JSON olarak saklanır; fotoğraf yükleme yok.

## Sonraya
Lig, MMR/ELO, koleksiyon.
