# PÉNC MI — obtenir l'APK Android

Ce dossier est un projet complet et fonctionnel (application web + coquille
Android via Capacitor). Il ne manque qu'une seule étape que je ne peux pas
faire moi-même : la **compilation**, qui nécessite les outils Android de
Google (Gradle, SDK) — mon environnement n'y a pas accès.

Deux façons d'obtenir le fichier `.apk` à partir d'ici, sans rien réécrire.

---

## Méthode recommandée — compilation automatique dans le cloud (gratuite, pas d'installation)

1. Créez un compte GitHub si vous n'en avez pas (gratuit) : https://github.com/signup
2. Créez un nouveau dépôt (bouton "New repository"), par exemple nommé `pencmi-app`.
3. Poussez ce dossier dedans. Le plus simple, directement dans le navigateur :
   - sur la page du nouveau dépôt, cliquez sur "uploading an existing file"
   - glissez-déposez tout le contenu de ce dossier (sauf `node_modules` s'il existe)
   - validez ("Commit changes")
4. Allez dans l'onglet **Actions** du dépôt. Un workflow nommé
   "Build APK Android — PÉNC MI" se lance automatiquement (ou cliquez sur
   "Run workflow" s'il ne démarre pas seul).
5. Attendez la fin (5 à 10 minutes). Une fois terminé, ouvrez le run et
   téléchargez le fichier joint **pencmi-app-debug-apk** en bas de page — c'est
   votre `.apk`.
6. Transférez-le sur un téléphone Android (par mail, clé USB, Drive...) et
   installez-le en autorisant "Sources inconnues" si demandé.

C'est un APK de **debug**, parfaitement installable et fonctionnel pour un
usage club — la version "release" (signée, optimisée) est une étape
supplémentaire, utile seulement si vous visez le Play Store plus tard.

---

## Méthode alternative — sur un ordinateur avec Android Studio

1. Installez Android Studio (gratuit) : https://developer.android.com/studio
2. Ouvrez ce dossier, puis dans un terminal :
   ```
   npm install
   npm run build
   npx cap sync android
   ```
3. Ouvrez le sous-dossier `android/` directement dans Android Studio.
4. Menu **Build → Build Bundle(s) / APK(s) → Build APK(s)**.
5. L'APK se trouve dans `android/app/build/outputs/apk/debug/`.

---

## Ce qui a déjà été fait pour vous

- L'application a été convertie en projet web autonome (Vite + React), qui se
  compile sans erreur — vérifié ici.
- Le stockage propre à l'environnement Claude a été remplacé par un stockage
  local standard (fonctionne hors-ligne, sur l'appareil).
- Le projet Android (Capacitor) est déjà généré dans le dossier `android/`.
- Le workflow d'automatisation cloud est prêt à l'emploi, aucune configuration
  supplémentaire nécessaire.

## À personnaliser si vous le souhaitez plus tard

- **Icône de l'app** : actuellement l'icône par défaut de Capacitor. Pour
  mettre le logo du club, voir https://capacitorjs.com/docs/guides/splash-screens-and-icons
- **Nom du paquet** : `sn.xataari.pencmi` (dans `capacitor.config.json`) —
  à changer si vous visez un jour le Play Store sous un autre identifiant.
