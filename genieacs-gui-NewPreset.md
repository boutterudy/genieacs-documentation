# GenieACS New Preset | GenieACS Nouveau Préréglage
Pour créer un nouveau preset *(préréglage)*, vous pouvez soit y accéder en utilisant les onglets de l’interface graphique (Onglet “Presets” > “New Preset”), ou directement aller à la page de création de preset via cet URL : `http://192.168.254.112:3000/presets/new`.
> `192.168.254.112` étant l’adresse IP du serveur qui permet l’accès à l’interface graphique de GenieACS.
<br />
Bien sûr si vous n'êtes pas connecté en tant qu'administrateur une connexion vous sera demandée.
<br />
La page suivante apparaît :

![Capture d'écran de la page de création d'un nouveau préset](/Images/GenieACS-NewPreset.png)

Remplissez donc les champs en fonction de vos besoins.

## Explications des champs
`Name` :  Correspond au nom du preset

<br />

`Channel` : Correspond au nom du canal sous lequel le preset sera executé. Si aucun nom n’est donné, le nom du canal par défaut est “default”. Les noms de canal sont utilisés pour regrouper les préréglages. Si une exception se produit sur un canal, seuls les préréglages de ce canal seront temporairement désactivés.

<br />

`Weight` : Correspond au niveau de priorité du preset. Plus il est élevé, plus le preset sera prioritaire.

> Exemple : Preset 1 avec un weight à 100 & Preset 2 avec un weight à 200. Preset 2 sera prioritaire sur le Preset 1, donc attribué en priorité.

<br />

`Schedule` :  L’expression Cron renseignée spécifie quand le preset sera actif, et la durée à laquelle il le sera. La durée correspond à la fenêtre temporelle en secondes. Comme précisé précédemment, le schedule utilise l’expression Cron. Si spécifié, le preset sera uniquement actif dans la période renseignée. Le temps spécifié est en UTC. 

> Exemple : Schedule “3600 * * 3 * 1-5” définit la période active comme étant tous les matins, de 3h00 à 4h00, du mois de janvier à mai.

<br />

`Events` : Correspond aux événements qui feront appel au preset. Si un événement est spécifié, ils doivent tous être présents. Pour exclure un événement, ajouter un - avant le nom de l’événement. Si aucun événement n’est spécifié, le preset sera utilisé à chaque fois que le CPE communique avec l’ACS.
<br /><br />
Les événements existants sont les suivants :

|**Nom de l’événement**|**Description**|
|---|---|
|`0 BOOTSTRAP`|Correspond au démarrage initial. Correspond aussi au démarrage suivant une réinitialisation à l’état d’usine.<br /><br />*Attention : `0 BOOTSTRAP` est généralement suivi de l’événement `1 BOOT`.*|
|`1 BOOT`|Correspond au démarrage du CPE.|
|`2 PERIODIC`|Correspond à la réception des requêtes informelles du CPE qui signalent à l’ACS, a intervalle régulière, qu’il est bien en service, tout en transmettant les paramètres actuels du CPE.<br  /><br />*Cette intervalle peut être spécifiée à travers le paramètre suivant : `InternetGatewayDevice.ManagementServer.PeriodicInformInterval`*|
|`4 VALUE CHANGE`|Lorsqu’un des paramètres de notification actifs ou passifs a changé depuis la dernière requête informelle du CPE.|
|`6 CONNECTION REQUEST`|Lorsque la session est établie suite à une demande de connexion à l’ACS.|
|`7 TRANSFER COMPLETE`|Lorsque le CPE a correctement upload ou téléchargé un fichier.|
|`8 DIAGNOSTICS COMPLETE`|Lorsque la connection à l’ACS est établie après un diagnostic complet des tests initié par l’ACS.|
|`9 REQUEST DOWNLOAD`|Lorsque la session dédiée au CPE fait appel à la méthode RequestDownload.|
|`M Reboot`|Lorsque le CPE redémarre à la demande de l’ACS.|
|`M Download`|Lorsque l’ACS a demandé le téléchargement d’un contenu.<br /><br />*Attention : `M Download` est généralement suivi de l’événement `7 TRANSFER COMPLETE`.*|

<br />

`Precondition` : La ou les conditions requises pour que le preset soit utilisé. Les options sont directement enregistrées dans le fichier `genieacs-gui/config/index_parameters.yml`.
<br /><br />
Par défaut les préconditions sont les suivantes :

|**Précondition**|**Description**|
|---|---|
|![Capture d'écran du champ "Last inform"](/Images/GenieACS-NewPreset-PreconditionLastInform.png)|Si la dernière requête informelle du CPE possède une information =, ≠, <, >, ≤ ou ≥ à celle renseigné.|
|![Capture d'écran du champ "Tag"](/Images/GenieACS-NewPreset-PreconditionTag.png)|Si le CPE possède un Tag =, ≠, <, >, ≤ ou ≥ à celui renseigné.|
|![Capture d'écran du champ "Serial number"](/Images/GenieACS-NewPreset-PreconditionSerialNumber.png)|Si le CPE possède un numéro de série =, ≠, <, >, ≤ ou ≥ à celui renseigné.|
|![Capture d'écran du champ "Product class"](/Images/GenieACS-NewPreset-PreconditionProductClass.png)|Si le CPE appartient à une classe de produit =, ≠, <, >, ≤ ou ≥ à celle renseignée.|
|![Capture d'écran du champ "OUI"](/Images/GenieACS-NewPreset-PreconditionOUI.png)|Si le CPE possède un identifiant de constructeur (OUI, Organizational Unit Identifier) =, ≠, <, >, ≤ ou ≥ à celui renseigné.|
|![Capture d'écran du champ "Manufacturer"](/Images/GenieACS-NewPreset-PreconditionManufacturer.png)|Si le CPE a été conçu par un fabricant =, ≠, <, >, ≤ ou ≥ à celui renseigné.|
|![Capture d'écran du champ "Hardware version"](/Images/GenieACS-NewPreset-PreconditionHardwareVersion.png)|Si le CPE possède une version matérielle =, ≠, <, >, ≤ ou ≥ à celle renseignée.|
|![Capture d'écran du champ "Software version"](/Images/GenieACS-NewPreset-PreconditionSoftwareVersion.png)|Si le CPE possède une version logicielle =, ≠, <, >, ≤ ou ≥ à celle renseignée.|
|![Capture d'écran du champ "MAC"](/Images/GenieACS-NewPreset-PreconditionMAC.png)|Si le CPE possède une adresse MAC =, ≠, <, >, ≤ ou ≥ à celle renseignée.|
|![Capture d'écran du champ "IP"](/Images/GenieACS-NewPreset-PreconditionIP.png)|Si le CPE possède une adresse IP =, ≠, <, >, ≤ ou ≥ à celle renseignée.|
|![Capture d'écran du champ "WLAN SSID"](/Images/GenieACS-NewPreset-PreconditionWLANSSID.png)|Si le CPE utilise un SSID =, ≠, <, >, ≤ ou ≥ à celui renseigné.|
|![Capture d'écran du champ "WLAN passphrase"](/Images/GenieACS-NewPreset-PreconditionWLANPassphrase.png)|Si le CPE utilise un mot de passe de connexion à son réseau WiFi =, ≠, <, >, ≤ ou ≥ à celui renseigné.|

<br />

`Configurations` : Correspond aux actions à effectuer.
<br /><br />
Les configurations possibles sont les suivantes :

![Capture d'écran des configurations possibles lors de la création d'un nouveau préréglage](/Images/GenieACS-NewPreset-AllConfigurations.png)

<br /><br />
Quelques explications sur les paramètres de configurations proposés par GenieACS :

|**Configuration**|**Description**|
|---|---|
|![Capture d'écran du champ "Provision"](/Images/GenieACS-NewPreset-ConfigurationProvisionName.png)|Provision : Permet d’exécuter un script de provision.|
|![Capture d'écran du champ "Set"](/Images/GenieACS-NewPreset-ConfigurationSet.png)|Set : Permet de définir la valeur d’un paramètre issu du modèle de données TR-069.<br /><br />Le paramètre est renseigné dans le premier champ, et sa valeur dans le second.<br /><br />Pour plus d’informations, voir [le référentiel des paramètres TR-069 de l’Innbox V45](/innbox_v45.md).|
|![Capture d'écran du champ "Refresh"](/Images/GenieACS-NewPreset-ConfigurationRefresh.png)|Refresh : Permet de définir l’intervalle de rafraîchissement d’une information précise auprès du CPE.<br /><br />L’information concernée est renseignée dans le premier champ, et l’intervalle (en secondes) dans le second champ. |
|![Capture d'écran du champ "Add tag"](/Images/GenieACS-NewPreset-ConfigurationAddTag.png)|Add tag : Permet d’ajouter un tag au CPE.<br /><br />Le tag à ajouter est renseigné dans le seul champ disponible.|
|![Capture d'écran du champ "Remove tag"](/Images/GenieACS-NewPreset-ConfigurationRemoveTag.png)|Remove tag : Permet de supprimer un tag du CPE.<br /><br />Le tag à supprimer est renseigné dans le seul champ disponible.|
|![Capture d'écran du champ "Add object"](/Images/GenieACS-NewPreset-ConfigurationAddObject.png)|Add object : Permet d’ajouter un objet.|
|![Capture d'écran du champ "Remove object"](/Images/GenieACS-NewPreset-ConfigurationRemoveObject.png)|Remove object : Permet de supprimer un objet.|
|![Capture d'écran du champ "Command value"](/Images/GenieACS-NewPreset-ConfigurationCommand.png)|Command value : Permet de faire appel à une commande avec une certaine valeur.<br /><br />La commande est renseignée dans le premier champ, et la valeur dans le second.|
|![Capture d'écran du champ "Command age"](/Images/GenieACS-NewPreset-ConfigurationExecute.png)|Command age : Permet de définir l’intervalle d’exécution d’une commande.<br /><br />La commande est renseignée dans le premier champ, et l’intervalle d'exécution dans la seconde.|
|![Capture d'écran du champ "Software version"](/Images/GenieACS-NewPreset-ConfigurationSoftwareVersion.png)|Software version : Permet de définir la version logicielle.<br /><br />La version logicielle est renseignée dans le seul champ disponible.|
