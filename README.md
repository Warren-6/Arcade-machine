# Arcade-machine
<img src ="Image/arcade-machine.jpeg" align ="left" size = "50%"/>

Ceci a pour but de mettre en evidence la documentation des methodes choisies pour reparer l'actuelle   
Borne d'arcade <br style ='left'>

### Description Electronique
---
Un diagnostique de la machine a ete effectuer  afin de rescencer les composants qu'elle contient pour mieux les proteges   
et eventuellement les changer le cas deffaillant. Le tableu suivant les presentent.


<div align = "center">
  
|    Composants     | Reference technique|
|        :---       |       :----        |
| Ecran             | Panasonic Plasma   |
| Unite             | Raspberry pi 3b+   |
| Carte mere        | Module TNPA4031    |
| Carte de jeu      | Encodeur cla-ps/2  |
| Micro switch      | Series D4*         |
| Carte de puissance| Panasonic sustain  |

</div>

> [!WARNING]
> Cependant utilisant un nouveau systeme d'exploitation [**Recalbox**](https://wiki.recalbox.com/fr/home), le fichier de configuration des entrees de touches   
> etant majoritairement different, rendant le pilotage non-intuitif. _Il tournait anciennement sur Arch-linux_
>
> Aussi, le cablage de l'electronique de la machine ne releve pas vraiment d'un "Chef d'oeuvre", autant dire qu'il   
> faudrait refaire toute la connectique pour la rendre plus lisible
>
> En fin, l'insecurisation du montage ne garantipas reelement une surete tant pour le maintenancier que pour le materiel

### *Choix de l'unite de commande
---
Theoriquement pour une machine comme l'arcade, une bonne vieille raspberry ferrait l'affaire (caracteristique a prendre en   
compte selon les jeux que l'on souhaite faire tourner). Mais en pratique on n'est jamais a l'abrit d'un freze [^1], d'une   
surchauffe,... C'est pour cela qu'un PC bien munis (ventirad, ventilateur, regulateur de tension,...) peu s'avere utile   
dans ce genre d'entreprise.

> [!NOTE]
> Dans notre cas on va rester sur un Raspberry pi 3b+ pour defaut de PC...[_cliquer ici pour plus d'information sur le modele_](https://www.raspberrypi.com/documentation/computers/getting-started.html#hardware-prerequisites)

### *Encodeur ps/2
---

<img src = "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTyEmd2xJILo-Rliofd78ghb21MyQwPvGtsYuElzgVIvq4tAnHnOt9rwCIg&s=10" align ="left" width ="200"/>

Il s'agit du module permettant de gerer l'interaction boutons-systeme. Comme le montre l'image ci-contre, il est monte en
parralele avec 2 colonnes pour 1 ligne (pouvant etre considerer ici comme une matrice pour faciler l'image mentale). A cet
effet, vous pouvez consulter [la representation matricielle](https://www.smallcab.net/telechargement/manuel/keyboard_PS2_to_panel_fr.pdf) (_pour un clavier 105 touches azerty_) 
suivante pour une meilleur   represenation. <br clear = 'left'>

 
### *Microswitch
---
Ce sont des interrupteurs rattaches aux boutons et laissant passer le courant lorsqu'il sont presses. Celui ci est ensuite percu    
par l'encodeur qui attribut une lettre du clavier a ce signal. [_consulter la documentation du microswitch_](https://www.alldatasheet.com/datasheet-pdf/view/809054/CHERRY/D413-R1AA-G2.html)

> [!TIP]
> Ces interrupteurs possedent une borne commune (COM) et une borne ouverte (NO). Le jeu est de connecter ces interrupeteurs
> en serie sur une meme ligne (R) et independante entre colonne (C).

<ins>**Exemple**</ins> : pour 3 interrupteurs, relier a 3 colonnes differentes C1, C2, C3 et une meme lignes R, on obtient    
les combinaisons suivantes R-C1, R-C2, R-C3 chacune correspondant a une touche de clavier

![view-more](Image/montage-diagram.png)

### *Logiciel et Pi 3b+
---
La Raspberry pi 3b+ choisi, offre des performances largement suffisante pour faire tourner les jeux sur le logiciel.    
 [_plus d'infos sur le module_](https://wiki.recalbox.com/fr/hardware-compatibility/raspberry-pi). Qu'en est-il du logiciel?

Le systeme de retrogaming[^2] Recalbox contient un panel de configurations contenus dans le repertoire
`/recalbox/share/system/recalbox.conf`, appeler fichiers d'`emulationstation`.   
Cependant necessite une certaine [compatibilite](https://wiki.recalbox.com/fr/hardware-compatibility) avec le materiel pour fonctionner correctement.


Pour le mapping des touches, le logiciel n'est compatible qu'avec une certaine [gamme d'encodeur](https://wiki.recalbox.com/fr/hardware-compatibility/compatible-devices/input), ainsi pour   
en ajouter d'autres on pourra configurer le logiciel. [_comment ajouter un encodeur USB?_](https://wiki.recalbox.com/fr/tutorials/controllers/usb-encoders/recalbox-for-your-usb-keyboard-encoder)

### *Configuration des touches
---


[^1]: Comportement d'un processeur qui bloque lors de l'execution de processus
[^2]: Logiciel permettant de jouer plusieurs jeux de platformes differente sur une seule
