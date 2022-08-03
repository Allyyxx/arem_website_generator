+++
title = "Pompes et ventouses"
date = "2022-08-03"
[ author ]
  name = "Titouan Real"
+++

## Présentation
{{< image_right src="/images/activities/CDR/2021/robots/kraken/pompes_et_ventouses/ventouses.webp" width="400px" >}}

Les actionneurs de Kraken ont pour but de récupérer les gobelets situés dans des écueils. Les gobelets sont collés aux ventouses par aspiration d’air avec des pompes, et ils sont soulevés grâce à un servomoteur. Les 5 pompes pour chaque ventouse s’allument ensemble, mais les électrovannes reliées individuellement à chaque ventouse peuvent s’utiliser individuellement et permettre de relâcher les gobelets. Ces actionneurs sont pilotés par l’intermédiaire d’une carte Arduino nano en liaison série avec le microcontrôleur principal.

***

## Description
{{< image_left src="/images/activities/CDR/2021/robots/kraken/pompes_et_ventouses/schema_electrique.webp" width="200px" >}}

Chaque pompe est hermétiquement reliée à une ventouse et une électrovanne. Les électrovannes ouvrent le circuit d’air quand elles sont alimentées, ce qui stoppe la succion des ventouses. La carte Arduino nano pilote les actionneurs sur ordre (liaison série) du microcontrôleur principal. Le fait de passer par la carte Arduino nano et de ne pas piloter les actionneurs directement depuis le microcontrôleur principal permet :
* de ne pas surcharger de fils le microcontrôleur principal
* d’avoir suffisamment de pin libre sur le microcontrôleur principal
L’ensemble des pompes sont reliées en parallèle et un unique transistor permet de les alimenter. Ce transistor est piloté par la carte Arduino nano. Il y a un transistor par électrovanne permettant de les alimenter ou de les éteindre de manière individuelle. Ces transistors sont pilotés par la carte Arduino nano.

L’alimentation de l’ensemble de la carte actionneurs (ou vient s’interfacer les alimentations des pompes, des électrovannes, et du servomoteur) est stabilisée par un condensateur de haute capacité ( en parallèle ).

En effet, des pics de courant important ont été détectés lors de l’utilisation de la carte (commutation des électrovannes notamment) qui nuisaient fortement au fonctionnement des actionneurs ( mise hors tension de la carte arduino, électrovannes et pompes mal alimentés). L’ajout d’un condensateur permet de régler ces problèmes. Les ventouses ont été choisies après un test de plusieurs échantillons envoyés par la société SAPELEM (ventouses qui nous ont été finalement offertes, merci). Elles permettaient une meilleure saisie des gobelets, par contact de la ventouse sur le gobelet, sans élan. Les tuyaux ont été choisis pour leur souplesse.

Les différents morceaux de tuyaux pour un même couple électrovanne/pompe/ventouse sont reliés par un « T ». Des morceaux de Tuyaux plus rigides assurent le lien entre les tuyaux souples et le T. La carte actionneur a été conçu sur KiCad et commandé sur JLPPCB Des Profilés en aluminium et pièce imprimés en 3D ont été utilisés pour fixer les actionneurs. Les alimentations des pompes et électrovannes sont interfacés sur la carte actionneur avec des câbles sertis. Ils se sont montrés indispensables pour limiter les faux contacts. Il faut aussi préférer l’utilisation de câbles pré-sertis au sertissage manuel.

***

## Code

    #include "HardwareSerial.h"
    HardwareSerial *ser_act;

    ser_act = new HardwareSerial(PD_2 PC_12);
    ser_act -> begin(9600);

### Envoi des données :

    ser_act -> print("3");

Il faut établir une table de correspondance caractère envoyé/opérations à effectuer

### Réception côté Arduino nano:

    Serial.begin(9600);
    void loop()
    {
        if(Serial.available())
        {
            char c = Serial.read();
            /*Réaliser Action selon le caractère reçu */
        }
    }
