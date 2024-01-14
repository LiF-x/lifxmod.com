---
_schema: default
layout: default
title: LiFx Knool Pack FR
nav_order: 7
nav_exclude: true
parent: Official mods
has_children: false
has_toc: true
last_modified_date:
---
# KnoolPack

[In english](/mods/lifx-knools-weapons)

&nbsp;Tuto pour les knools et armes de knools&nbsp;

Pré requis pour suivre le tuto:

1. Votre serveur doit utilisé [LiFx Server Framework](/Docs/server-framework)
2. Votre serveur doit etre connecté à [YoLauncher.app](https://YoLauncher.app)

[Téléchargement ici](https://github.com/LiF-x/Knool-Pack/releases/latest)

### Installation/instructions&nbsp;

1. Téléchargez le dernier packages à partir du lien ci-dessus

2. Extraire le contenu du zip dans un dossier local (le tutoriel suppose que vous travaillez à partir du répertoire de base extrait pour toutes les instructions locales).

3. Supprimez les anciennes versions du mod de votre serveur

4. Mettre le contenu du dossier "mods" sur le serveur

5. Mettre le contenu du dossier "yolauncher" sur le serveur

6. Modifiez **Votre** skill\_types.xml du serveur,

   1. &nbsp;Ajoutez "2399 2359 2360 2361 2362" à la liste des identifiants dans&nbsp;

      &lt;ent\_req type="object\_type\_id"&gt;1070 1083 924 925 926 927 928 929 930 931 932 933 934 935 936 1090 1460 &lt;/ent\_req&gt;

      of Loot! ability. (Normalement sur la ligne# 6073)

   2. Ajoutez "2465" dans&nbsp;

      &lt;ent\_req type="object\_type\_id"&gt;47 48 49 1466&lt;/ent\_req&gt;

      &nbsp;of Shape Stones Ability (Normalement sur la ligne# 1902)

7. Copiez toutes les données du fichier Knool\_cm\_equipTypes.xml et collez au bas de **votre** cm\_equipTypes.xml dans le dossier data du serveur&nbsp; Veuillez noter : Assurez-vous de coller en haut de cette balise &lt;/equipment\_types&gt; car le fichier Knool\_cm\_equipTypes.xml l'inclut.

8. &nbsp;Copiez toutes les données de knool\_cm\_objects et le coller au bas de votre cm\_objects.xml<br>\- Veillez à ne pas écraser la dernière ligne "&lt;/object\_types&gt;" Ceci est nécessaire pour compléter le fichier xml.

9. Mettre le dossier "data\\ai" (y compris le contenu) dans le dossier data de votre serveur.

10. Utilisez LiFx Server framework v3.0.0 ou plus récent avec $LiFx::createDataXMLS réglez sur "true" AutoloadConfig.cs pour créer objects\_types.xml, recipe.xml and recipe\_requirement.xml sur le serveur et démarrer le serveur. (Toutefois, ce module ne nécessite que l'utilisation de l'option object\_types.xml)

11. Arrêter le serveur et copier les fichiers sur le serveur à partir de /LiFx/dbexport vers votre dossier serveur/data

12. Récupérez &nbsp;recipe.xml and recipe\_requirement.xml à partir des fichiers xml généré dans (LiFx Folder) extraire ensuite dans le dossier "yolauncher/modpack/data".

13. Récupérez cm\_objects.xml and skill\_types du dossier data du serveur et le mettre dans le dossier "yolauncher/modpack/data".

14. Assurez vous d'avoir 7zip d'installé sur votre ordinateur [téléchargement ici](https://7zip.dev/en/download/)

15. Assurez-vous que tout ce dont vous avez besoin se trouve dans le pack et insérez les fichiers dans le dossier de YOLauncher dont vous avez besoin pour votre serveur, en vous assurant de ne pas écraser les fichiers du mod sans vérifier que vous possédez déjà une version plus à jour avec les informations correctes.

### Assurez-vous que les fichiers mentionnés ci-dessous se trouvent sur votre serveur.&nbsp;

<br>\- cm\_spawn\_patterns.xml ( Veiller à ce que tous les "knools" soient dedans )<br>\- skill\_types.xml (doit être construit comme indiqué étape 6).<br>\- cm\_equipTypes.xml (doit être construit comme indiqué étape 7).<br>\- cm\_objects.xml &nbsp;(doit être construit comme indiqué étape 8).<br>\- object\_types.xml (Construit pour vous comme mentionné sur le serveur et peut être trouvé dans le dossier LiFx/dbexport ).<br>\- recipe.xml (Construit pour vous comme mentionné sur le serveur et peut être trouvé dans le dossier LiFx/dbexport ).<br>\- recipe\_requirement.xml (Construit pour vous comme mentionné sur le serveur et peut être trouvé dans le dossier LiFx/dbexport ).​​​

### Assurez-vous que les fichiers se trouvent dans le dossier data préparé pour yo launcher..&nbsp;

<br>\- skill\_types.xml (needs to be built as mentioned above).<br>\- cm\_equipTypes.xml (needs to be built as mentioned above).<br>\- cm\_objects.xml &nbsp;(needs to be built as mentioned above).<br>\- object\_types.xml (Built for you as mentioned on the server and can be found in the db export folder ).<br>\- recipe.xml (Built for you as mentioned on the server and can be found in the db export folder ).<br>\- recipe\_requirement.xml (Built for you as mentioned on the server and can be found in the db export folder ).​​​

1. Lancez "createModpack.bat" inclus dans ce pack pour générer un .zip de modpack à envoyer sur votre serveur sur&nbsp;[Yo Launcher](https://www.yolauncher.app/)&nbsp;

2. Envoyez vers Yo Launcher le site sans oublier de ce connecter&nbsp;

3. Définir le modpack comme actif

4. (Re)Lancez YoLauncher pour télécharger le modpack pour votre client et rejoignez votre serveur.