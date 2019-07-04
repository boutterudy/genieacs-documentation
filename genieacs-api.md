
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

    curl -i 'http://localhost:7557/faults/202BC1-BM632w-0000000:default' -X DELETE

### DELETE /devices/<i>\<device_id\></i>

> *`<device_id>`* est à remplacer par l'identifiant *(ID)* de l'équipement concerné.

Cette fonction permet de supprimer un équipement au sein de la liste des équipements connectés à l'ACS.
<br />
Toutefois l'équipement sera de nouveau enregistré lors de sa prochaine connexion à l'ACS, y compris pour les requêtes informelles.


#### Exemple :

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

## Tâches
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
  }
</code></pre>

Si la réponse de l'ACS (GenieACS) est le code d'état *(status code)* `200`, alors l'équipement a répondu à la commande avant que le délai ne soit expiré *(timeout)* et l'action *(tâche)* a bien été effectuée. Les tâches possibles sont par exemple : `setParameterValues`, `reboot`,  ou `refreshObject`...

### getParameterValues
Cette tâche *(action)* permet de récupérer la valeur d'un ou plusieurs paramètres d'un équipement *(CPE)* spécifique.<br />
<br />
Une fois que l'équipement a retourné sa réponse *(le résultat)* à GenieACS, il est possible d'effectuer une requête auprès de GenieACS pour extraire du JSON les paramètres souhaités.

#### Exemple :
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
Lors de la requête, spécifier le nom du fichier *(la valeur de `"_id"`, trouvable grâce à [cette fonction]()* dans l'option `"file"`. Voir l'exemple ci-dessous.

#### Exemple :
* #### Télécharger le fichier `mipsbe-6-42-lite.xml` de l'équipement possédant l'identifiant *(ID)* `00236a-SR552n-SR552NA084%252D0003269`
	<pre><code>curl -i 'http://localhost:7557/devices/00236a-SR552n-SR552NA084%252D0003269/tasks?timeout=3000&connection_request' \
		-X POST \
		--data '{ "name": "download", <b>"file": "mipsbe-6-42-lite.xml"</b>}'</code></pre>

