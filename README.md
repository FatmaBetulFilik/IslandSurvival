# IslandSurvival

Multiplayer (host/client) ada hayatta kalma oyunu. Unity 6, URP ve Netcode for GameObjects ile geliştirilmektedir.

## Gereksinimler

| Araç | Sürüm |
|---|---|
| Unity | **6000.3.26f1** (başka sürüm kullanmayın) |
| Render pipeline | Universal Render Pipeline (URP) |
| Git | 2.40+ |
| Git LFS | 3.x |
| Kod editörü | VS Code (önerilen) |

## Kurulum

### 1. Repoyu klonla

```bash
git lfs install
git clone https://github.com/FatmaBetulFilik/IslandSurvival.git
```

`git lfs install` komutu klonlamadan **önce** çalıştırılmalıdır. Aksi halde LFS dosyaları metin işaretçisi olarak iner ve bozuk görünür.

### 2. Smart Merge (UnityYAMLMerge) ayarı

Sahne ve prefab çakışmalarını otomatik çözmek için gereklidir. Bu ayar repoyla gelmez, her bilgisayarda bir kez yapılır.

`IslandSurvival/.git/config` dosyasının sonuna ekleyin ve Unity kurulum yolunu kendi bilgisayarınıza göre değiştirin:

```ini
[merge "unityyamlmerge"]
	name = Unity SmartMerge (UnityYAMLMerge)
	driver = "C:/UNITY_KURULUM_YOLU/6000.3.26f1/Editor/Data/Tools/UnityYAMLMerge.exe" merge -h -p --force %O %B %A %A
	recursive = binary
```

Yolda ters eğik çizgi (`\`) değil, düz eğik çizgi (`/`) kullanın. Kontrol etmek için:

```bash
git config --get merge.unityyamlmerge.driver
```

### 3. Üçüncü parti asset'leri indir

Lisans nedeniyle üçüncü parti asset'ler **repoda bulunmaz**. `Assets/ThirdParty/` klasörü `.gitignore` ile dışarıda tutulur.

1. [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) dosyasındaki listeye bakın.
2. Her paketi belirtilen sürümle indirip `Assets/ThirdParty/<Paket Adı>/` altına import edin.
3. Unity konsolunda hata kalmadığını kontrol edin.

### 4. Projeyi aç

Unity Hub → **Add project from disk** → klonlanan klasörü seçin. Unity 6000.3.26f1 ile açın. İlk açılış, `Library` klasörü oluşturulacağı için uzun sürebilir.

## Proje yapısı

```
Assets/
  _Project/                 Bu projeye ait her şey
    Art/                    Materyaller, ortam
    Prefabs/                Building, Network, Player, World
    Scenes/                 Main, Test
    Scripts/                IslandSurvival.Runtime asmdef'i buradadır
      Building/ Crafting/ Networking/ Player/ UI/
  Scenes/                   Unity şablonunun örnek sahnesi
  Settings/                 URP ayarları
  ThirdParty/               Repoda YOK, her geliştirici kendisi doldurur
Packages/                   Paket listesi (manifest.json)
ProjectSettings/            Proje ayarları
```

## Kod kuralları

- Tüm oyun scriptleri `Assets/_Project/Scripts/` altında olmalıdır. Bu klasör `IslandSurvival.Runtime` assembly'sine dahildir. Scripti bu klasörün dışına koyarsanız `Assembly-CSharp`'a düşer ve Runtime kodunu göremez.
- Namespace kökü `IslandSurvival` olmalıdır (örn. `IslandSurvival.Networking`).
- Dosya adı ile sınıf adı aynı olmalıdır.
- `UnityEditor` kullanan kod oyun scriptlerine yazılmamalıdır, build'i bozar.

## Git kuralları

- Commit'ten önce `git status` ile `Library`, `Logs`, `UserSettings`, `*.csproj` ve `Assets/ThirdParty` dosyalarının listede **olmadığını** kontrol edin.
- `.meta` dosyaları mutlaka commit edilir, asla silinmez.
- Yeni üçüncü parti paket eklerken `THIRD_PARTY_NOTICES.md` tablosunu güncelleyin.
- Büyük binary dosyalar (görsel, ses, model) Git LFS ile takip edilir. Kurallar `.gitattributes` içindedir.
- Aynı sahne veya prefabı iki kişi aynı anda düzenlememelidir.

## Lisans

Bu projenin kaynak kodu ve içeriği için [LICENSE](LICENSE) dosyasına bakın. Üçüncü parti asset'lerin lisansları kendi sahiplerine aittir ve [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) dosyasında listelenmiştir.
