# API GenieACS

GenieACS propose une API basée sur le protocole HTTP qui utilise le JSON pour structurer les données.
> Si vous avez besoin de plus d'informations à propos des requêtes disponibles, référez vous aux requêtes MongoDB.

# Sommaire
1. [Ressources \(Resources\)](#ressources-resources)
1. [Fonctions \(Functions\)](#fonctions-functions)
    1. [GET /<i>\<collection\></i>/?query=<i>\<query\></i>](#get-collectionqueryquery)
        - [Exemples](#exemples-)
            1. [Rechercher un équipement par son identifiant *(ID)*, ici son identifiant est `202BC1-BM632w-0000000`](#rechercher-un-équipement-par-son-identifiant-id-ici-son-identifiant-est-202bc1-bm632w-0000000)
            1. [Rechercher un équipement par son adresse MAC, ici son adresse MAC est `20:2B:C1:E0:06:65`](#rechercher-un-équipement-par-son-adresse-mac-ici-son-adresse-mac-est-202bc1e00665)
            1. [Afficher les équipements qui n'ont pas envoyés de requête informelle ces sept derniers jours](#afficher-les-équipements-qui-nont-pas-envoyés-de-requête-informelle-ces-sept-derniers-jours)
            1. [Afficher les tâches/requêtes en attentes d'un équipement spécifique](#afficher-les-tâchesrequêtes-en-attentes-dun-équipement-spécifique)
            1. [Afficher une liste de plusieurs paramètres attribués à un équipement spécifique](#afficher-une-liste-de-plusieurs-paramètres-attribués-à-un-équipement-spécifique)
    1. [POST /devices/<i>\<device_id\></i>/tasks?<i>[connection_request]</i>](#post-devicesdevice_idtasksconnection_request)
        -  [Exemples](#exemples--1)
            1. [Rafraîchir tous les paramètres d'un équipement spécifique](#rafraîchir-tous-les-paramètres-dun-équipement-spécifique)
            1. [Changer le SSID du WiFi ainsi que son mot de passe](#changer-le-ssid-du-wifi-ainsi-que-son-mot-de-passe)
    1. [POST /tasks/<i>\<task_id\></i>/retry](#post-taskstask_idretry)
        - [Exemple](#exemple-)
            1. [Réessayer d'exécuter la tâche possédant l'identifiant *(ID)* `5403908ef28ea3a25c138adc` à la prochaine requête informelle]()
    1. [DELETE /tasks/<i>\<task_id\></i>](#delete-taskstask_id)
        - [Exemple](#exemple--1)
            1. [Supprimer la tâche qui possède l'identifiant `5403908ef28ea3a25c138adc` de la liste d'attente](#supprimer-la-tâche-qui-possède-lidentifiant-5403908ef28ea3a25c138adc-de-la-liste-dattente)
    1. [DELETE /faults/<i>\<fault_id\></i>](#delete-faultsfault_id)
        - [Exemple](#exemple--2)
            1. [Supprimer une erreur sur l'équipement possédant l'identifiant `202BC1-BM632w-0000000` sur le canal `default`]()
    1. [DELETE /devices/<i>\<device_id\></i>](#delete-devicesdevice_id)
        - [Exemple](#exemple--3)
            1. [Supprimer l'équipement possédant l'identifiant `202BC1-BM632w-000001`]()
    1. [POST /devices/<i>\<device_id\></i>/tags/<i>\<tag\></i>](#post-devicesdevice_idtagstag)
        - [Exemple](#exemple--4)
            1. [Assigner le tag `ExempleDeTag` à un équipement](#assigner-le-tag-exempledetag-à-un-équipement)
    1. [DELETE /devices/<i>\<device_id\></i>/tags/<i>\<tag\></i>](#delete-devicesdevice_idtagstag)
        - [Exemple](exemple--5)
            1. [Supprimer le tag `ExempleDeTag` à un équipement](#supprimer-le-tag-exempledetag-à-un-équipement)
    1. [PUT /presets/<i>\<preset_name\></i>](#put-presetspreset_name)
        - [Exemple](#exemple--6)
            1. [Créer un préréglage qui règle l'intervalle des requêtes informelles sur 5 minutes pour tous les équipements qui possèdent le tag `CinqMinutes`](#créer-un-préréglage-qui-règle-lintervalle-des-requêtes-informelles-sur-5-minutes-pour-tous-les-équipements-qui-possèdent-le-tag-cinqminutes)
    1. [DELETE /presets/<i>\<preset_name\></i>](#delete-presetspreset_name)
        - [Exemple](#exemple--7)
            1. [Supprimer le préréglage `PetitExemple`](#supprimer-le-préréglage-petitexemple)
    1. [PUT /files/<i>\<nomFichier\></i>](#put-filesnomfichier)
        - [Exemple](#exemple--8)
            1. [Envoyer une image *firmware* vers un équipement](#envoyer-une-image-firmware-vers-un-équipement)
    1. [DELETE /files/\<nomFichier\>](#delete-filesnomfichier)
        - [Exemple](#exemple--9)
            1. [Supprimer un fichier nommé `nouveau_firmware_v1.2.bin`](#supprimer-un-fichier-nommé-nouveau_firmware_v12bin)
    1. [GET /files/](#get-files)
        - [Exemple](#exemple--10)
            1. [Récupérer la liste de tous les fichiers disponibles sur l'ACS](#récupérer-la-liste-de-tous-les-fichiers-disponibles-sur-lacs)
    1. [GET /files/?query{"filename":"\<nomFichier\>"}](#get-filesqueryfilenamenomfichier)
        - [Exemple](#exemple--11)
            1. [Récupérer le fichier `incroyableFichierTest`](#récupérer-le-fichier-incroyablefichiertest)
1. [Tâches (Tasks)](#tâches-tasks)
    - [Exemple](#exemple--12)
        1. [Contenu JSON d'une réponse de l'ACS ou du CPE où l'identifiant de la tâche est `54dcacde2acb0b10130750d9`](#contenu-json-dune-réponse-de-lacs-ou-du-cpe-où-lidentifiant-de-la-tâche-est-54dcacde2acb0b10130750d9)
    1. [getParameterValues](#getparametervalues)
        - [Exemples](#exemples--2)
            1. [Récupérer la valeur des paramètres](#récupérer-la-valeur-des-paramètres-internetgatewaydevicewandevice1wanconnectiondevice1wanipconnectionnumberofentries--internetgatewaydevicetimentpserver1-et-internetgatewaydevicetimestatus)
            1. [Récupérer les paramètres de l'équipement possédant l'identifiant *(ID)*  `00236a-96318REF-SR360NA0A4%2D0003196`](#récupérer-les-paramètres-de-léquipement-possédant-lidentifiant-id--00236a-96318ref-sr360na0a42d0003196)
    1. [refreshObject](#refreshobject)
        - [Exemple](#exemple--14)
            1. [Actualiser la valeur du paramètre `InternetGatewayDevice.WANDevice.1.WANConnectionDevice` de l'équipement possédant l'identifiant *(ID)* `00236a-SR552n-SR552NA084%252D0003269`](#actualiser-la-valeur-du-paramètre-internetgatewaydevicewandevice1wanconnectiondevice-de-léquipement-possédant-lidentifiant-id-00236a-sr552n-sr552na084252d0003269)
    1. [setParameterValues](#setparametervalues)
        - [Exemples](#exemples--3)
            1. [Définir la valeur du paramètre `InternetGatewayDevice.ManagementServer.UpgradesManaged` comme étant `false`](#définir-la-valeur-du-paramètre-internetgatewaydevicemanagementserverupgradesmanaged-comme-étant-false)
            1. [Définir la valeur du paramètre `InternetGatewayDevice.ManagementServer.UpgradesManaged` comme étant `false`, celle du paramètre `InternetGatewayDevice.Time.Enable` comme étant `true` et celle du paramètre `InternetGatewayDevice.Time.NTPServer1` comme étant `pool.ntp.org`](#définir-la-valeur-du-paramètre-internetgatewaydevicemanagementserverupgradesmanaged-comme-étant-false-celle-du-paramètre-internetgatewaydevicetimeenable-comme-étant-true-et-celle-du-paramètre-internetgatewaydevicetimentpserver1-comme-étant-poolntporg)
    1. [addObject](#addobject)
        - [Exemple](#exemple--15)
            1. [Ajouter le paramètre `InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection` à l'équipement possédant l'identifiant *(ID)* `00236a-SR552n-SR552NA084%252D0003269`](#ajouter-le-paramètre-internetgatewaydevicewandevice1wanconnectiondevice1wanpppconnection-à-léquipement-possédant-lidentifiant-id-00236a-sr552n-sr552na084252d0003269)
    1. [reboot](#reboot)
        - [Exemple](#exemple--16)
            1. [Redémarrer l'équipement possédant l'identifiant *(ID)* `00236a-SR552n-SR552NA084%252D0003269`](#redémarrer-léquipement-possédant-lidentifiant-id-00236a-sr552n-sr552na084252d0003269)
    1. [Factory Reset](#factory-reset)
        - [Exemple](#exemple--17)
            1. [Réinitialiser l'équipement possédant l'identifiant *(ID)* `00236a-SR552n-SR552NA084%252D0003269` à l'état d'usine](#réinitialiser-léquipement-possédant-lidentifiant-id-00236a-sr552n-sr552na084252d0003269-à-létat-dusine)
    1. [download](#download)
        - [Exemple](#exemple--18)
            1. [Télécharger le fichier `mipsbe-6-42-lite.xml` de l'équipement possédant l'identifiant *(ID)* `00236a-SR552n-SR552NA084%252D0003269`](#télécharger-le-fichier-mipsbe-6-42-litexml-de-léquipement-possédant-lidentifiant-id-00236a-sr552n-sr552na084252d0003269)
    1. [Préréglages (Presets)](#préréglages-presets)
        - [Exemple](#exemple-de-préréglage-preset-)
            1. [Créer un préréglage qui règle l'intervalle des requêtes informelles sur 5 minutes pour tous les équipements qui possèdent le tag  `CinqMinutes`](#créer-un-préréglage-qui-règle-lintervalle-des-requêtes-informelles-sur-5-minutes-pour-tous-les-équipements-qui-possèdent-le-tag--cinqminutes)
1. [Provisions](#provisions)
    - [Exemples](#exemples--4)
        1. [Création d'une provision portant le nom `nouvelleProvisionDeQualité`](#création-dune-provision-portant-le-nom-nouvelleprovisiondequalité)
        1. [Supprimer une la provision portant le nom `ancienneProvision`](#supprimer-une-la-provision-portant-le-nom-ancienneprovision)
        1. [Récupérer la liste de toutes les "*provisions*"](#récupérer-la-liste-de-toutes-les-provisions)

## Ressources (Resources)
Les ressources suivantes peuvent être lues et/ou modifiées :
* `/devices/`
* `/devices/tasks/`
* `/devices/tags/`
* `/faults/`
* `/presets/`
* `/provisions/`
* `/files/`
* `/ping/`

## Fonctions (Functions)
### GET /<i>\<collection\></i>/?query=<i>\<query\></i>
> *`<collection>`* est à remplacer par la cible de nos recherches : `tasks`, `devices`, `presets`, `objects`...<br />
> *`<query>`* est à remplacer par la requête MongoDB.

Cette fonction permet de rechercher un objet dans la base de données et retourne une réponse sous forme de JSON.

#### Exemples :
* #### Rechercher un équipement par son identifiant *(ID)*, ici son identifiant est `202BC1-BM632w-0000000`.

        # query={"_id":"202BC1-BM632w-0000000"}
        
        curl -i 'http://localhost:7557/devices/?query=%7B%22_id%22%3A%22202BC1-BM632w-0000000%22%7D'

<br />

* #### Rechercher un équipement par son adresse MAC, ici son adresse MAC est `20:2B:C1:E0:06:65`.

        # query={
        #    "InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANIPConnection.1.MACAddress" :
        #       "20:2B:C1:E0:06:65"
        # }
        
        curl -i 'http://localhost:7557/devices/?query=%7B%22InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANIPConnection.1.MACAddress%22%3A%2220:2B:C1:E0:06:65%22%7D'

<br />

* #### Afficher les équipements qui n'ont pas envoyés de requête informelle ces sept derniers jours
	 > Les requêtes informelles signalent à l'ACS (ici GenieACS) que l'appareil est actif et contacte sans problème l'ACS.

        # query={
        #    "_lastInform" :
        #       {
        #           "$lt" : "2017-12-11 13:16:23 +0000"
        #       }
        # }
        
        curl -i 'http://localhost:7557/devices/?query=%7B%22_lastInform%22%3A%7B%22%24lt%22%3A%222017-12-11%2013%3A16%3A23%20%2B0000%22%7D%7D

<br />

* #### Afficher les tâches/requêtes en attentes d'un équipement spécifique

        # query={"device":"202BC1-BM632w-0000000"}
        
        curl -i 'http://localhost:7557/tasks/?query=%7B%22device%22%3A%22202BC1-BM632w-0000000%22%7D'

<br />

* #### Afficher une liste de plusieurs paramètres attribués à un équipement spécifique
  > La réponse est sous forme de liste dans laquelle chaque élément demandé est séparé par une virgule.

        # query={"_id":"202BC1-BM632w-0000000"}

        curl -i 'http://localhost:7557/devices?query=%7B%22_id%22%3A%22202BC1-BM632w-0000000%22%7D&projection=InternetGatewayDevice.DeviceInfo.ModelName,InternetGatewayDevice.DeviceInfo.Manufacturer'


<br />

### POST /devices/<i>\<device_id\></i>/tasks?<i>[connection_request]</i>
> *`<device_id>`* est à remplacer par l'ID de l'équipement concerné.<br />
> *`[connection_request]`* indique qu'une connexion sera requise pour toute requête qui devra être exécutée instantanément. Sans connexion la tâche sera ajoutée à la file d'attente et sera exécutée à la prochaine requête informelle.

Cette fonction permet d'exécuter une tâche sur un équipement spécifique. Le code d'état *(status code)* `200` est retourné si la tâche a bien été exécutée. Le code d'état *(status code)* `202` est retourné si la tâche a été ajoutée à la liste d'attente et qu'elle sera exécutée à la prochaine requête informelle de l'équipement concerné.

#### Exemples :
* #### Rafraîchir tous les paramètres d'un équipement spécifique

        curl -i 'http://localhost:7557/devices/202BC1-BM632w-0000000/tasks?connection_request' \
        -X POST \
        --data '{"name":"refreshObject", "objectName":""}'

* #### Changer le SSID du WiFi ainsi que son mot de passe

        # query={
        #   "name":"setParameterValues",
        #   "parameterValues":
        #      [
        #         ["InternetGatewayDevice.LANDevice.1.WLANConfiguration.1.SSID", "Nouveau SSID", "xsd:string"],
        #         ["InternetGatewayDevice.LANDevice.1.WLANConfiguration.1.PreSharedKey.1.PreSharedKey", "Nouveau mot de passe", "xsd:string"]
        #      ]
        # }
        
        curl -i 'http://localhost:7557/devices/202BC1-BM632w-0000000/tasks?connection_request' \
        -X POST \
        --data '{"name":"setParameterValues", "parameterValues":[["InternetGatewayDevice.LANDevice.1.WLANConfiguration.1.SSID", "Nouveau SSID", "xsd:string"],["InternetGatewayDevice.LANDevice.1.WLANConfiguration.1.PreSharedKey.1.PreSharedKey", "Nouveau mot de passe", "xsd:string"]]}'

### POST /tasks/<i>\<task_id\></i>/retry
> *`<task_id>`* est à remplacer par l'identifiant *(ID)* de la tâche concernée.

Cette fonction permet de réessayer d'exécuter une tâche à la prochaine requête informelle grâce à son identifiant *(ID)*.


#### Exemple :
* #### Réessayer d'exécuter la tâche possédant l'identifiant *(ID)* `5403908ef28ea3a25c138adc` à la prochaine requête informelle

        curl -i 'http://localhost:7557/tasks/5403908ef28ea3a25c138adc/retry' -X POST
    
### DELETE /tasks/<i>\<task_id\></i>
> *`<task_id>`* est à remplacer par l'identifiant *(ID)* de la tâche concernée. Pour récupérer les identifiant *(ID)* des tâches en attentes, utiliser la requête `GET /tasks`.

Cette fonction permet de supprimer une tâche de la liste d'attente grâce à son identifiant *(ID)*.


#### Exemple :
* #### Supprimer la tâche qui possède l'identifiant `5403908ef28ea3a25c138adc` de la liste d'attente

	    curl -i 'http://localhost:7557/tasks/5403908ef28ea3a25c138adc' -X DELETE

### DELETE /faults/<i>\<fault_id\></i>

> *`<fault_id>`* est à remplacer par l'identifiant *(ID)* de l'erreur concernée. Pour récupérer les identifiants *(ID)* des erreurs, utiliser la requête `GET /faults`. Les identifiants *(ID)* sont aux format `\<IDEquipement\>:\<Cannal\>`

Cette fonction permet de supprimer une erreur.


#### Exemple :
* #### Supprimer une erreur sur l'équipement possédant l'identifiant `202BC1-BM632w-0000000` sur le canal `default`

        curl -i 'http://localhost:7557/faults/202BC1-BM632w-0000000:default' -X DELETE

### DELETE /devices/<i>\<device_id\></i>

> *`<device_id>`* est à remplacer par l'identifiant *(ID)* de l'équipement concerné.

Cette fonction permet de supprimer un équipement au sein de la liste des équipements connectés à l'ACS.
<br />
Toutefois l'équipement sera de nouveau enregistré lors de sa prochaine connexion à l'ACS, y compris pour les requêtes informelles.


#### Exemple :
* #### Supprimer l'équipement possédant l'identifiant `202BC1-BM632w-000001`

        curl -X DELETE -i 'http://localhost:7557/devices/202BC1-BM632w-000001'

 ### POST /devices/<i>\<device_id\></i>/tags/<i>\<tag\></i>
> *`<device_id>`* est à remplacer par l'identifiant *(ID)* de l'équipement concerné.<br />
> *`<tag>`* est à remplacer par le tag à attribuer.

Cette fonction permet d'assigner un tag à un équipement spécifié. Si le tag spécifié est déjà associé à l'équipement concerné, il n'y aura aucune modification.

#### Exemple :
* #### Assigner le tag `ExempleDeTag` à un équipement
	    curl -i 'http://localhost:7557/devices/202BC1-BM632w-0000000/tags/ExempleDeTag' -X POST

### DELETE /devices/<i>\<device_id\></i>/tags/<i>\<tag\></i>
> *`<device_id>`* est à remplacer par l'identifiant *(ID)* de l'équipement concerné.<br />
> *`<tag>`* est à remplacer par le tag à attribuer.

Cette fonction permet de supprimer un tag d'un équipement spécifique.

#### Exemple :
* #### Supprimer le tag `ExempleDeTag` à un équipement

	    curl -i 'http://localhost:7557/devices/202BC1-BM632w-0000000/tags/ExempleDeTag' -X DELETE

### PUT /presets/<i>\<preset_name\></i>
> *`<preset_name>`* est à remplacer par le nom du préréglage (preset) concerné. <br />
> **⚠️ Le nom d'un préréglage ne peut pas contenir de `.` ⚠️**

Cette fonction permet de créer ou modifier un préréglage (preset). Retourne le code d'état *(status code)* `200` si le préréglage a bien été ajouté/modifié. Le corps (body) de la requête est une représentation JSON du préréglage. Se référer à l'exemple ci-dessous pour mieux comprendre le format du préréglage.

#### Exemple :
* #### Créer un préréglage qui règle l'intervalle des requêtes informelles sur 5 minutes pour tous les équipements qui possèdent le tag `CinqMinutes`

	    # query={
	    #    weight: 0,
	    #    precondition: "{\"_tags\":\"CinqMinutes\"}"
	    #    configurations:
	    #       [
	    #           { type: "value",
	    #             name: "InternetGatewayDevice.ManagementServer.PeriodicInformEnable", value: "true" },
	    #           { type: "value", name: "InternetGatewayDevice.ManagementServer.PeriodicInformInterval",
	    #              value: "300" }
	    #       ]
	    # }
	    
	    curl -i 'http://localhost:7557/presets/inform' \
	    -X PUT \
	    --data '{ "weight": 0, "precondition": "{\"_tags\":\"CinqMinutes\"}", "configurations": [ { "type": "value", "name": "InternetGatewayDevice.ManagementServer.PeriodicInformEnable", "value": "true" }, { "type": "value", "name": "InternetGatewayDevice.ManagementServer.PeriodicInformInterval", "value": "300" } ] }'

	> `type:` possibles :
	>	- `"value"` : Correspond à la tâche *(action)* [`setParameterValues`](#setparametervalues). Son `name:` est le nom du paramètre à modifier et son `value:` est la valeur à attribuer au paramètre.
	>	- `"add_object"` : Correspond à la tâche *(action)* [`addObject`](#addobject). Son `name:` est le nom de l'objet parent auquel est rattaché le nouvel objet et son `object:` est le nom du nouvel objet.
	>	- `"delete_object"` : Permet de supprimer un objet *(paramètre)* présent dans la configuration d'un équipement tel qu'une règle de pare-feu. Son `name:` est le nom de l'objet parent auquel est rattaché le nouvel objet et son `object:` est le nom du nouvel objet.
	>	- `"provision"` : Permet de faire appel à un script de provision. Son `name:` est le nom du script de provision auquel faire appel.

### DELETE /presets/<i>\<preset_name\></i>
> *`<preset_name>`* est à remplacer par le nom du préréglage (preset) concerné. 

Cette fonction permet de supprimer un préréglage (preset).
#### Exemple :
* #### Supprimer le préréglage `PetitExemple`

	    curl -i 'http://localhost:7557/presets/PetitExemple' -X DELETE

### PUT /files/<i>\<nomFichier\></i>
> *`<nomFichier>`* est à remplacer par le nom du fichier concerné. 

Cette fonction permet d'envoyer un fichier ou de mettre à jour un fichier déjà téléchargé sur l'équipement. Retourne le code d'état *(status code)* `200` si le fichier est correctement ajouté/mis à jour. Le contenu du fichier peut être envoyé en tant que corps (body) de la requête.

Les métadonnées du fichier sont envoyées dans les en-têtes (headers) de la requête.<br />
<br />
Il y a quatre métadonnées pour chaque fichier :<br />
<br />
- *`fileType`*: Pour une image *firmware* vaut `1 Firmware Upgrade Image`. Pour les autres types de fichiers les plus communs, `fileType` peut valoir `2 Web Content` ou bien `3 Vendor Configuration File`.
- *`oui`*: L'identifiant du constructeur *(Organizational Unit Identifier)* de l'équipement auquel le fichier appartient.
- *`productClass`*: La classe de produit de l'équipement concerné par le fichier.
- *`version`*: Dans le cas d'une image *firmware*, il s'agit de la version du *firmware*.

#### Exemple :
* #### Envoyer une image *firmware* vers un équipement
	
	    curl -i 'http://localhost:7557/files/new_firmware_v1.0.bin' \
	    -X PUT \
	    --data-binary @"./new_firmware_v1.0.bin" \
	    --header "fileType: 1 Firmware Upgrade Image" \
	    --header "oui: 123456" \
	    --header "productClass: ABC" \
	    --header "version: 1.0"

### DELETE /files/\<nomFichier\>
> *`<nomFichier>`* est à remplacer par le nom du fichier concerné. 

Cette fonction permet de supprimer un fichier transféré précédemment.

#### Exemple :
* #### Supprimer un fichier nommé `nouveau_firmware_v1.2.bin`

		curl -i 'http://localhost:7557/files/nouveau_firmware_v1.2.bin' -X DELETE

### GET /files/
Cette fonction permet de récupérer la liste de tous les fichiers précédemment upload et encore disponibles sur l'ACS.

#### Exemple :
* #### Récupérer la liste de tous les fichiers disponibles sur l'ACS

		curl -i 'http://localhost:7557/files/' -X GET

### GET /files/?query{"filename":"\<nomFichier\>"}
> *`<nomFichier>`* est à remplacer par le nom du fichier concerné. 

Cette fonction permet de récupérer un fichier en fonction de son nom.

#### Exemple :
* #### Récupérer le fichier `incroyableFichierTest`

		curl -i 'http://localhost:7557/files/?query{"filename":"incroyableFichierTest"}' -X GET

## Tâches (Tasks)
Dans l'URL spécifié, `&connection_request` indique à GenieACS de se connecter à l'équipement *(CPE)*.<br />
<br />
Si la réponse de l'ACS (GenieACS) est le code d'état *(status code)* `202`, alors l'équipement n'a pas répondu à la commande avant que le délai ne soit expiré *(timeout)*. L'équipement pourra encore traiter la requête (ou envoyer une réponse) un peu plus tard.<br />
<br />
L'identifiant *(ID)* de chaque tâche *(action)* se trouve dans le contenu JSON de la réponse en tant  que `"_id"`.

#### Exemple :
* #### Contenu JSON d'une réponse de l'ACS ou du CPE où l'identifiant de la tâche est `54dcacde2acb0b10130750d9`
	<pre><code>{
	<b>"_id": "54dcacde2acb0b10130750d9"</b>,
	"device": "00236a-96318REF-SR360NA0A4%252D0003196",
	"name": "addObject",
	"objectName": "InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection",
	"timestamp": "2015-02-12T13:38:38.256Z"
  }</code></pre>
  
Si la réponse de l'ACS (GenieACS) est le code d'état *(status code)* `200`, alors l'équipement a répondu à la commande avant que le délai ne soit expiré *(timeout)* et l'action *(tâche)* a bien été effectuée. Les tâches possibles sont par exemple : `setParameterValues`, `reboot`,  ou `refreshObject`...

### getParameterValues
Cette tâche *(action)* permet de récupérer la valeur d'un ou plusieurs paramètres d'un équipement *(CPE)* spécifique.<br />
<br />
Une fois que l'équipement a retourné sa réponse *(le résultat)* à GenieACS, il est possible d'effectuer une requête auprès de GenieACS pour extraire du JSON les paramètres souhaités.

#### Exemples :
* #### Récupérer la valeur des paramètres `InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANIPConnectionNumberOfEntries` , `InternetGatewayDevice.Time.NTPServer1`, et `InternetGatewayDevice.Time.Status`
        # query={
        #    "name": "getParameterValues",
        #    "parameterNames":
        #       [
        #          "InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANIPConnectionNumberOfEntries",
        #          "InternetGatewayDevice.Time.NTPServer1", "InternetGatewayDevice.Time.Status"
        #       ]
        # }
        
        curl -i 'http://localhost:7557/devices/00236a-96318REF-SR360NA0A4%252D0003196/tasks?timeout=3000&connection_request' \
        -X POST \
        --data '{ "name": "getParameterValues", "parameterNames": ["InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANIPConnectionNumberOfEntries", "InternetGatewayDevice.Time.NTPServer1", "InternetGatewayDevice.Time.Status"] }'

* #### Récupérer les paramètres de l'équipement possédant l'identifiant *(ID)*  `00236a-96318REF-SR360NA0A4%2D0003196`

        # query={"_id":"00236a-96318REF-SR360NA0A4%2D0003196"}
        
        curl -i 'http://localhost:7557/devices/?query=%7B%22_id%22%3A%2200236a-96318REF-SR360NA0A4%252D0003196%22%7D'

### refreshObject
Cette tâche *(action)* permet d'actualiser les valeurs d'un ou plusieurs paramètres d'un équipement spécifique et mettre à jour les informations sur GenieACS.

#### Exemple :
* #### Actualiser la valeur du paramètre `InternetGatewayDevice.WANDevice.1.WANConnectionDevice` de l'équipement possédant l'identifiant *(ID)* `00236a-SR552n-SR552NA084%252D0003269`
        curl -i 'http://localhost:7557/devices/00236a-SR552n-SR552NA084%252D0003269/tasks?timeout=3000&connection_request' \
        -X POST \
        --data '{ "name": "refreshObject", "objectName": "InternetGatewayDevice.WANDevice.1.WANConnectionDevice" }'

### setParameterValues
Cette tâche *(action)* permet de définir la valeur d'un ou plusieurs paramètres d'un équipement.<br />
<br />
L'ACS devrait répondre par `200 OK` ou <pre><code>202 Accepted <i>exempleValeurParamètre</i></code></pre> pour signaler que la modification a bien été effectuée.

> *exempleValeurParamètre* est remplacé par la valeur qui a normalement été attribuée au paramètre

#### Exemples :
* #### Définir la valeur du paramètre `InternetGatewayDevice.ManagementServer.UpgradesManaged` comme étant `false`
        curl -i 'http://localhost:7557/devices/00236a-SR552n-SR552NA084%252D0003269/tasks?timeout=3000&connection_request' \
        -X POST \
        --data '{ "name": "setParameterValues", "parameterValues": [["InternetGatewayDevice.ManagementServer.UpgradesManaged",false]] }'

* #### Définir la valeur du paramètre `InternetGatewayDevice.ManagementServer.UpgradesManaged` comme étant `false`, celle du paramètre `InternetGatewayDevice.Time.Enable` comme étant `true` et celle du paramètre `InternetGatewayDevice.Time.NTPServer1` comme étant `pool.ntp.org`

        curl -i 'http://localhost:7557/devices/00236a-SR552n-SR552NA084%252D0003269/tasks?timeout=3000&connection_request' \
        -X POST \
        --data '{ "name": "setParameterValues", "parameterValues": [["InternetGatewayDevice.ManagementServer.UpgradesManaged", false], ["InternetGatewayDevice.Time.Enable", true], ["InternetGatewayDevice.Time.NTPServer1", "pool.ntp.org"]]

### addObject
Cette tâche *(action)* permet d'ajouter un paramètre non configuré ou nouveau à un équipement. Par exemple pour créer un nouvelle règle de pare-feu.

#### Exemple :
* ####  Ajouter le paramètre `InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection` à l'équipement possédant l'identifiant *(ID)* `00236a-SR552n-SR552NA084%252D0003269`
        curl -i 'http://localhost:7557/devices/00236a-SR552n-SR552NA084%252D0003269/tasks?timeout=3000&connection_request' \
        -X POST \
        --data '{"name":"addObject","objectName":"InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection"}'

### reboot
Cette tâche *(action)* permet de redémarrer un équipement *(CPE)*.

#### Exemple :
* #### Redémarrer l'équipement possédant l'identifiant *(ID)* `00236a-SR552n-SR552NA084%252D0003269`
        curl -i 'http://localhost:7557/devices/00236a-SR552n-SR552NA084%252D0003269/tasks?timeout=3000&connection_request' \
        -X POST \
        --data '{ "name": "reboot" }'

### Factory Reset
Cette tâche *(action)* permet de réinitialiser un équipement à l'état d'usine.

#### Exemple :
* #### Réinitialiser l'équipement possédant l'identifiant *(ID)* `00236a-SR552n-SR552NA084%252D0003269` à l'état d'usine
        curl -i 'http://localhost:7557/devices/00236a-SR552n-SR552NA084%252D0003269/tasks?timeout=3000&connection_request' \
        -X POST \
        --data '{ "name": "factoryReset" }'

### download
Cette tâche *(action)* permet de télécharger un fichier présent sur un équipement.<br />
<br />
Lors de la requête, spécifier le nom du fichier *(la valeur de `"_id"`, trouvable grâce à [cette fonction](#get-files))* dans l'option `"file"`. Voir l'exemple ci-dessous.

#### Exemple :
* #### Télécharger le fichier `mipsbe-6-42-lite.xml` de l'équipement possédant l'identifiant *(ID)* `00236a-SR552n-SR552NA084%252D0003269`
	<pre><code>curl -i 'http://localhost:7557/devices/00236a-SR552n-SR552NA084%252D0003269/tasks?timeout=3000&connection_request' \
		-X POST \
		--data '{ "name": "download", <b>"file": "mipsbe-6-42-lite.xml"</b>}'</code></pre>

## Préréglages (Presets)
Les préréglages *(presets)* sont similaires à des *templates* de configurations. Ils peuvent concerner un ou plusieurs équipements.
* Afin de configurer un ou plusieurs équipements spécifiques, il est possible d'ajouter des préconditions *(preconditions)*.
	> Par exemple cela peut être l'identifiant de fabricant des équipements, s'ils correspondent la configuration sera appliquée.

* Afin de configurer l'équipement désiré lors de certains événements *(events)*, il est possible de spécifier à partir de quel événement la configuration sera appliquée à un ou plusieurs équipements.
	> Par exemple cela peut être au démarrage de la machine avec la valeur `**1 BOOT**` <br />

* Il est également possible de spécifier l'ordre d'importance des préréglages. 
	> Par exemple si a un préréglage 1 avec une priorité à 100 & préréglage 2 avec une priorité à 200. Le préréglage 2 sera prioritaire sur le préréglage 1, donc la configuration du préréglage 2 sera utilisée en priorité.

* Il est tout aussi possible d'envoyer vers le ou les équipements la configuration spécifiée dans le préréglage toutes les X secondes/minutes/heures/jours/etc...<br />

* Bien sûr, il est possible de définir la configuration liée au préréglage.<br />

	#### Exemple de préréglage (preset) :
	* #### [Créer un préréglage qui règle l'intervalle des requêtes informelles sur 5 minutes pour tous les équipements qui possèdent le tag  `CinqMinutes`](#créer-un-préréglage-qui-règle-lintervalle-des-requêtes-informelles-sur-5-minutes-pour-tous-les-équipements-qui-possèdent-le-tag-cinqminutes)

### Provisions
Une "*provision*" javascript est une entrée *(input)* dans le corps *(body)* de la requête HTTP.

#### Exemples :
* #### Création d'une provision portant le nom `nouvelleProvisionDeQualité`
	
	    curl -X PUT -i 'http://localhost:7557/provisions/nouvelleProvisionDeQualité' --data 'log("Provision started at " + now);'

* #### Supprimer une la provision portant le nom `ancienneProvision`
	
	    curl -X DELETE -i 'http://localhost:7557/provisions/ancienneProvision'

* #### Récupérer la liste de toutes les "*provisions*"
	    curl -X GET -i 'http://localhost:7557/provisions/'
