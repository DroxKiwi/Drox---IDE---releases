# Drox IDE — Releases

Canal public de distribution **binaires uniquement** (sans sources).

| Ressource | Description |
|-----------|-------------|
| [Releases GitHub](https://github.com/DroxKiwi/Drox---IDE---releases/releases) | Installeurs et manifests par version |
| [`stable/latest.json`](stable/latest.json) | Manifest de mise à jour (F4/F5) |
| [NOTICE.md](NOTICE.md) | Licence et attributions |

## Téléchargement

1. Ouvrir [Releases](https://github.com/DroxKiwi/Drox---IDE---releases/releases) et prendre la dernière version **stable**.
2. Télécharger `Drox-IDE-Setup-*-win32-x64.exe` depuis les **assets de la release** (pas depuis le dépôt git — les binaires dépassent la limite GitHub).
3. Lancer l’installeur (user setup — pas besoin de droits admin).

## Prérequis

- **Windows 10+** (64 bits)
- **[WebView2 Runtime](https://developer.microsoft.com/microsoft-edge/webview2/)** — inclus sur Windows 11 ; sur Windows 10, installer si l’IDE ne démarre pas.
- **[Ollama](https://ollama.com/)** — optionnel, pour le chat IA local (non embarqué dans l’installeur).

## Profil utilisateur

Les paramètres et l’historique sont stockés sous :

`%APPDATA%\.drox-ide`

## Licence

Drox IDE est basé sur **Visual Studio Code - Open Source (Code OSS)**, Copyright (c) Microsoft Corporation, licence **MIT**.

Des portions supplémentaires (moteur Drox, intégration workbench, branding) sont Copyright (c) **KDDS**.

L’application installée contient :

- `LICENSE.txt` — licence MIT Code OSS
- `ThirdPartyNotices.txt` — licences des composants tiers

Voir [NOTICE.md](NOTICE.md) pour le résumé.

## Signaler un problème

[Ouvrir une issue](https://github.com/DroxKiwi/Drox---IDE---releases/issues/new) sur ce dépôt (distribution / install). Les bugs produit peuvent aussi être remontés via **Aide → Signaler un problème** dans l’IDE.

## Structure

```text
stable/
  latest.json          # versionné dans git
  1.3.0/
    SHA256SUMS
    RELEASE_NOTES.md
_upload/               # local seulement (.gitignore)
  Drox-IDE-Setup-*.exe # → gh release create
```

## Mainteneurs

Publication depuis le monorepo privé :

```powershell
.\scripts\build-release-win32.ps1 -SkipNpmInstall -SkipCompile -WithSetup
npm run release-publish-win32
```

Puis commit + `gh release create` (voir sortie du script).
