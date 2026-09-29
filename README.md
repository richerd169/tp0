<img src="images/header.jpg" />

## Sommaire <!-- omit in toc -->
- [🎯 Objectifs](#-objectifs)
- [A. Sur le téléphone](#a-sur-le-téléphone)
- [B. VSCod\[e/ium\]](#b-vscodeium)
- [C. Les SDK Android](#c-les-sdk-android)
- [D. srccpy](#d-srccpy)
- [E. Node \& Git](#e-node--git)
- [F. Configuration de votre compte Github](#f-configuration-de-votre-compte-github)
- [🚧 Troubleshooting](#-troubleshooting)
	- [Windows build tools](#windows-build-tools)
	- [Xiaomi](#xiaomi)

## 🎯 Objectifs
**Dans ce TP nous allons mettre en place les outils nécessaires au développement d'applications React Native. Le gros du travail ne concerne pas React Native en lui même mais plutôt la partie native du dev mobile : l'installation des SDK android.**

Soyons clairs, ce n'est sans doute pas le TP le plus exaltant de la formation, mais si vous le faites correctement cela vous simplifiera grandement la vie pour la suite ! 😄

<br/>

## A. Sur le téléphone
1. **Activez le mode développeur** sur votre smartphone en vous rendant dans
`Paramètres > À propos du téléphone`
et en appuyant frénétiquement sur "Numéro de build" jusqu'à ce qu'un message de confirmation apparaisse
1. **Activez le débuggage USB** dans `Paramètres > Options pour les développeurs`
	> 🚧 _Si vous êtes sur un téléphone **Xiaomi**, rendez-vous dans la section [Troubleshooting : Xiaomi](#xiaomi)_

3. **Installez l'application Expo Go** sur votre téléphone/tablette (_à trouver sur le [play store android](https://play.google.com/store/apps/details?id=host.exp.exponent)_). Elle vous sera utile pendant le cours pour tester des exemples de code qui vous seront fournis !

<br/>

## B. VSCod\[e/ium\]

<img src="images/vscode-ium.jpg" />

_**Pour développer, vous utilisez déjà sans doute un éditeur adapté au JS moderne. Si vous ne l'avez pas encore testé, je ne peux que vous recommander d'utiliser Visual Studio Code / VSCodium au moins pour la durée de cette formation.**_

[Visual Studio Code](https://code.visualstudio.com/) (vscode) est à l'heure actuelle l'un des éditeurs les plus **populaires** pour le développement web et en particulier dans l'écosystème React. C'est un éditeur opensource et développé avec [Electron](https://electronjs.org/), c'est donc un outil qui est **lui-même développé en JS !**

Malheureusement des questions de licence liées à Microsoft [plus ou moins obscures](https://vscodium.com/#why) viennent ternir un peu le tableau. Je vous conseille donc d'utiliser **la distribution "vraiment opensource" du logiciel qu'est [VSCodium](https://vscodium.com/)** (_aucune différence de fonctionnalité, hormis le [store d'extensions](https://github.com/VSCodium/vscodium/blob/master/DOCS.md#extensions-marketplace)_).

> <details><summary>ℹ️ <em>Vous avez déjà VSCode ?</em></summary>
>
> _Si vous avez déjà VSCode et que vous ne souhaitez pas faire la bascule vers VSCodium, pas de soucis pour la formation, comme les deux sont strictement identiques en terme de fonctionnalités (hormis le store d'extension qui diffère), les TP fonctionneront de la même manière avec vscode !_
> </details>


1. **Ouvrez le panneau des extensions de VSCod\[e/ium\]** à l'aide du raccourci <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>X</kbd>

2. **Installez l'extension `Prettier - Code formatter`** (_esbenp.prettier-vscode_)

	Prettier permet de formater automatiquement notre code en respectant de base un certain nombre de bonnes pratiques. Les possibilités de configuration sont volontairement limitées mais suffisantes pour avoir quand même l'impression d'avoir encore un peu la main sur son formatage 😄

	On configurera cette extension dans les prochains TP.

<br/>

## C. Les SDK Android

<img src="images/header-android-sdk.png" />

**Puisque les applications que nous développons avec React Native sont de vraies applications natives, il va nous falloir des outils de développement natifs.**


Comme dans cette formation nous nous concentrons sur le développement d'applis android, il nous faudra le SDK android et JAVA. Le plus simple pour installer le SDK est d'utiliser Android Studio, c'est donc ce que nous allons voir.

> <details><summary>ℹ️ Pourquoi Android et pas iOS ? On fait pas du cross-platform ??</summary>
>
> _Pour compiler des applications iOS il faut obligatoirement un mac, et ce quelque soit le framework qu'on utilise. Si vous avez un mac et que vous voulez faire les TPs sur votre iPhone (ou sur le simulateur intégré à XCode) pas de soucis, mais référez-vous aux instructions transmises par email_
>
> _Notez que certains outils de build en ligne peuvent permettre de contourner ce problème, comme par exemple [Expo Applications Services](https://expo.dev/eas)._
> </details>

> <details><summary>⚠️ Attention : ce TP est prévu pour Windows. Si on est pas sous Windows comment on fait ?</summary>
>
> _Ce TP est effectivement prévu pour des postes sous **Windows** (avec un téléphone **android** donc). Si vous êtes sous Linux ou Mac, il vous faudra adapter les instructions en vous appuyant à la fois sur cet énoncé et sur la documentation officielle ici : https://reactnative.dev/docs/set-up-your-environment (en prenant soin de sélectionner les OS que vous utilisez sur votre machine et sur votre tel)._
>
> _N'hésitez pas à m'appeler à l'aide ou à poster dans le salon #tp0 si vous rencontrez des problèmes !_
> </details>

1. **Installez Java JDK 17 (https://adoptium.net/temurin/releases/?version=17&os=windows pour le télécharger, ou bien si vous avez [chocolatey](https://chocolatey.org/) : `choco install -y microsoft-openjdk17`)**

	> ⚠️ _**Attention**_ ⚠️ : _choisissez bien la version correspondant à votre OS : x64 pour Windows 64bits (le plus probable), x86 sinon._

2. **Modifiez les variables d’environnement `JAVA_HOME` et `PATH`** (_remplacez les chemins pour correspondre au dossier de votre jdk_) :
    ```bash
    JAVA_HOME = C:\chemin\vers\jdku17xxxxx
    PATH +=
        C:\chemin\vers\jdku17xxxxx;
        C:\chemin\vers\jdku17xxxxx\bin;
    ```
3. **Téléchargez et installez [Android Studio](https://developer.android.com/studio/)**
    > ℹ️ _Pendant le processus d'installation, choisissez l'install "standard"._
4. On va maintenant installer les SDK nécessaires au développement android avec React Native (_chaque version de React Native nécessite une version de SDK bien particulière par défaut, il est possible d'en changer au prix de quelques modifications du code de nos applis mobiles, mais le plus simple à notre niveau c'est simplement d'installer les bonnes versions directement_). \
	Lancez Android Studio et **ouvrez le SDK Manager :**

	<img src="images/sdk-manager-button.png" width="700">

5.  Dans le SDK Manager (onglet *SDK Platform*), cochez la case **"Show Package details"** en bas à droite, dépliez le groupe **`Android 15.0 ("VanillaIceCream")`** et installez **Android SDK Platform 35**  :
	```
	SDK Platforms /
		Android 15.0 ("VanillaIceCream") /
			+ Android SDK Platform 35
	```
	<img src="images/sdk-manager-1.png" width="700"><br>

	Puis dans l'onglet ***SDK Tools***, cochez à nouveau la case **"Show Package Details"** en bas à droite, puis cochez si ce n'est pas déjà le cas la version **36.0.0** ainsi que la ligne **"Android SDK Command-line Tools (latest)"** :
	```
	SDK Tools /
		Android SDK Build-Tools /
			+ 36.0.0
		Android SDK Command-line Tools (latest) /
			+ Android SDK Command-line Tools (latest)
	```
	<img src="images/sdk-manager-2.png" width="700">
	<img src="images/sdk-manager-3.png" width="700">

6. **Notez le dossier dans lequel sont installés les SDK** en examinant le champ "Android SDK Location:" du SDK Manager

	<img src="images/sdk-manager-sdk-location.png" width="700">

7.  **Ajoutez les sous-dossiers `emulator` et `platform-tools` du sdk dans la variable d’environnement `PATH` puis créez une variable `ANDROID_HOME`** contenant le chemin vers la racine du dossier sdk :
    ```
    PATH +=
        C:\<chemin-vers-votre-dossier-sdk>\emulator
        C:\<chemin-vers-votre-dossier-sdk>\platform-tools

	ANDROID_HOME = C:\<chemin-vers-votre-dossier-sdk>
    ```
8. **Afin de vérifier que le SDK a bien été installé, branchez votre smartphone/tablette en USB, lancez la commande `adb devices`** dans un terminal et croisez les doigts ! Le résultat devrait ressembler à ceci :
    ```
    List of devices attached
    015d21098658181a        device
    ```

	> 🚧 _En cas d'échec, vérifiez que tous les préparatifs (cf. début du TP) ont bien été réalisés, débranchez/rebranchez le câble USB, et installez si besoin les drivers USB de votre téléphone (disponibles en principe sur le site du fabricant)._

<br/>

## D. srccpy

<img src="images/header-scrcpy.jpg">

_**Pendant les prochains TPs vous allez tester vos développements directement sur votre téléphone (grâce à tous les préparatifs que l'on fait maintenant !). C'est pratique mais ça a un inconvénient dans le cadre d'une formation à distance : votre formateur peut voir l'écran de votre ordi mais pas celui de votre téléphone !**_

Heureusement il existe des outils qui vont vous permettre de "recopier" en temps réel l'écran de votre téléphone sur l'écran de votre machine, ce qui me permettra de vous aider plus efficacement quand vous rencontrerez des bugs 😎


Je vous propose donc d'installer **[scrcpy](https://github.com/Genymobile/scrcpy)** qui est un outil opensource vraiment simple d'utilisation. Suivez la documentation officielle pour l'installer : https://github.com/Genymobile/scrcpy/blob/master/README.md

> <details><summary>⚠️ ⚠️ <em>Utilisez <strong>ABSOLUMENT</strong> le lien ci-dessus pour obtenir les instructions officielles pour télécharger et installer scrcpy ! …</em></summary>
> 
> _En effet, comme le dit le readme :_ \
> _"This GitHub repo (https://github.com/Genymobile/scrcpy) is the only official source for the project. Do not download releases from random websites, even if their name contains scrcpy."_
>
> _Effectivement... n'utilisez **PAS** https://scrcpy.org/ qui n'a rien d'officiel !!_ 😱
> </details>

Une fois scrcpy installé tentez d'afficher l'écran de votre téléphone sur votre ordi !

<br/>

## E. Node & Git

<img src="images/header-node.jpg">

**Lorsqu'on code une appli React Native, vous verrez (spoiler alert) qu'on utilise JavaScript. On va donc avoir besoin de Node.JS qui est LA plateforme de développement JavaScript.**


1. **Installez** NodeJS https://nodejs.org/en/download/ (_version LTS **24.x.x**_)

	> <details><summary>⚠️ <em><strong>ATTENTION (bis)</strong> : vous êtes sous <strong>Windows</strong> ? Vous devez OBLIGATOIREMENT ...</em></summary>
	>
	> _... télécharger l'installateur (partie "`Ou obtenez Node.js® préconstruit...`" en bas de page) puis pendant le processus d'installation de Node, **COCHER** la case "Automatically install the necessary tools. ..." sur l'écran **"Tools for native modules"**_
	>
	> <img src="images/node-install.png" >
	>
	> _Cette case permettra d'installer des dépendances utiles pour la suite (notamment python et les visual c++ build tools)._
	> </details>

	> <details><summary>⚠️ <em><strong>ATTENTION</strong> : vous avez <strong>déjà Node</strong> sur votre machine ?</em></summary>
	>
	> _Pour être certain·e de ne pas avoir de soucis pendant les TPs il vous faudra la dernière version stable._
	>
	> _Si vous aviez déjà une version plus ancienne de Node (tapez `node -v` dans un terminal pour en avoir le coeur net) alors vous devez la **DÉSINSTALLER COMPLÈTEMENT** avant d'installer la nouvelle version._
	> </details>


	> <details><summary>ℹ️ Votre connexion internet se trouve derrière un proxy ?</summary>
	>
	> _Alors, pour que node fonctionne correctement, tapez les commandes suivantes (en remplaçant les login/pass/adresse/port dans l'url) :_
	>
	> ```bash
    > npm config set proxy "http://username:password@servername:port/"
    > npm config set https-proxy "http://username:password@servername:port/"
    > ```
	> </details>

2. **Installez** aussi Git http://git-scm.com/ et sélectionnez les choix suivants pendant le processus d'installation :

    + "Git from the command line and also from 3rd-party software"
    + "Checkout as-is, commit as-is"

<br/>

##  F. Configuration de votre compte Github

<img src="images/header-github.png" />

_**Pour la suite de la formation vous aurez besoin de récupérer du code depuis le repo de chaque TP.**_

Le plus simple c'est de "cloner" avec git le repo de chaque TP au fur et à mesure, mais pour ça il faut que vous ayez au préalable configuré votre compte github :

- **si vous voulez cloner en SSH** : il faut que vous renseigniez une clé SSH dans votre [compte utilisateur github > Settings > SSH & GPG Keys](https://github.com/settings/keys) (_pour plus de précisions sur la configuration de clés SSH avec github je vous recommande la [doc officielle](https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories#cloning-with-ssh-urls)_).

- **si vous préférez cloner en https**, vous devrez vous créer un "Personal access token" [dans votre compte github > Settings > Developer Settings > Personal access tokens](https://github.com/settings/tokens) et cocher tous les droits `"repo"`. Vous pourrez ensuite cloner à partir de l'URL du repo en tapant votre token à la place du mot de passe (_plus d'infos sur comment générer et utiliser les Personal access tokens dans [la documentation officielle](https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls)_).

Une fois la configuration de votre compte terminée, vous pouvez tester de cloner ce TP pour vérifier que tout fonctionne correctement. Ouvrez un terminal, placez vous dans le dossier de votre choix avec la commande `cd chemin/du/dossier/choisi/`, puis :
- si vous êtes en SSH tapez la commande :
	```
	git clone git@github.com:formation-react-native/tp0.git
	```
- si vous avez choisi de cloner en https avec un personal access token, tapez la commande :
	```
	git clone https://github.com/formation-react-native/tp0.git
	```

Si tout se passe bien vous devriez avoir maintenant un sous-dossier `tp0` contenant ce fichier `README.md`, et un dossier `images` avec les images que vous avez vues plus haut !


<br>
<br>

**Voilà, en principe votre poste est maintenant prêt pour la formation ! Félicitation !!** 🎉 RDV dans quelques jours pour la mise en pratique !
<br>
<br>
<br>
<br>


## 🚧 Troubleshooting
### Windows build tools

**Sur certaines configuration, il peut être utile d'installer Python et les Visual C++ Build Tools (normalement déjà installés via l'installer de node)** :

si vous avez installé chocolatey, vous pouvez installer les 2 paquets suivants :
- https://chocolatey.org/packages/python
- https://chocolatey.org/packages/visualstudio2019-workload-vctools

```bash
choco install python visualstudio2019-workload-vctools
```

> 📖 _[Source](https://github.com/nodejs/node/blob/1ba508d51b3057768fa068dc3e279450d498c3d9/tools/msvs/install_tools/install_tools.bat#L41-L42)_

Dans le cas contraire, installez [chocolatey](https://chocolatey.org/install) puis les 2 paquets mentionnés ci-dessus.

Si vous ne souhaitez/pouvez vraiment pas utiliser chocolatey, alors vous pouvez tenter d'installer le paquet npm `windows-build-tools`. Ouvrez un terminal **en tant qu'*ADMINISTRATEUR*** et tapez la commande suivante :
```bash
npm install --global --production --verbose windows-build-tools
```

> _**NB :** En cas de blocage de l'installation sur la ligne **"Successfully installed Python 2.7"** pendant plus de 5 ~ 10 minutes, tentez donc la manipulation décrite sur cette issue github : https://github.com/felixrieseberg/windows-build-tools/issues/172#issuecomment-484091133_

### Xiaomi
Si vous vous trouvez sur un téléphone Xiaomi, il est probable que vous ayez à cocher les options suivantes dans la page "`Developer options`" :
- USB Debugging
- Install via USB
- USB Debugging (Security settings)
