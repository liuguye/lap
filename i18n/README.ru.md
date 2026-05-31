<div align="center">
  <img src="../docs/public/icon.png" alt="Логотип Lap" width="120" style="border-radius: 20px">
  <h1>Lap — Приватный локальный менеджер фотографий</h1>
  <h3>Менеджер фотографий с открытым исходным кодом для macOS, Windows и Linux.</h3>
  <p>
    <a href="https://github.com/julyx10/lap/releases"><img src="https://img.shields.io/github/v/release/julyx10/lap" alt="GitHub release"></a>
    <a href="https://github.com/julyx10/lap/releases"><img src="https://img.shields.io/github/downloads/julyx10/lap/total" alt="GitHub all releases"></a>
    <a href="https://github.com/julyx10/lap/stargazers"><img src="https://img.shields.io/github/stars/julyx10/lap" alt="GitHub stars"></a>
  </p>
</div>

[English](../README.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | [Español](README.es.md) | [Português](README.pt.md) | Русский | [简体中文](README.zh-CN.md) | [日本語](README.ja.md) | [한국어](README.ko.md)

Lap — это локальный менеджер фотографий с открытым исходным кодом, созданный для просмотра семейных альбомов, быстрого поиска старых снимков и управления огромными медиабиблиотеками без доступа к интернету.
Это приватная альтернатива облачным сервисам: никакой принудительной загрузки, локальный поиск на базе ИИ, рабочий процесс на основе папок и бесплатное использование.

- Сайт: [https://julyx10.github.io/lap/](https://julyx10.github.io/lap/)
- Демо-видео: [https://youtu.be/RbKqNKhbVUs](https://youtu.be/RbKqNKhbVUs)
- Конфиденциальность: [PRIVACY.md](../PRIVACY.md)

## Скачать Lap

Откройте [страницу последних релизов](https://github.com/julyx10/lap/releases/latest) и скачайте файл, подходящий для вашей системы:

| Платформа | Пакет | Примечание |
| :-- | :-- | :-- |
| **macOS (Apple Silicon / Intel)** | `_aarch64.dmg` / `_x64.dmg` | Нотариально заверено Apple |
| **Windows 10/11 (x64 / ARM64)** | `_x64_en-US.msi` / `_arm64_en-US.msi` | Без подписи — если SmartScreen блокирует загрузку, нажмите **Все равно сохранить** |
| **Linux (amd64 / arm64)** | `_amd64.deb` / `_arm64.deb` | Для дистрибутивов на базе Debian (Ubuntu, Debian, Linux Mint и т.д.) |

## Скриншоты

<p align="center">
  <img src="../docs/public/screenshots/lap-home-0.1.10_1.png" alt="Скриншот локального менеджера фото Lap" width="900">
</p>

<p align="center">
  <img src="../docs/public/screenshots/lap-home-0.1.10_2.png" alt="Скриншот локального ИИ-поиска фото Lap" width="900">
</p>

## Почему Lap

- **Облако не требуется**: храните свою библиотеку на собственном диске, а не на стороннем сервисе.
- **Приватность по умолчанию**: вся обработка происходит локально, ваши фотографии остаются под вашим контролем.
- **Бесплатно**: никаких подписок или периодических платежей.
- **Работа с папками**: работайте напрямую с существующими папками, этап импорта не требуется.
- **Высокая производительность для больших библиотек**: оптимизировано для плавного просмотра и организации огромных медиаколекций (100 000+ файлов в одной библиотеке).

## Возможности

- **Просмотр и фильтрация** по дате, месту, камере, объективу, тегам, избранному, рейтингу и лицам (BETA).
- **Управление несколькими библиотеками** и быстрое переключение между ними.
- **Поиск дубликатов** и пакетное перемещение ненужных копий в корзину.
- **Редактирование на месте**: обрезка, поворот, отражение, изменение размера и базовые настройки изображения.
- **Синхронизация папок**: операции, учитывающие изменения в файловой системе, и ручное обновление.
- **Локальный ИИ-поиск**: поиск по тексту/изображению, поиск похожих изображений, кластеризация лиц и умные теги.
- **Поиск более чем на 50 языках** с опциональными многоязычными моделями, доступными как дополнительная загрузка при необходимости.
- **Поддержка современных форматов**: WebP, HEIC/HEIF/HIF, AVIF и JXL (JPEG XL).
- **Просмотр RAW**: встроенное декодирование более чем 20 форматов RAW (CR2, NEF, ARW, DNG и др.).
- **Широкая совместимость видео**: поддержка MP4, MOV, AVI, MKV и более 20 других форматов с кроссплатформенной оптимизацией.

## Сборка из исходников

Требования: Node.js 20+, pnpm, Rust stable.

```bash
# Системные зависимости macOS
xcode-select --install
brew install nasm pkg-config autoconf automake libtool cmake

# Системные зависимости Linux
# sudo apt install libwebkit2gtk-4.1-dev libappindicator3-dev librsvg2-dev \
#   patchelf nasm clang pkg-config autoconf automake libtool cmake

# Клонирование и сборка
git clone --recursive https://github.com/julyx10/lap.git
cd lap
git submodule update --init --recursive
cargo install tauri-cli --version "^2.0.0" --locked
./scripts/download_models.sh            # Windows: .\scripts\download_models.ps1
./scripts/download_ffmpeg_sidecar.sh    # Windows: .\scripts\download_ffmpeg_sidecar.ps1
cd src-vite && pnpm install && cd ..
cargo tauri dev
```

## Поддерживаемые форматы

| Тип | Форматы |
| :--- | :--- |
| Изображения | JPG/JPEG, PNG, GIF, BMP, TIFF, WebP, HEIC/HEIF/HIF, AVIF, JXL |
| RAW-фото | CR2, CR3, CRW, NEF, NRW, ARW, SRF, SR2, RAF, RW2, ORF, PEF, DNG, SRW, RWL, MRW, 3FR, MOS, DCR, KDC, ERF, MEF, RAW, MDC |
| Видео | MP4, MOV, M4V, MKV, AVI, FLV, TS/M2TS, WMV, WebM, 3GP/3G2, F4V, VOB, MPG/MPEG, ASF, DIVX и другие. Воспроизведение H.264 поддерживается на всех платформах с автоматической обработкой совместимости, если нативное воспроизведение недоступно. HEVC/H.265 и VP9 поддерживаются нативно в macOS. |

### Примечания по воспроизведению видео в Linux

В Linux Mint/Ubuntu/Debian установите эти пакеты для лучшей поддержки воспроизведения видео:

```bash
sudo apt install gstreamer1.0-libav gstreamer1.0-plugins-good
```

## Архитектура

- Ядро: Tauri + Rust
- Фронтенд: Vue + Vite + Tailwind CSS
- Данные: SQLite

### Ключевые библиотеки

| Библиотека | Назначение |
| :-- | :-- |
| [LibRaw](https://github.com/LibRaw/LibRaw) | Декодирование RAW-изображений и извлечение миниатюр |
| [libheif](https://github.com/strukturag/libheif) | Декодирование HEIC/HEIF/HIF изображений и генерация превью |
| [FFmpeg](https://ffmpeg.org/) | Обработка видео и генерация миниатюр |
| [ONNX Runtime](https://onnxruntime.ai/) | Локальный движок вывода ИИ-моделей |
| [CLIP](https://github.com/openai/CLIP) | Поиск сходства изображений и текста |
| [InsightFace](https://github.com/deepinsight/insightface) | Обнаружение и распознавание лиц |
| [Leaflet](https://leafletjs.com/) | Интерактивная карта для фото с геометками |
| [daisyUI](https://daisyui.com/) | Библиотека UI-компонентов |

## Лицензия

GPL-3.0-or-later. См. [LICENSE](../LICENSE).
