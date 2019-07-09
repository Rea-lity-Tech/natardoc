# Processing \[FR\]

Une fois l'appareil monté, vous pouvez lancer les exemples, calibrer votre système et créer vos propres applications.

### Lancement des exemples

Les exemples sont des sketchs [Processing](http://processing.org). Les exemples de code sont situés dans votre dossier sketchbook accessible dans Processing depuis `Fichier -> Exemples` puis dans la pop-up dans le sous-dossier `PapArt/first-exemples`.

Les premiers exemples 

* **Camera**:  Réalité augmentée par-dessus le flux vidéo en vue à travers ou "See Through" en anglais. Ces exemples proposent les premiers concepts: suivi d'éléments trackés, rendu en "2D" \(on paper\) et "3D" \(around paper\) avec des PaperScreens, [documenté ici](http://forum.rea.lity.tech/t/paperscreen-model-in-papart/39). Les interactions se font à la souris ou avec le suivi de couleurs.
* **DepthCamera**: Même que précédemment mais avec un flux de profondeur en plus. Les exemples permettent de visualiser le flux de profondeur coloré \(`DepthVisualization`\), de créer des écrans tactiles \(`TouchScreen`\) avec des boutons \(`TouchWithGUI`\).  L'accès aux données de profondeur est illustré dans `TouchPointCloud`. 

**Pour les exemples suivants, la calibration est nécessaire.**

* **Projection 2D**: Projection sur une une table/mur sans exploiter la calibration 3D. Très pratique pour tester la qualité de calibration ou faire des applications tactiles simples. 
* **Projection**: Projection 3D calibrée. Ces exemples montrent l'utilisation de `PaperScreen`  et `TableScreen` en mode projection. Ils sont similaire à `DepthCamera` et `Camera` mais utilisent la projection en mode de rendu.  

### Calibration

La calibration est accessible via `calibration` -&gt; `mainCalib`.  
Cette application dédiée est minimale et la calibration se lance avec la touche `c`. Elle fonctionne avec projection pour calibrer:

* La position de la caméra. 
* La position de la table. 
* La position du projecteur \(si le booléen `useProjection` est activé\).
* Les couleurs à détecter pour le suivi de couleurs. 

La calibration s'effectue avec la feuille plastifiée fournie avec l'appareil

![](../.gitbook/assets/image%20%2810%29.png)

Au verso:

![](../.gitbook/assets/image%20%281%29.png)

Ces images sont disponibles dans le dossier  `/usr/share/processing/modes/java/libraries/PapARt/data/markers/`.

Les discussions et conseils pour obtenir une bonne calibration sont sur [FAQ Calibration](http://forum.rea.lity.tech/t/faq-sur-la-calibration-french-prototype-fab-lab/62). Posez des questions, nous aurons des solutions !

### Création d'applications

#### 1. Développement local \(sur le PC intégré\).

En développement local, vous devez ajouter un second écran. Le code en mode «star wars» est très déconseillé. Vous pouvez alors coder avec l'IDE Processing, ou avec tout autre environnement de développement \(Eclipse, Netbeans, Emacs etc...\).

Nous proposons un [exemple de compilation](https://github.com/Rea-lity-Tech/papart-app-example) avec Maven.

#### 2. Développement à distance \(depuis une autre machine\).

Le développement à distance est une nouvelle fonctionnalité de Natar en test. Cela permet une meilleure compatibilité pour les développeurs.

