# Recherche d’informations autour du protocole TR-069
## Termes importants
**TR-069 :**  Le Technical Report (ou CWMP pour « CPE WAN Management Protocol »), est un protocole défini pour gérer la communication entre un équipement terminal du réseau local du client et un serveur d’autoconfiguration (ACS) associé dans un même réseau appartenant à l'opérateur.

**ACS :**  AutoConfiguration Server, il va fournir les configurations de différents équipements automatiquement et facilement.

**CPE :**  Customer-premises equipment (CPE) est un équipement qui se trouve dans le site d'un client.

**RPC :**  Un RPC est initié par le client qui envoie un message de requête à un serveur distant connu pour exécuter une procédure spécifique avec des paramètres spécifiques. Le serveur distant envoie une réponse au client puis l'application continue son déroulement.

**SOAP :** Ancien acronyme de Simple Object Access Protocol, c'est un protocole d'échange d'information structurée dans l'implémentation de services web bâti sur XML.

## TR-069
Le protocole TR-069 (Technical Report ou CWMP pour « CPE WAN Management Protocol »), est un protocole défini pour gérer la communication entre un équipement terminal du réseau local du client et un serveur d’autoconfiguration associé dans un même réseau appartenant à l'opérateur. Il offre à l’utilisateur un ensemble de services d’administration, de contrôle et de diagnostic tout en évitant les problèmes liés aux diversités matérielles et logicielles. Les spécifications sont régulièrement publiées sur le site officiel du BroadBand Forum.

Le protocole de gestion des CPE permet à un ACS (Auto Configuration Server) de surveiller une ou plusieurs entités et offre un mécanisme d’ajout de fonctionnalités propres au vendeur du CPE.

Le système de supervision permet le suivi du CPE dès sa connexion au réseau de diffusion de service (Broad Band Access Network), tout en offrant à l’ACS la possibilité de sa supervision d’une manière asynchrone.

L’extensibilité du protocole permet la supervision des paramètres ajoutés d’une version à une autre, et offre la possibilité de personnalisation au constructeur par ajout de fonctionnalités propres.

Le protocole CWMP (ou TR-069) manipule donc des paramètres qui sont modélisés dans un modèle de données (similaire à une MIB). Les principaux modèles de données sont :
-   TR-098 : Modèle de données de l'IGD (Internet Gateway Device)
-   TR-104 : Modèle de données de la VoIP
-   TR-140 : Modèle de données du NAS (disque réseau)
-   TR-135 : Modèle de données de la STB
-   TR-106 : Template
-   TR-157 : Objet commun réutilisable

## CPE
Customer-premises equipment (CPE) est un équipement qui se trouve dans le site d'un client (d'une entreprise) et qui est raccordé à l'infrastructure d'un opérateur, dans un Point Of Presence (POP), via une boucle locale.

Un CPE joue donc un rôle de client vis-à-vis de l'infrastructure de l'opérateur, un rôle d'ETTD (ou DTE pour Data Terminal Equipment) dans le modèle de l'UIT-T, l'équipement du POP auquel il est raccordé jouant un rôle d'ETCD (ou DCE pour Data circuit-terminating equipment).

## SOAP (Simple Object Access Protocol)
SOAP est un protocole d'échange d'information structurée dans l'implémentation de services web bâti sur XML.

Il permet la transmission de messages entre objets distants, ce qui veut dire qu'il autorise un objet à invoquer des méthodes d'objets physiquement situés sur un autre serveur. Le transfert se fait le plus souvent à l'aide du protocole HTTP, mais peut également se faire par un autre protocole, comme SMTP.

Le protocole SOAP est composé de deux parties :
1.  une enveloppe, contenant des informations sur le message lui-même afin de permettre son acheminement et son traitement ;
2. un modèle de données, définissant le format du message, c'est-à-dire les informations à transmettre.

## ACS (Automatic Configuration Server)
Un ACS est un serveur qui a pour but de configurer automatiquement et facilement des CPE grâce au protocole décrit dans le standard TR-069. Il permet également de modifier la configuration des appareils à distance. Il est très utile pour centraliser la gestion d'équipements.

Ce standard TR-069 définit les règles de sécurité et le protocole de communication entre le CPE et l'ACS, et inversement. 

### Quelques illustrations pour mieux comprendre
![](https://lh3.googleusercontent.com/E948eoqXBcCt4n87fXgExsFCYSDWIyOSkkXXRIA3FNkA3PxnMii_H0QL4bOxzDxBb7UIis3VwxW418WoH_1yr5pwOzaScmbyzKjTHbRgYfdgnzya1dUBa8QlKRgeRSiWJxMk5au5)
![](https://lh5.googleusercontent.com/EVdZ7ORZp66EFIeyNBThMTWAaV_qvuLHH64HzNdr0RaSCbzM7hRnZDT33hGCiV4fFpBFqG2-HYiddUeGpiKp9HYNXMbW7Ii4AgYrcsWJu8vY7uW8fR_sEgJ_9KwWGH8JEXfZscCH)
![](https://lh6.googleusercontent.com/8T_RkKTO4tUwii05V5eD8z5L62nNrKVSd4m8BC7abQEQId4S7awp1BrwlH_-F2psfjzEy5OZSzrZHfBqJFsRXog9k3TM-rEdRSECHhee_3HSqqI-OOoawmvT5mq9laqLOnpQp3Qs)
![](https://lh4.googleusercontent.com/nzyKeFK4jcILBVZ4OvrclWXF_u39U5dkpeEeEVgVdJcM0gLLBREw3a3LyGEvDU8Z8ws6o1AGIJhsVEAVDMiTn6m-g7epoz3u-MfKPSpkVe0l99sVNHHKfeheoUL_xu_Tbf-uudI6)![](https://lh4.googleusercontent.com/UbqCqxlWu_bLbrNpTqxO0dJEm5ERENi0o9cjzmB5tUx60hwu-nJKFQ2-oa-yVElbimYabZQjgTj9igDP6ugQmDbeX_gs4ymAyIVriaKQCdsci1KGSxR3-KwvEo2zuxHV7n9FDf9c)

## Différentes étapes d’un échange avec le protocole TR-069
1 - Initialisation de la session
> L’appareil se connecte à l’ACS
2 - Authentification
> L’ACS vérifie le nom d’utilisateur et le mot de passe envoyé par le CPE.
3 - Identification de l’appareil
> Identifie le dispositif à partir des informations transmises par le CPE lors de l’initialisation de la session.
4 - Exécution de tâches sur le dispositif
> Après l’identification et l’envoie de toutes les informations utiles, l’ACS ordonne certaines tâches et actions à effectuer sur le CPE. Par exemple cela peut être la lecture et/ou la sauvegarde de paramètres, la réalisation de diagnostics, le redémarrage du CPE ou bien un transfert de fichier.
5 - Clôture de la session
> Quand toutes les tâches/actions ont été planifiées, le CPE ferme la session. Pour effectuer d’autres tâches une nouvelle initialisation est obligatoire.

## Procédures de communication détaillées

### Côté CPE :
1.  Connexion SSL/TLS avec l’ACS (initiée par le CPE)
2.  Envoi d’une requête RPC vers l’ACS
3.  Envoi d’une requête POST pour indiquer la fin de l’envoi de requêtes RPC vers l’ACS
4.  Envoi d’un paramètre et sa valeur vers l’ACS
5.  Interrompre la connexion SSL/TLS avec l’ACS

### Côté ACS :
1.  Connexion SSL/TLS avec le CPE (initiée par le CPE)
2.  Envoi d’une réponse après la réception d’une requête RPC vers le CPE
3.  Demander au CPE la valeur d’un paramètre
4.  Ordonner au CPE la modification d’un paramètre et de sa valeur
5.  Informer le CPE qu’il peut interrompre la connexion SSL/TLS

## Solutions Open-Source

Les plus connues :
-   [GenieACS](https://github.com/genieacs/genieacs)
-   [netcwmp](https://github.com/netcwmp/netcwmp)
-   [EasyCwmp](http://easycwmp.org/get/)
-   [freecwmp](http://www.freecwmp.org/)
-   [cwmpclient](http://bitbucket.org/spapas/cwmpclient)
-   [open-tr069](http://code.google.com/p/open-tr069/)

### Comparatif (GenieACS exclu) :
![](https://lh3.googleusercontent.com/F-wEj7nrR3r4iN-WGrttHIdIKxzz5HvN3ylTDDHW4tafsdH8ONLDxYF0Eqa6fgqUhIosYx9jgqB6aBxHziAj5MOr2-_XpMC7Q_RRYSLuPnZM-qZR757W34lxXXNZXvf8PNizcm1_)
![](https://lh4.googleusercontent.com/XylYy5O_vDi-zpC19y_rANcFyETNzG96FNHSbSLDczIpnlEy3zdQ0HIeyoawKZAhPFbxS-8XkuElVtLSBs9MPOQsUlXd1_f7cg2x65o47hiryTGTN-xvCH44CHoyoh3ZgfHizXpG)
> Comparatif des meilleures solutions Opensource datant du 01/07/2014
  
### Comparatif entre FreeACS & GenieACS
#### FreeACS :
- Développé en Java
- Excellente documentation
- Version stable
- Facile à installer
- Non mis à jour depuis longtemps
- Le script de déploiement ne semble pas fonctionner sur MikroTik
- L'interface (GUI) est très difficile d'utilisation et peu de modifications sont faisables
- Si un paramètre est modifiable, impossible de forcer la modification de valeur à chaque connexion avec le CPE.

#### GenieACS :
- Programmé avec Node.js & Ruby On Rails
- Très peu de documentation
- Difficile à installer
- Version stable (en installant les bonnes versions de paquets tel que Node.Js)
- Maintenu à jour
- Toutes les fonctionnalités fonctionnent (le déploiement de scripts vers MikroTik fonctionne, possiblité de mettre à jour les firmware etc...)
- Interface (GUI) très claire et simple d'utilisation, tout en étant opérationnelle
- API fonctionnelle et utilisable
- Possibilité de modifier les paramètres souhaités automatiquement et créer des configurations par défaut qui peuvent être implémentées à chaque connexion du CPE.

## Sources
### TR-069 :
[https://fr.wikipedia.org/wiki/TR-069](https://fr.wikipedia.org/wiki/TR-069)
[https://www.broadband-forum.org/download/TR-069_Amendment-6.pdf](https://www.broadband-forum.org/download/TR-069_Amendment-6.pdf)
[http://easycwmp.org/](http://easycwmp.org/)
[https://cwmp-data-models.broadband-forum.org/](https://cwmp-data-models.broadband-forum.org/)
[https://github.com/KanjiMonster/freecwmp](https://github.com/KanjiMonster/freecwmp)
[https://stackoverflow.com/questions/23240813/tr-069-cwmp-client-implementation-open-sources-comparison](https://stackoverflow.com/questions/23240813/tr-069-cwmp-client-implementation-open-sources-comparison)
[https://openwrt.org/downloads](https://openwrt.org/downloads)
[https://www.avsystem.com/crashcourse/tr069/](https://www.avsystem.com/crashcourse/tr069/)
[https://support.usr.com/support/9114/9114-fr-ug/device_tr069.html](https://support.usr.com/support/9114/9114-fr-ug/device_tr069.html)
[https://wiki.teltonika.lt/view/TR-069](https://wiki.teltonika.lt/view/TR-069)
[https://www.incognito.com/tutorials/faq-tr-069/](https://www.incognito.com/tutorials/faq-tr-069/)
[https://wiki.infomir.eu/eng/set-top-box/for-developers/stb-android/tr069-client/what-is-tr069-client](https://wiki.infomir.eu/eng/set-top-box/for-developers/stb-android/tr069-client/what-is-tr069-client)
[https://www.qacafe.com/tr-069-training/session-overview/](https://www.qacafe.com/tr-069-training/session-overview/)
[https://github.com/alepapadop/phpCWMP](https://github.com/alepapadop/phpCWMP)
[https://github.com/BroadbandForum/cwmp-data-models](https://github.com/BroadbandForum/cwmp-data-models)
[https://www.genivia.com/examples/tr069/](https://www.genivia.com/examples/tr069/)

### CPE :
[https://fr.wikipedia.org/wiki/Customer_Premises_Equipment](https://fr.wikipedia.org/wiki/Customer_Premises_Equipment)

### RPC :
[https://fr.wikipedia.org/wiki/Remote_procedure_call](https://fr.wikipedia.org/wiki/Remote_procedure_call)

### ACS :
[https://github.com/freeacs/freeacs/wiki](https://github.com/freeacs/freeacs/wiki)
[http://www.optokon.com/acs-automatic-configuration-server](http://www.optokon.com/acs-automatic-configuration-server)
[https://openacs.org/](https://openacs.org/)
[https://genieacs.com/](https://genieacs.com/)
[http://www.ijcst.org/Volume5/Issue3/p2_5_3.pdf](http://www.ijcst.org/Volume5/Issue3/p2_5_3.pdf)
[https://mum.mikrotik.com/presentations/EU18/presentation_5202_1523350603.pdf](https://mum.mikrotik.com/presentations/EU18/presentation_5202_1523350603.pdf)
[https://gist.github.com/AfroThundr3007730/e30fcb2fd9cf60365b21e34170b98199](https://gist.github.com/AfroThundr3007730/e30fcb2fd9cf60365b21e34170b98199)
[https://forum.mikrotik.com/viewtopic.php?t=116977](https://forum.mikrotik.com/viewtopic.php?t=116977)
[https://youtu.be/MoywoC8BC0M](https://youtu.be/MoywoC8BC0M)
[https://tr069.wordpress.com/2014/03/26/installing-genieacs-on-precise-pangolin/](https://tr069.wordpress.com/2014/03/26/installing-genieacs-on-precise-pangolin/)

### SOAP :
[https://fr.wikipedia.org/wiki/SOAP](https://fr.wikipedia.org/wiki/SOAP)
[https://youtu.be/dYH61zd7Qxo](https://youtu.be/dYH61zd7Qxo)