# Kıvılcım — Türkçe Araştırma Laboratuvarı

Meraktan keşfe: yöntemleri keşfet, varsayımları değiştir, deney sonuçlarını kaydet.

## Çalışan özellikler
- Türkçe, mobil uyumlu keşif atlası ve altı etkileşimli yöntem kartı.
- Batarya kapasitesi, güneş paneli gücü, akşam tarifesi ve çevrim verimiyle değişen 24 saatlik enerji simülasyonu.
- Bataryalı / bataryasız maliyet karşılaştırması, enerji grafiği, saatlik CSV dışa aktarımı.
- Yöntem, deney ve kişisel notları tarayıcı localStorage alanında tutan araştırma defteri.

## Çalıştırma

Derleme veya API anahtarı gerekmez. Python 3 ile:

```sh
python -m http.server 8080 --directory dist
```

Ardından http://localhost:8080 adresini açın. Herhangi bir statik sunucu da kullanılabilir. Google Fonts isteğe bağlıdır; yüklenmezse sistem yazı tipleri kullanılır.

## Model sınırları

Sentetik tüketim ve güneş profili kullanılır. Bu uygulama gerçek makale sonuçlarını yeniden üretmez ve bağlı bir yapay zekâ modeli içermez. Harita kavramsaldır; atıf ağı değildir. PDF içe aktarma, otomatik literatür tarama, kaynaklı AI yanıtları ve güvenli deney yürütme gelecekteki geliştirmelerdir.

Başlangıç batarya enerjisi sıfırdır. Fazla güneş üretimi bataryayı doldurur. Gece 00–05 saatlerinde şebekeden şarj; 17–21 saatlerinde deşarj uygulanır. Güç sınırı 3 kW, iki yöndeki verim çevrim veriminin kareköküdür. Gece 0,12 €/kWh, gündüz 0,23 €/kWh, akşam kullanıcının seçtiği örnek tarife kullanılır. Strateji optimal değildir. Yatırım, yıpranma, vergi, ihracat geliri ve gün sonu enerji değeri yoktur.

Kayıtlar yalnızca kullanılan tarayıcıdadır. Veriler silinirse notlar kaybolur; cihazlar arası senkronizasyon yoktur.

## Doğrulama

JavaScript sözdizimi kontrolü ve 108 parametre kombinasyonunda enerji dengesi, batarya kapasite sınırları, negatif olmayan şebeke tüketimi ve sıfır bataryada eşit maliyet kontrol edildi. Tarayıcıda ana ekran ve deney akışı kontrol edildi.

## Dosyalar

- `dist/index.html`: ekranlar ve Türkçe metinler
- `dist/style.css`: responsive tasarım
- `dist/app.js`: yöntem atlası, simülasyon, grafik, yerel kayıt ve CSV

## Geliştirme yönü

1. Makale kimliği ve alıntı konumu korunarak PDF işleme.
2. Kaynağa dayalı Türkçe soru-cevap; desteklenmeyen iddiaların ayrılması.
3. Makale / varsayım / deney / sonuç arasında izlenebilir bağlantılar.
4. İzole ortamda tekrar üretilebilir deneyler ve basit temel yöntemlerle kıyaslama.
5. Sentetik verilerden açıkça ayrılmış gerçek veri setleri.
