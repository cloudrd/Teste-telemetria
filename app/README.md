# FMS Telemetria — esboço com captura em segundo plano

App Android (via Capacitor) que reaproveita o esboço web de telemetria
(https://cloudrd.github.io/Teste-telemetria/), mas usando o plugin
`@capacitor-community/background-geolocation` pra continuar capturando GPS
mesmo com a tela apagada ou o app em segundo plano.

## Como pegar o APK

A cada push na branch `main`, o GitHub Actions compila o APK automaticamente
(veja a aba "Actions" ou "Releases" deste repositório) — não precisa Android
Studio nem nada instalado localmente.

## Estrutura

- `www/index.html` — mesma interface do esboço web, com detecção automática:
  roda como app nativo (fundo ativo) ou cai pro modo navegador (só primeiro
  plano) se aberto fora do Capacitor.
- `android/` — projeto Android gerado pelo Capacitor.
- `.github/workflows/build-apk.yml` — build automático na nuvem.

## Build manual (se tiver Android Studio)

```
npm install
npx cap sync android
cd android
./gradlew assembleDebug
```
