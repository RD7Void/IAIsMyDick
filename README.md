# IA is my dick

**Removedor de metadados de imagem com detector automático de geração por IA — 100% local, nada sai do seu dispositivo.**

Escaneia o arquivo byte a byte (APP1/APP0 do JPEG, chunks do PNG, RIFF do WEBP, blocos do GIF), mostra exatamente o que está escondido, detecta assinaturas de geradores de IA e recorta os metadados **sem recompressão** — qualidade idêntica, arquivo sempre menor ou igual.

> Repo: `RD7VOID/IAIsMyDick`

---

## Por quê?

Toda foto que você tira ou gera carrega dados escondidos: GPS, modelo do celular, hora exata, e — quando a imagem veio de IA — a assinatura do gerador (Midjourney, DALL·E, Stable Diffusion, Firefly, Flux, C2PA…). Redes sociais **recomprimem** a imagem e, no processo, podem *preservar* metadados de IA. A limpeza aqui é cirúrgica: os blocos de metadado são removidos e o resto é reconcatenado byte a byte.

## Funcionalidades

- **Remoção sem perda** — sem recompressão, pixel idêntico, arquivo menor
- **Detector de IA** — ~20 regras de assinatura (EXIF, XMP, IPTC, comentários, C2PA) com veredito e nível de confiança
- **Processamento em lote** — analise e limpe várias imagens de uma vez, com relatório JSON exportável
- **Inspeção completa** — veja campo por campo do que a imagem carrega
- **Tema personalizável** — claro/escuro + cor de destaque escolhida pelo usuário (persistida)
- **Multiplataforma** — Windows, Android, iOS e Web (PWA)

## Formatos suportados

| Formato | Remoção | Detector de IA |
|---------|:-------:|:--------------:|
| JPEG / JPG | ✅ | ✅ |
| PNG | ✅ | ✅ |
| WEBP | ✅ | ✅ |
| GIF | ✅ | ✅ |

## Privacidade

- Nenhuma rede, nenhuma nuvem, nenhuma telemetria
- O arquivo é lido e processado inteiramente na memória do seu dispositivo
- O arquivo limpo é salvo na pasta original (ou na que você configurar)

## Download

| Plataforma | Como obter |
|---|---|
| **Windows** | `Release` → `ai_is_my_dick.exe` (portátil) |
| **Android** | `Release` → `app-arm64-v8a-release.apk` (instalar de fontes desconhecidas) |
| **Web** | GitHub Pages / deploy próprio (`flutter build web`) |
| **iOS** | Compilar no macOS (`flutter build ios`) |

## Build do zero

Pré-requisito: [Flutter SDK](https://docs.flutter.dev/get-started/install) 3.x

```bash
git clone https://github.com/RD7VOID/IAIsMyDick.git
cd IAIsMyDick
flutter pub get

# Windows
flutter build windows --release

# Android (APK universal)
flutter build apk --release
# Android (APK otimizado por arquitetura)
flutter build apk --release --split-per-abi

# Web
flutter build web --release
```

## Estrutura do projeto

```
lib/
├── main.dart              # bootstrap
├── app.dart               # MaterialApp + casca responsiva
├── core/
│   ├── models.dart        # ImageScan, AiAnalysis, vereditos
│   ├── scanner.dart       # parser byte-a-byte (JPEG/PNG/WEBP/GIF)
│   ├── platform_io.dart   # abstração de I/O (desktop/mobile vs web)
│   └── desktop_window.dart# janela de desktop (stub na web)
├── state/
│   └── app_state.dart     # estado global + persistência
├── theme/
│   ├── tokens.dart        # paleta (acento customizável)
│   └── app_theme.dart     # ThemeData claro/escuro
└── ui/
    ├── shell.dart         # fundo ambiente, sidebar, HUD, nav inferior
    ├── title_bar.dart     # barra de título tematizada (desktop)
    ├── widgets.dart       # cards, botões, chips
    └── pages/             # painel, remoção, detector, lote, configurações
```

## Responsividade

- **≥ 1040px** — layout completo com sidebar e painéis lado a lado
- **640–1040px** — sidebar compacta, colunas empilham
- **< 640px (celular)** — sidebar sai, entra barra de navegação inferior; HUD mostra só o essencial

## Stack

[Flutter](https://flutter.dev) (Dart) · `file_picker` · `shared_preferences` · `window_manager` · zero dependências de rede

## Licença

Defina aqui a licença do projeto (ex.: MIT, GPL-3.0). Sugestão: criar o arquivo `LICENSE` e referenciá-lo neste README.

---

*Feito para quem se importa com o que uma foto revela.*
