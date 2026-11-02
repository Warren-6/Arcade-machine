# Arcade-machine
This will show the documentation about the method we choice to repair and maintain the actual arcade

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
> Cependant utilisant un nouveau systeme d'exploitation [**Recalbox**](), le fichier de configuration des entrees de touches   
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
> Dans notre cas on va rester sur un Raspberry pi 3b+ pour defaut de PC...[_clique pour plus d'information sur le modele_]()

### *Encodeur ps/2
---

<img src = "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTyEmd2xJILo-Rliofd78ghb21MyQwPvGtsYuElzgVIvq4tAnHnOt9rwCIg&s=10" align ="left" width ="200">

Il s'agit du module permettant de gerer l'interaction boutons-systeme. 

[1]: Comportement d'un processeur qui bloque lors de l'execution de processus


