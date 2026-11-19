# Third Party Notices

Bu projede kullanılan üçüncü parti asset paketlerinin listesi.

**Bu paketlerin dosyaları GitHub'da YOKTUR.** Lisans nedeniyle `Assets/ThirdParty/` klasörü `.gitignore` ile repo dışında tutulur. Projeyi açmadan önce aşağıdaki listedeki paketleri kendi bilgisayarınıza indirip kurmanız gerekir.

## Kurulum

1. Projeyi klonlayın (`git lfs install` yapılmış olmalı).
2. Unity'de projeyi açın. İlk açılışta eksik paket kaynaklı hatalar normaldir.
3. Aşağıdaki tablodaki her paketi, belirtilen sürümle indirip **`Assets/ThirdParty/<Paket Adı>/`** altına import edin.
4. Mümkünse **aynı sürümü** kullanın. Aksi halde prefab ve sahne referansları kırılabilir.
5. Paketler tamamlanınca konsolda hata kalmadığını kontrol edin.

## Paket Listesi

| # | Paket adı | Sürüm | Kaynak (link) | Lisans | Zorunlu mu? | Kullanıldığı yer |
|---|-----------|-------|---------------|--------|-------------|------------------|
| 1 | _örnek: Paket Adı_ | _1.0.0_ | _https://..._ | _Standard Asset Store EULA_ | _Evet / Hayır_ | _Player, Terrain, ..._ |

## Yeni paket eklerken

- Paketi `Assets/ThirdParty/<Paket Adı>/` altına import edin (başka yere değil).
- Bu tabloya satır ekleyin: ad, sürüm, kaynak linki, lisans, zorunlu olup olmadığı.
- `git status` ile paketin dosyalarının listede **görünmediğini** kontrol edin.
- Bir asmdef, prefab veya sahne bu pakete referans veriyorsa "Kullanıldığı yer" sütununa yazın.
