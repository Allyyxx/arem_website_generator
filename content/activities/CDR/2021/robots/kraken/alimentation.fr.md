+++
title = "Alimentation"
date = "2022-08-03"
[ author ]
  name = "Titouan Real"
+++

{{< image_right src="/images/activities/CDR/2021/robots/kraken/alimentation/buck.webp" width="200">}}

La carte d’alimentation est l’interface entre la batterie et le reste du robot.
Elle s’occupe de transformer la tension non constante de la batterie en une série de tensions nécessaires au bon fonctionnement de tous les circuits et actionneurs du robot.
{{< blank_line>}}
{{< blank_line>}}
{{< blank_line>}}
***

{{< image_left src="/images/activities/CDR/2021/robots/kraken/alimentation/carte.webp" width="250">}}


Pour cela, elle utilise deux méthodes de régulation différentes.

La première consiste en l’utilisation de convertisseurs Buck, permettant d’abaisser une tension continue. La carte en possède quatre afin de pouvoir fournir toutes les tensions demandées, et de répartir la charge.
La deuxième, utilisée uniquement pour les moteurs, se base sur un régulateur LM338T, qui peut fournir jusqu’à 5 ampères.

{{< image_left src="/images/activities/CDR/2021/robots/kraken/alimentation/schema.webp" width="250">}}

Pour la connecter aux différentes parties du robot, nous avions prévu un système de nappes, permettant de garder propre l’intérieur du robot, et éviter d’avoir des câbles partout. Cependant, comme toutes les cartes n’ont pas été réalisées en même temps, les connections se sont faites petit à petit, et la nappe n’a jamais servie.
C’est sur cette carte que viennent s’interfacer les boutons d’arrêt global et d’arrêt d’urgence, qui peuvent déconnecter certains régulateurs et ainsi couper l’alimentation du robot.
Elle dispose aussi d’une rangée de LEDs de différentes couleurs, afin de détecter rapidement les pannes, et de vérifier ce qui est sous tension.

Une particularité de cette carte est la largeur des pistes. En effet, comme elles doivent supporter des courants de plusieurs ampères, elles sont plus larges que la moyenne.

***

{{< image_right src="/images/activities/CDR/2021/robots/kraken/alimentation/EasyEDA.webp" width="200">}}

Pour leurs conceptions, nous avons utilisés EasyEDA, un logiciel assez simple permettant de concevoir des cartes, et disposant d’une librairie très complète de composants. De plus, ce logiciel est édité par l’un des plus grands fabricants de PCB, ce qui nous garantit que la production se passera sans soucis si nous passons par eux.

Nous avons dans un premier temps voulu réaliser ces cartes grâce aux machines de l’école afin de gagner du temps. Cependant, la machine est entrée en période de maintenance, ce qui nous a obligés à les commander chez JLCPCB, nous faisant gagner des puzzles en cadeau, ce qui fût quand même plutôt cool.