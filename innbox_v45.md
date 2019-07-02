# Référentiel des paramètres TR-069 de l’Innbox V45
Le modèle Innbox V45 d'Iskratel peut être configuré via un serveur ACS grâce au protocole TR-069. Il existe donc différents paramètres auxquels on peut attribuer différentes valeurs en fonction de nos besoins.

> Tous les *`{i}`* sont à remplacer par un nombre, en fonction du paramètre concerné. <br /> <br />
> *Exemple : Si on veut modifier un paramètre de l'interface PPP N°2, il faudra spécifier le numéro de l'interface juste avant le `.WANPPPConnection` comme ci-dessous :* <br />
> *<pre><code>InternetGatewayDevice.WANDevice.1.WANConnectionDevice.<b>2.WANPPPConnection</b></code></pre>*
# Sommaire
> *A ajouter à la fin*

## WiFi
#### SSID du réseau WiFi :

    InternetGatewayDevice.LANDevice.1.WLANConfiguration.{i}.SSID
> Valeur possible :<br />
>  *Chaîne de caractères* 

<br />

#### Méthode de cryptage du mot de passe du WiFi :

    InternetGatewayDevice.LANDevice.1.WLANConfiguration.{i}.BeaconType
>  Valeurs possibles :<br />
>   `Basic` : Pas de cryptage<br />
>   `11i` : Correspond au WPA2-PSK<br />
>   `WPA` : Correspond au WPA-PSK<br />
>   `WPAand11i` : Correspond au WPA/WPA2-PSK mixed<br />

<br />

#### Mot de passe du WiFi :

    InternetGatewayDevice.LANDevice.1.WLANConfiguration.{i}.PreSharedKey.{i}.KeyPassphrase
> Valeur possible :<br />
> *`Chaîne de caractères`*  

<br />

#### Adresse IP de l'Innbox V45 :

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.IPInterface.{i}.IPInterfaceIPAddress
> Valeur possible :<br />
> *`Adresse IP`*  

<br />

## DHCP
#### Définir si l’Innerbox V45 utilisera le DHCP ou non pour l'adressage du réseau local :

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.DHCPServerEnable

> Valeurs possibles :<br />
> `true` : DHCP activé<br />
> `false` : DHCP désactivé  

<br />

#### Définir l’adresse IP la plus basse de celles distribuées par le serveur DHCP dans le réseau local :

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.MinAddress
> Valeur possible :<br />
> *`Adresse IP`*  

<br />


#### Définir l’adresse IP la plus haute de celles distribuées par le serveur DHCP dans le réseau local :

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.MaxAddress
> Valeur possible :<br />
> *`Adresse IP`*  

<br />

#### Réserver des adresses IP :

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.ReservedAddresses
> Valeur possible :<br />
> *`Liste d'adresses IP (maximum 256, séparés par une virgule)`*

<br />

#### Masque de sous-réseau :

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.SubnetMask
> Valeur possible :<br />
> *`Masque de sous-réseau`*

<br />

#### Passerelle par défaut (gateway) :

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.IPRouters
> Valeur possible :<br />
> *`Liste d'adresses IP (séparés par une virgule)`*

<br />

#### DNS (Domain Name System) :

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.DNSServers
> Valeur possible :<br />
> *`Liste d'adresses IP (maximum 32, séparés par une virgule)`*

<br />

#### Nom de domaine :

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.DomainName
> Valeur possible :<br />
> *`Chaîne de caractères`*

<br />

#### Durée des sessions (DHCP Lease Time) :

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.DHCPLeaseTime
> Valeur possible :<br />
> *`Durée (nombre, -1 équivaut à infini)`*

<br />

#### Adresses MAC autorisées via le WiFi :

    InternetGatewayDevice.LANDevice.1.WLANConfiguration.1.X_BROADCOM_COM_WlanAdapter.WlVirtIntfCfg.1.WlFltMacMode
> Valeurs possibles :<br />
> `allow` : Autoriser l'accès au réseau WiFi aux adresses MAC renseignées dans la liste<br />
> `deny` : Autoriser l'accès au réseau WiFi aux adresses MAC renseignées dans la liste

<br />

    InternetGatewayDevice.LANDevice.1.WLANConfiguration.1.X_BROADCOM_COM_WlanAdapter.WlVirtIntfCfg.1.WlMacFltCfg.11.WlMacAddr
> Valeur possible :<br />
> *`Adresse MAC`*

<br />

    InternetGatewayDevice.LANDevice.1.WLANConfiguration.1.X_BROADCOM_COM_WlanAdapter.WlVirtIntfCfg.1.WlMacFltCfg.11.WlIfcname
> Valeur possible :<br />
> *`Interface Linux (par défaut utiliser : wl0)`*

<br />

#### Adresses IP statiques (en fonction de l'adresse MAC) :

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.DHCPConditionalServingPool.{i}.Enable
> Valeurs possibles :<br />
> `TRUE` : Distribution de l'adresse IP à l'adresse MAC spécifiée active<br />
> `FALSE` : Distribution de l'adresse IP à l'adresse MAC spécifiée inactive

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.DHCPConditionalServingPool.{i}.Chaddr
> Valeur possible :<br />
> *`Adresse MAC concernée`*

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.DHCPConditionalServingPool.{i}.ReservedAddresses
> Valeur possible :<br />
> *`Adresse IP attribuée`*

<br />

## NAT
#### Port extérieur de début utilisé par la règle NAT (côté WAN) :

    InternetGatewayDevice.WANDevice.{i}.WANConnectionDevice.{i}.WANPPPConnection.{i}.PortMapping.ExternalPort
> Valeur possible :<br />
> *`Port (nombre)`*  

<br />

#### Port extérieur de fin utilisé par la règle NAT (côté WAN) :

    InternetGatewayDevice.WANDevice.{i}.WANConnectionDevice.{i}.WANPPPConnection.{i}.PortMapping.X_BROADCOM_COM_ExternalPortEnd
> Valeur possible :<br />
> *`Port (nombre)`*  

<br />

#### Adresse IP (côté LAN) vers laquelle rediriger les requêtes :

    InternetGatewayDevice.WANDevice.{i}.WANConnectionDevice.{i}.WANPPPConnection.{i}.PortMapping.InternalClient
> Valeur possible :<br />
> *`Adresse IP`*  

<br />

#### Port intérieur de début utilisé par la règle NAT (côté LAN) :

    InternetGatewayDevice.WANDevice.{i}.WANConnectionDevice.{i}.WANPPPConnection.{i}.PortMapping.InternalPort

> Valeur possible :<br />
> *`Port (nombre)`*  

<br />

#### Port intérieur de fin utilisé par la règle NAT (côté LAN) :

    InternetGatewayDevice.WANDevice.{i}.WANConnectionDevice.{i}.WANPPPConnection.{i}.PortMapping.X_BROADCOM_COM_InternalPortEnd

> Valeur possible :<br />
> *`Port (nombre)`*  

<br />

#### Nom de la règle NAT :

    InternetGatewayDevice.WANDevice.{i}.WANConnectionDevice.{i}.WANPPPConnection.{i}.PortMapping.PortMappingDescription
> Valeur possible :<br />
> *`Chaîne de caractères`*  

<br />

#### Définir si la règle NAT est activée ou non :

    InternetGatewayDevice.WANDevice.{i}.WANConnectionDevice.{i}.WANPPPConnection.{i}.PortMapping.PortMappingEnabled
> Valeurs possibles :<br />
> `true` : NAT activé<br />
> `false` : NAT désactivé  

<br />

#### Durée de la règle NAT :

    InternetGatewayDevice.WANDevice.{i}.WANConnectionDevice.{i}.WANPPPConnection.{i}.PortMapping.PortMappingLeaseDuration
> Valeurs possibles :<br />
> *`Durée (nombre)`*<br />
> `0` : Infini  

<br />

#### Protocole utilisé par la règle NAT :

    InternetGatewayDevice.WANDevice.{i}.WANConnectionDevice.{i}.WANPPPConnection.{i}.PortMapping.PortMappingProtocol
> Valeurs possibles :<br />
> `TCP` : Protocole TCP<br />
> `UDP` : Protocole UDP  
> `TCP&#32;or&#32;UDP` : Protocole TCP/UDP

<br />

#### Définir si la fonctionnalité de boucle NAT est activée ou non :

    InternetGatewayDevice.WANDevice.{i}.WANConnectionDevice.{i}.WANPPPConnection.{i}.PortMapping.LoopBack
> Valeurs possibles :<br />
> `true` : Boucle NAT activé<br />
> `false` : Boucle NAT désactivé  

<br />

## DMZ
#### Adresse IP qui fera parti de la DMZ (demilitarized zone) :

    InternetGatewayDevice.X_BROADCOM_COM_SecDmzHostCfg.IPAddress
> Valeur possible :<br />
> *`Adresse IP`*  

<br />

## PPPoE
#### Définir la connexion en IP_Routed :

    InternetGatewayDevice.WANDevice.{i}.WANConnectionDevice.{i}.WANPPPConnection.{i}.ConnectionType
> Valeur possible :<br />
> `IP_Routed`  

<br />

#### Nom de la connexion :

    InternetGatewayDevice.WANDevice.{i}.WANConnectionDevice.{i}.WANPPPConnection.{i}.Name
> Valeur possible :<br />
> *`Chaîne de caractères`*  

<br />

#### Définir si le pare-feu (firewall) est activé ou non :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.X_BROADCOM_COM_FirewallEnabled
> Valeurs possibles :<br />
> `1` : Pare-feu (firewall) activé<br />
> `0` : Pare-feu (firewall) désactivé  

<br />

#### 	Définir si l'IGMP Multicast Proxy est activé ou non :

    InternetGatewayDevice.WANDevice.{i}.WANConnectionDevice.{i}.WANPPPConnection.{i}.X_BROADCOM_COM_IGMPEnabled
> Valeurs possibles :<br />
> `true` : IGMP Multicast Proxy activé<br />
> `false` : IGMP Multicast Proxy désactivé

<br />

#### 	Définir si l'IGMP Multicast Source est activé ou non :

    InternetGatewayDevice.WANDevice.{i}.WANConnectionDevice.{i}.WANPPPConnection.{i}.X_BROADCOM_COM_IGMPEnabled
> Valeurs possibles :<br />
> `true` : IGMP Multicast Source activé<br />
> `false` : IGMP Multicast Source désactivé

<br />

#### 	Définir si le PPP Debug Mode est activé ou non :

    InternetGatewayDevice.WANDevice.{i}.WANConnectionDevice.{i}.WANPPPConnection.{i}.X_BROADCOM_COM_Enable_Debug
> Valeurs possibles :<br />
> `true` : PPP Debug Mode activé<br />
> `false` : PPP Debug Mode désactivé

<br />

#### 	Définir si le DNS est activé ou non :

    InternetGatewayDevice.WANDevice.{i}.WANConnectionDevice.{i}.WANPPPConnection.{i}.X_BROADCOM_COM_Enable_Debug
> Valeurs possibles :<br />
> `true` : PPP Debug Mode activé<br />
> `false` : PPP Debug Mode désactivé

<br />

#### Quality of Service (QoS) :

    InternetGatewayDevice.WANDevice.{i}.WANConnectionDevice.{i}.WANPPPConnection.{i}.X_BROADCOM_COM_VlanMux8021p
> Valeur possible :<br />
> *`Nombre`*  

<br />

#### ID VLAN :

    InternetGatewayDevice.WANDevice.{i}.WANConnectionDevice.{i}.WANPPPConnection.{i}.X_BROADCOM_COM_VlanMuxID
> Valeur possible :<br />
> *`ID VLAN (nombre)`*  

<br />

#### VLAN Tag Protocol IDentifier (TPID) :

    InternetGatewayDevice.WANDevice.{i}.WANConnectionDevice.{i}.WANPPPConnection.{i}.X_BROADCOM_COM_VlanTpid
> Valeur possible :<br />
> *`VLAN TPID (nombre)`*  

<br />

#### Interface Linux :

    InternetGatewayDevice.WANDevice.{i}.WANConnectionDevice.{i}.WANPPPConnection.{i}.X_BROADCOM_COM_IfName
> Valeur possible :<br />
> *`Chaîne de caractères`*  

<br />

#### Maximum Transmission Unit (MTU, taille maximale des paquets pouvant être transmis) :

    InternetGatewayDevice.WANDevice.{i}.WANConnectionDevice.{i}.WANPPPConnection.{i}.MTU
> Valeur possible :<br />
> *`Nombre`*  

<br />

#### Définir si la fonctionnalité NAT est activée ou non :

    InternetGatewayDevice.WANDevice.{i}.WANConnectionDevice.{i}.WANPPPConnection.{i}.NATEnabled
> Valeurs possibles :<br />
> `true` : Fonctionnalité NAT activée<br />
> `false` : Fonctionnalité NAT désactivée  

<br />

#### Nom d'utilisateur pour la connexion PPPoE :

    InternetGatewayDevice.WANDevice.{i}.WANConnectionDevice.{i}.WANPPPConnection.{i}.Username
> Valeur possible :<br />
> *`Chaîne de caractères`*  

<br />

#### Mot de passe pour la connexion PPPoE :

    InternetGatewayDevice.WANDevice.{i}.WANConnectionDevice.{i}.WANPPPConnection.{i}.Password
> Valeur possible :<br />
> *`Chaîne de caractères`*  

<br />

#### Définir si la connexion PPPoE est activée ou non :

    InternetGatewayDevice.WANDevice.{i}.WANConnectionDevice.{i}.WANPPPConnection.{i}.Enable
> Valeurs possibles :<br />
> `true` : Connexion PPPoE activée<br />
> `false` : Connexion PPPoE désactivée  

<br />

#### Passerelle secondaire du CPE (interface Linux) :

    InternetGatewayDevice.Layer3Forwarding.X_BROADCOM_COM_DefaultConnectionServices
> Valeur possible :<br />
> *`Interface Linux (Chaîne de caractères)`*  

<br />

#### Définir la connexion PPPoE comme serveur DNS secondaire :

    InternetGatewayDevice.X_BROADCOM_COM_NetworkConfig.DNSIfName
> Valeur possible :<br />
> *`Liste de nom d'interface Linux (Chaînes de caractères, séparés par une virgule)`*  

<br />

## Pare-feu (firewall) | ⚠️ NON VÉRIFIÉ ⚠️
#### Adresse IP de destination :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.1.X_BROADCOM_COM_FirewallException.DestinationIPAddress
> Valeur possible :<br />
> *`Adresse IP`*  

<br />

#### Masque de sous-réseau de l’adresse IP de destination :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.1.X_BROADCOM_COM_FirewallException.DestinationNetMask
> Valeur possible :<br />
> *`Masque de sous-réseau (nombre de bits, ex : 24)`*  

<br />

#### Port de début du destinataire :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.1.X_BROADCOM_COM_FirewallException.DestinationPortStart
> Valeur possible :<br />
> *`Port (nombre)`*  

<br />

#### Port de fin du destinataire :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.1.X_BROADCOM_COM_FirewallException.DestinationPortEnd
> Valeur possible :<br />
> *`Port (nombre)`*  

<br />

#### Adresse IP source :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.1.X_BROADCOM_COM_FirewallException.SourceIPAddress
> Valeur possible :<br />
> *`Adresse IP`*  

<br />

#### Masque de sous-réseau de l’adresse IP source :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.1.X_BROADCOM_COM_FirewallException.SourceNetMask
> Valeur possible :<br />
> *`Masque de sous-réseau (nombre de bits, ex : 24)`*  

<br />

#### Port de début de la source :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.1.X_BROADCOM_COM_FirewallException.SourcePortStart
> Valeur possible :<br />
> *`Port (nombre)`*  

<br />

#### Port de fin de la source :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.1.X_BROADCOM_COM_FirewallException.SourcePortEnd
> Valeur possible :<br />
> *`Port (nombre)`*  

<br />

#### Version d’adresse IP :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.1.X_BROADCOM_COM_FirewallException.IPVersion
> Valeur possible :<br />
> *`Version d'adresse IP (nombre, ex : 4 pour IPv4)`*  

<br />

#### Protocole de communication :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.1.X_BROADCOM_COM_FirewallException.Protocol
> Valeurs possibles :<br />
> `TCP` : Protocole TCP<br />
> `UDP` : Protocole UDP  

<br />

#### Nom de la règle :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.1.X_BROADCOM_COM_FirewallException.FilterName
> Valeur possible :<br />
> *`Chaîne de caractères`*  

<br />

#### Définir si la règle de pare-feu est activée ou non :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.1.X_BROADCOM_COM_FirewallException.Enable
> Valeurs possibles :<br />
> `true` : Règle de pare-feu activée<br />
> `false` : Règle de pare-feu désactivée  

<br />

## VoIP (SIP)

#### Interface Linux utilisée par l'application VoIP :

    InternetGatewayDevice.Services.VoiceService.{i}.X_BROADCOM_COM_BoundIfName
> Valeur possible :<br />
> *`Interface Linux (Chaîne de caractères)`*  

<br />

#### Nombre d'entrée(s) :

    InternetGatewayDevice.Services.VoiceService.{i}.VoiceProfileNumberOfEntries
> Valeur possible :<br />
> *`Nombre`*  

<br />

#### Nombre de session(s) maximal :

    InternetGatewayDevice.Services.VoiceService.{i}.VoiceProfile.{i}.MaxSessions
> Valeur possible :<br />
> *`Nombre`*  

<br />

#### Définir si l'application VoIP est activée ou non :

    InternetGatewayDevice.Services.VoiceService.{i}.VoiceProfile.{i}.Enable
> Valeur possible :<br />
> `Enabled` : Application VoIP activée  

<br />

#### Région de l'application VoIP :

    InternetGatewayDevice.Services.VoiceService.{i}.VoiceProfile.{i}.Region
> Valeur possible :<br />
> *`Code pays (voir tables des codes de pays selon l'ISO 3166)`*

<br />

#### Adresse IP du serveur proxy VoIP :

    InternetGatewayDevice.Services.VoiceService.{i}.SIP.ProxyServer
> Valeur possible :<br />
> *`Adresse IP`*  

<br />

#### Port du serveur proxy VoIP :

    InternetGatewayDevice.Services.VoiceService.{i}.SIP.ProxyServerPort
> Valeur possible :<br />
> *`Port (nombre)`*  

<br />

#### Nom de domaine SIP :

    InternetGatewayDevice.Services.VoiceService.{i}.SIP.UserAgentDomain
> Valeur possible :<br />
> *`Chaîne de caractères`*  

<br />

#### Adresse IP du serveur proxy VoIP sortant :

    InternetGatewayDevice.Services.VoiceService.{i}.SIP.OutboundProxy
> Valeur possible :<br />
> *`Adresse IP`*  

<br />

#### Port du serveur proxy VoIP sortant :

    InternetGatewayDevice.Services.VoiceService.{i}.SIP.OutboundProxyPort
> Valeur possible :<br />
> *`Port (nombre)`*  

<br />

#### Adresse IP du serveur Registrar :

    InternetGatewayDevice.Services.VoiceService.{i}.SIP.RegistrarServer
> Valeur possible :<br />
> *`Adresse IP`*  

<br />

#### Port du serveur Registrar :

    InternetGatewayDevice.Services.VoiceService.{i}.SIP.RegistrarServerPort
> Valeur possible :<br />
> *`Port (nombre)`*  

<br />

#### Définir si un compte SIP est activé ou non :

    InternetGatewayDevice.Services.VoiceService.{i}.Line.{i}.Enable
> Valeur possible :<br />
> `Enabled` : Premier compte SIP activé  

<br />

#### Terminaux physiques assignés :

    InternetGatewayDevice.Services.VoiceService.{i}.Line.{i}.PhyReferenceList
> Valeur possible :<br />
> *`Liste de ports FXS (numéros, séparés par une virgule)`*

<br />

#### Directory Number (extension) d'un compte SIP :

    InternetGatewayDevice.Services.VoiceService.{i}.Line.{i}.DirectoryNumber
> Valeur possible :<br />
> *`Port FXS (nombre)`*  

<br />

#### Uniform Ressource Identifier (URI) d'un compte SIP :

    InternetGatewayDevice.Services.VoiceService.{i}.Line.{i}.SIP.URI
> Valeur possible :<br />
> *`Port FXS (nombre)`*  

<br />

#### Nombre de sessions SIP maximales :

    InternetGatewayDevice.Services.VoiceService.{i}.Line.{i}.CallingFeatures.MaxSessions
> Valeur possible :<br />
> *`Nombre`*

<br />

#### Nom d'utilisateur d'authentification d'un compte SIP :

    InternetGatewayDevice.Services.VoiceService.1.VoiceProfile.1.Line.1.SIP.AuthUserName
> Valeur possible :<br />
> *`Port FXS (nombre)`*  

<br />

#### Mot de passe d'authentification d'un compte SIP :

    InternetGatewayDevice.Services.VoiceService.1.VoiceProfile.1.Line.1.SIP.AuthPassword
> Valeur possible :<br />
> *`Port FXS (nombre)`*  

<br />

#### Caller Line IDentification (CLID) du compte SIP 1 :

    InternetGatewayDevice.Services.VoiceService.1.VoiceProfile.1.Line.1.CallingFeatures.CallerIDName
> Valeur possible :<br />
> *`Port FXS (nombre)`*  

<br />

#### DigitMap du service SIP :

    InternetGatewayDevice.Services.VoiceService.{i}.VoiceProfile.{i}.DigitMap
> Valeur possible :<br />
> *`DigitMap (format : xxxxxxx)`*  

<br />

#### Confirmer ou non la modification des paramètres en supprimant les anciennes valeurs :

    InternetGatewayDevice.Services.VoiceService.1.VoiceProfile.1.Reset
> Valeurs possibles :<br />
> `true` : Modifications validées et suppression de l'ancienne configuration<br />
> `false` : Modifications annulées et maintient de l'ancienne configuration
