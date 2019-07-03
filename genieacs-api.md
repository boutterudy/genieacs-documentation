


# API GenieACS

GenieACS propose une API basée sur le protocole HTTP qui utilise le JSON pour structurer les données.
> Si vous avez besoin de plus d'informations à propos des requêtes disponibles, référez vous aux requêtes MongoDB.

## Ressources
Les ressources suivantes peuvent être lues et/ou modifiées :
* `/devices/`
* `/devices/tasks/`
* `/devices/tags/`
* `/faults/`
* `/presets/`
* `/provisions/`
* `/files/`
* `/ping/`

## Fonctions
### GET /<i>\<collection\></i>/?query=<i>\<query\></i>
> *`<collection>`* est à remplacer par la cible de nos recherches : `tasks`, `devices`, `presets`, `objects`...<br />
> *`<query>`* est à remplacer par la requête MongoDB.

Cette fonction permet de rechercher un objet dans la base de données et retourne une réponse sous forme de JSON.

#### Exemples :
* #### Rechercher un équipement par son ID

        # query={"_id":"202BC1-BM632w-0000000"}
        
        curl -i 'http://localhost:7557/devices/?query=%7B%22_id%22%3A%22202BC1-BM632w-0000000%22%7D'

<br />

* #### Rechercher un équipement par son adresse MAC

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

Cette fonction permet d'exécuter une tâche sur un équipement spécifique. Le statut `200` est retourné si la tâche a bien été exécutée. Le statut `202` est retourné si la tâche a été ajoutée à la liste d'attente et qu'elle sera exécutée à la prochaine requête informelle de l'équipement concerné.

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
> *`<task_id>`* est à remplacer par l'ID de la tâche concernée.

Cette fonction permet de réessayer d'exécuter une tâche à la prochaine requête informelle grâce à son ID.


#### Exemple :

    curl -i 'http://localhost:7557/tasks/5403908ef28ea3a25c138adc/retry' -X POST
    
### DELETE /tasks/<i>\<task_id\></i>
> *`<task_id>`* est à remplacer par l'ID de la tâche concernée. Pour récupérer les ID des tâches en attentes, utiliser la requête `GET /tasks`.

Cette fonction permet de supprimer une tâche de la liste d'attente grâce à son ID.


#### Exemple :

    curl -i 'http://localhost:7557/tasks/5403908ef28ea3a25c138adc' -X DELETE

### DELETE /faults/<i>\<fault_id\></i>

> *`<fault_id>`* est à remplacer par l'ID de l'erreur concernée. Pour récupérer les ID des erreurs, utiliser la requête `GET /faults`. Les ID sont aux format `\<IDEquipement\>:\<Cannal\>`

Cette fonction permet de supprimer une erreur.


#### Exemple :

    curl -i 'http://localhost:7557/faults/202BC1-BM632w-0000000:default' -X DELETE

### DELETE /devices/<i>\<device_id\></i>

> *`<device_id>`* est à remplacer par l'ID de l'équipement concerné.

Cette fonction permet de supprimer un équipement au sein de la liste des équipements connectés à l'ACS.
<br />
Toutefois l'équipement sera de nouveau enregistré lors de sa prochaine connexion à l'ACS, y compris pour les requêtes informelles.


#### Exemple :

        curl -X DELETE -i 'http://localhost:7557/devices/202BC1-BM632w-000001'

 ### POST /devices/<i>\<device_id\></i>/tags/<i>\<tag\></i>
> *`<device_id>`* est à remplacer par l'ID de l'équipement concerné.<br />
> *`<tag>`* est à remplacer par le tag à attribuer.

Cette fonction permet d'assigner un tag à un équipement spécifié. Si le tag spécifié est déjà associé à l'équipement concerné, il n'y aura aucune modification.

#### Exemple :
* #### Assigner le tag "ExempleDeTag" à un équipement
	    curl -i 'http://localhost:7557/devices/202BC1-BM632w-0000000/tags/ExempleDeTag' -X POST

### DELETE /devices/<i>\<device_id\></i>/tags/<i>\<tag\></i>
> *`<device_id>`* est à remplacer par l'ID de l'équipement concerné.<br />
> *`<tag>`* est à remplacer par le tag à attribuer.

Cette fonction permet de supprimer un tag d'un équipement spécifique.

#### Exemple :
* #### Supprimer le tag "ExempleDeTag" à un équipement

	    curl -i 'http://localhost:7557/devices/202BC1-BM632w-0000000/tags/ExempleDeTag' -X DELETE

### PUT /presets/<i>\<preset_name\></i>
> *`<preset_name>`* est à remplacer par le nom du préréglage (preset) concerné. <br />
> **⚠️ Le nom d'un préréglage ne peut pas contenir de `.` ⚠️**

Cette fonction permet de créer ou modifier un préréglage (preset). Retourne le statut 200 si le préréglage a bien été ajouté/modifié. Le corps (body) de la requête est une représentation JSON du préréglage. Se référer à l'exemple ci-dessous pour mieux comprendre le format du préréglage.

#### Exemple :
* #### Créer un préréglage qui règle l'intervalle des requêtes informelles sur 5 minutes pour tous les équipements qui possèdent le tag "CinqMinutes"

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

### DELETE /presets/<i>\<preset_name\></i>
> *`<preset_name>`* est à remplacer par le nom du préréglage (preset) concerné. 

Cette fonction permet de supprimer un préréglage (preset).
#### Exemple :
* #### Supprimer le préréglage `PetitExemple`

	    curl -i 'http://localhost:7557/presets/PetitExemple' -X DELETE

### PUT /files/<i>\<file_name\></i>
> *`<file_name>`* est à remplacer par le nom de l'équipement concerné. 

Cette fonction permet d'envoyer un fichier ou de mettre à jour un fichier déjà téléchargé sur l'équipement. Retourne le statut `200` si le fichier est correctement ajouté/mis à jour. Le contenu du fichier peut être envoyé en tant que corps (body) de la requête.

Les métadonnées du fichier sont envoyées dans les en-têtes (headers) de la requête.<br />
<br />
Il y a quatre métadonnées :<br />
<br />
<i>[EN COURS DE REDACTION]</i>
