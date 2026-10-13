# IA is my dick

**Removedor de metadados de imagem com detector automático de geração por IA — 100% local, nada sai do seu dispositivo.**

Escaneia o arquivo byte a byte (APP1/APP0 do JPEG, chunks do PNG, RIFF do WEBP, blocos do GIF), mostra exatamente o que está escondido, detecta assinaturas de geradores de IA e recorta os metadados **sem recompressão** — qualidade idêntica, arquivo sempre menor ou igual.

> Repo: `RD7Void/IAIsMyDick`

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

Baixe na [página de releases (v1.0)](https://github.com/RD7Void/IAIsMyDick/releases/tag/1.0):

[![Download APK Android](https://img.shields.io/badge/Android-APK_ARM64-3DDC84?style=for-the-badge&logo=android&logoColor=white)](https://github.com/RD7Void/IAIsMyDick/releases/tag/1.0)
[![Download APK Android antigo](https://img.shields.io/badge/Android_antigo-APK_ARMv7-3DDC84?style=for-the-badge&logo=android&logoColor=white)](https://github.com/RD7Void/IAIsMyDick/releases/tag/1.0)
[![Download Windows](https://img.shields.io/badge/Windows-ZIP_port%C3%A1til-0078D4?style=for-the-badge&logo=windows&logoColor=white)](https://github.com/RD7Void/IAIsMyDick/releases/tag/1.0)

| Plataforma | Arquivo |
|---|---|
| **Android** | `app-arm64-v8a-release.apk` — celulares modernos (recomendado) |
| **Android (antigo)** | `app-armeabi-v7a-release.apk` |
| **Windows** | `IAIsMyDick_Win.zip` — portátil: extraia e execute o `ai_is_my_dick.exe`, não precisa instalar |

> No Android, permita "instalar de fontes desconhecidas" ao abrir o APK.

---

*Feito para quem se importa com o que uma foto revela.*
