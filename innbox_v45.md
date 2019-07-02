# Référentiel des paramètres TR-069 de l’Innbox V45
Le modèle Innbox V45 d'Iskratel peut être configuré via un serveur ACS grâce au protocole TR-069. Il existe donc différents paramètres auxquels on peut attribuer différentes valeurs en fonction de nos besoins.

> Tous les *`{i}`* sont à remplacer par un nombre, en fonction du paramètre concerné.

- [WiFi](#wifi)
  - [SSID du réseau WiFi ](#ssid-du-r%C3%A9seau-wifi-)
  - [Méthode de cryptage du mot de passe du WiFi ](#m%C3%A9thode-de-cryptage-du-mot-de-passe-du-wifi-)
  - [Mot de passe du WiFi ](#mot-de-passe-du-wifi-)
  - [Adresse IP de l'Innbox V45 ](#adresse-ip-de-linnbox-v45-)
- [DHCP](#dhcp)
  - [Définir si l’Innerbox V45 utilisera le DHCP ou non pour l'adressage du réseau local ](#définir-si-linnerbox-v45-utilisera-le-dhcp-ou-non-pour-ladressage-du-réseau-local-)
  - [Définir l’adresse IP la plus basse de celles distribuées par le serveur DHCP dans le réseau local ](#définir-ladresse-ip-la-plus-basse-de-celles-distribuées-par-le-serveur-dhcp-dans-le-réseau-local-)
  - [Définir l’adresse IP la plus haute de celles distribuées par le serveur DHCP dans le réseau local ](#définir-ladresse-ip-la-plus-haute-de-celles-distribuées-par-le-serveur-dhcp-dans-le-réseau-local-)
  - [Réserver des adresses IP ](#r%C3%A9server-des-adresses-ip-)
  - [Masque de sous-réseau ](#masque-de-sous-r%C3%A9seau-)
  - [Passerelle par défaut \(gateway\) ](#passerelle-par-d%C3%A9faut-gateway-)
  - [DNS \(Domain Name System\) ](#dns-domain-name-system-)
  - [Nom de domaine ](#nom-de-domaine-)
  - [Durée des sessions \(DHCP Lease Time\) ](#dur%C3%A9e-des-sessions-dhcp-lease-time-)
  - [Adresses MAC autorisées  | ⚠️ NON VÉRIFIÉ ⚠️](#adresses-mac-autorisées---️-non-vérifié-️)
  - [Adresses IP statiques  | ⚠️ NON VÉRIFIÉ ⚠️](#adresses-ip-statiques---️-non-vérifié-️)
  - [Nombre d'adresses IP statiques dans la plage d'adresses IP distribuées  | ⚠️ NON VÉRIFIÉ ⚠️](#nombre-dadresses-ip-statiques-dans-la-plage-dadresses-ip-distribuées---️-non-vérifié-️)
- [NAT | ⚠️ NON VÉRIFIÉ ⚠️](#nat--️-non-vérifié-️)
  - [Port extérieur utilisé par la règle NAT \(côté WAN\) ](#port-ext%C3%A9rieur-utilis%C3%A9-par-la-r%C3%A8gle-nat-c%C3%B4t%C3%A9-wan-)
  - [Adresse IP \(côté LAN\) vers laquelle rediriger les requêtes ](#adresse-ip-c%C3%B4t%C3%A9-lan-vers-laquelle-rediriger-les-requ%C3%AAtes-)
  - [Port intérieur utilisé par la règle NAT \(côté LAN\) ](#port-int%C3%A9rieur-utilis%C3%A9-par-la-r%C3%A8gle-nat-c%C3%B4t%C3%A9-lan-)
  - [Nom de la règle NAT ](#nom-de-la-r%C3%A8gle-nat-)
  - [Définir si la règle NAT est activée ou non ](#d%C3%A9finir-si-la-r%C3%A8gle-nat-est-activ%C3%A9e-ou-non-)
  - [Durée de la règle NAT ](#dur%C3%A9e-de-la-r%C3%A8gle-nat-)
  - [Protocole utilisé par la règle NAT ](#protocole-utilis%C3%A9-par-la-r%C3%A8gle-nat-)
  - [Définir si la fonctionnalité de boucle NAT est activée ou non ](#d%C3%A9finir-si-la-fonctionnalit%C3%A9-de-boucle-nat-est-activ%C3%A9e-ou-non-)
  - [Ajouter une nouvelle règle NAT ](#ajouter-une-nouvelle-r%C3%A8gle-nat-)
- [DMZ](#dmz)
  - [Adresse IP qui fera parti de la DMZ \(demilitarized zone\) ](#adresse-ip-qui-fera-parti-de-la-dmz-demilitarized-zone-)
- [PPPoE](#pppoe)
  - [Définir la connexion en IP_Routed ](#d%C3%A9finir-la-connexion-en-ip_routed-)
  - [Nom de la connexion ](#nom-de-la-connexion-)
  - [Définir si le pare-feu \(firewall\) est activé ou non ](#d%C3%A9finir-si-le-pare-feu-firewall-est-activ%C3%A9-ou-non-)
  - [Définir si l'IGMP Multicast Proxy est activé ou non ](#d%C3%A9finir-si-ligmp-multicast-proxy-est-activ%C3%A9-ou-non-)
  - [Définir si l'IGMP Multicast Source est activé ou non ](#d%C3%A9finir-si-ligmp-multicast-source-est-activ%C3%A9-ou-non-)
  - [Définir si le PPP Debug Mode est activé ou non ](#d%C3%A9finir-si-le-ppp-debug-mode-est-activ%C3%A9-ou-non-)
  - [Définir si le DNS est activé ou non ](#d%C3%A9finir-si-le-dns-est-activ%C3%A9-ou-non-)
  - [Quality of Service \(QoS\) ](#quality-of-service-qos-)
  - [ID VLAN ](#id-vlan-)
  - [VLAN Tag Protocol IDentifier \(TPID\) ](#vlan-tag-protocol-identifier-tpid-)
  - [Interface Linux ](#interface-linux-)
  - [Maximum Transmission Unit \(MTU, taille maximale des paquets pouvant être transmis\) ](#maximum-transmission-unit-mtu-taille-maximale-des-paquets-pouvant-%C3%AAtre-transmis-)
  - [Définir si la fonctionnalité NAT est activée ou non ](#d%C3%A9finir-si-la-fonctionnalit%C3%A9-nat-est-activ%C3%A9e-ou-non-)
  - [Nom d'utilisateur pour la connexion PPPoE ](#nom-dutilisateur-pour-la-connexion-pppoe-)
  - [Mot de passe pour la connexion PPPoE ](#mot-de-passe-pour-la-connexion-pppoe-)
  - [Définir si la connexion PPPoE est activée ou non ](#d%C3%A9finir-si-la-connexion-pppoe-est-activ%C3%A9e-ou-non-)
  - [Passerelle secondaire du CPE \(interface Linux\) ](#passerelle-secondaire-du-cpe-interface-linux-)
  - [Définir la connexion PPPoE comme serveur DNS secondaire ](#d%C3%A9finir-la-connexion-pppoe-comme-serveur-dns-secondaire-)
- [Pare-feu \(firewall\) | ⚠️ NON VÉRIFIÉ ⚠️](#pare-feu-firewall--️-non-vérifié-️)
  - [Adresse IP de destination ](#adresse-ip-de-destination-)
  - [Masque de sous-réseau de l’adresse IP de destination ](#masque-de-sous-réseau-de-ladresse-ip-de-destination-)
  - [Port de début du destinataire ](#port-de-d%C3%A9but-du-destinataire-)
  - [Port de fin du destinataire ](#port-de-fin-du-destinataire-)
  - [Adresse IP source ](#adresse-ip-source-)
  - [Masque de sous-réseau de l’adresse IP source ](#masque-de-sous-réseau-de-ladresse-ip-source-)
  - [Port de début de la source ](#port-de-d%C3%A9but-de-la-source-)
  - [Port de fin de la source ](#port-de-fin-de-la-source-)
  - [Version d’adresse IP ](#version-dadresse-ip-)
  - [Protocole de communication ](#protocole-de-communication-)
  - [Nom de la règle ](#nom-de-la-r%C3%A8gle-)
  - [Définir si la règle de pare-feu est activée ou non ](#d%C3%A9finir-si-la-r%C3%A8gle-de-pare-feu-est-activ%C3%A9e-ou-non-)
- [VoIP \(SIP\)](#voip-sip)
  - [Interface Linux utilisée par l'application VoIP ](#interface-linux-utilis%C3%A9e-par-lapplication-voip-)
  - [Nombre d'entrée\(s\) ](#nombre-dentr%C3%A9es-)
  - [Nombre de session\(s\) maximal ](#nombre-de-sessions-maximal-)
  - [Définir si l'application VoIP est activée ou non ](#d%C3%A9finir-si-lapplication-voip-est-activ%C3%A9e-ou-non-)
  - [Région de l'application VoIP ](#r%C3%A9gion-de-lapplication-voip-)
  - [Adresse IP du serveur proxy VoIP ](#adresse-ip-du-serveur-proxy-voip-)
  - [Port du serveur proxy VoIP ](#port-du-serveur-proxy-voip-)
  - [Nom de domaine SIP ](#nom-de-domaine-sip-)
  - [Adresse IP du serveur proxy VoIP sortant ](#adresse-ip-du-serveur-proxy-voip-sortant-)
  - [Port du serveur proxy VoIP sortant ](#port-du-serveur-proxy-voip-sortant-)
  - [Adresse IP du serveur Registrar ](#adresse-ip-du-serveur-registrar-)
  - [Port du serveur Registrar ](#port-du-serveur-registrar-)
  - [Définir si un compte SIP est activé ou non ](#d%C3%A9finir-si-un-compte-sip-est-activ%C3%A9-ou-non-)
  - [Terminaux physiques assignés ](#terminaux-physiques-assign%C3%A9s-)
  - [Directory Number \(extension\) d'un compte SIP ](#directory-number-extension-dun-compte-sip-)
  - [Uniform Ressource Identifier \(URI\) d'un compte SIP ](#uniform-ressource-identifier-uri-dun-compte-sip-)
  - [Nombre de sessions SIP maximales ](#nombre-de-sessions-sip-maximales-)
  - [Nom d'utilisateur d'authentification d'un compte SIP ](#nom-dutilisateur-dauthentification-dun-compte-sip-)
  - [Mot de passe d'authentification d'un compte SIP ](#mot-de-passe-dauthentification-dun-compte-sip-)
  - [Caller Line IDentification \(CLID\) du compte SIP 1 ](#caller-line-identification-clid-du-compte-sip-1-)
  - [DigitMap du service SIP ](#digitmap-du-service-sip-)
  - [Confirmer ou non la modification des paramètres en supprimant les anciennes valeurs ](#confirmer-ou-non-la-modification-des-param%C3%A8tres-en-supprimant-les-anciennes-valeurs-)



## WiFi
#### SSID du réseau WiFi :

    InternetGatewayDevice.LANDevice.{i}.WLANConfiguration.{i}.SSID
> Valeur possible :<br />
>  *Chaîne de caractères* 

<br />

#### Méthode de cryptage du mot de passe du WiFi :

    InternetGatewayDevice.LANDevice.{i}.WLANConfiguration.{i}.BeaconType
>  Valeurs possibles :<br />
>   `Basic` : Pas de cryptage<br />
>   `11i` : Correspond au WPA2-PSK<br />
>   `WPA` : Correspond au WPA-PSK<br />
>   `WPAand11i` : Correspond au WPA/WPA2-PSK mixed<br />

<br />

#### Mot de passe du WiFi :

    InternetGatewayDevice.LANDevice.{i}.WLANConfiguration.{i}.PreSharedKey.{i}.KeyPassphrase
> Valeur possible :<br />
> *`Chaîne de caractères`*  

<br />

#### Adresse IP de l'Innbox V45 :

    InternetGatewayDevice.LANDevice.{i}.LANHostConfigManagement.IPInterface.{i}.IPInterfaceIPAddress
> Valeur possible :<br />
> *`Adresse IP`*  

<br />

## DHCP
#### Définir si l’Innerbox V45 utilisera le DHCP ou non pour l'adressage du réseau local :

    InternetGatewayDevice.LANDevice.{i}.LANHostConfigManagement.DHCPServerEnable

> Valeurs possibles :<br />
> `true` : DHCP activé<br />
> `false` : DHCP désactivé  

<br />

#### Définir l’adresse IP la plus basse de celles distribuées par le serveur DHCP dans le réseau local :

    InternetGatewayDevice.LANDevice.{i}.LANHostConfigManagement.MinAddress
> Valeur possible :<br />
> *`Adresse IP`*  

<br />


#### Définir l’adresse IP la plus haute de celles distribuées par le serveur DHCP dans le réseau local :

    InternetGatewayDevice.LANDevice.{i}.LANHostConfigManagement.MaxAddress
> Valeur possible :<br />
> *`Adresse IP`*  

<br />

#### Réserver des adresses IP :

    InternetGatewayDevice.LANDevice.{i}.LANHostConfigManagement.ReservedAddresses
> Valeur possible :<br />
> *`Liste d'adresses IP (maximum 256, séparés par une virgule)`*

<br />

#### Masque de sous-réseau :

    InternetGatewayDevice.LANDevice.{i}.LANHostConfigManagement.SubnetMask
> Valeur possible :<br />
> *`Masque de sous-réseau`*

<br />

#### Passerelle par défaut (gateway) :

    InternetGatewayDevice.LANDevice.{i}.LANHostConfigManagement.IPRouters
> Valeur possible :<br />
> *`Liste d'adresses IP (séparés par une virgule)`*

<br />

#### DNS (Domain Name System) :

    InternetGatewayDevice.LANDevice.{i}.LANHostConfigManagement.DNSServers
> Valeur possible :<br />
> *`Liste d'adresses IP (maximum 32, séparés par une virgule)`*

<br />

#### Nom de domaine :

    InternetGatewayDevice.LANDevice.{i}.LANHostConfigManagement.DomainName
> Valeur possible :<br />
> *`Chaîne de caractères`*

<br />

#### Durée des sessions (DHCP Lease Time) :

    InternetGatewayDevice.LANDevice.{i}.LANHostConfigManagement.DHCPLeaseTime
> Valeur possible :<br />
> *`Durée (nombre, -1 équivaut à infini)`*

<br />

#### Adresses MAC autorisées : | ⚠️ NON VÉRIFIÉ ⚠️

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.AllowedMACAddresses
> Valeur possible :<br />
> *`Liste d'adresses MAC (séparés par une virgule)`*

<br />

#### Adresses IP statiques : | ⚠️ NON VÉRIFIÉ ⚠️
**Attention : Le `{i}` est à remplacer par le numéro de la règle que vous souhaitez créer ou modifier.**

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.DHCPStaticAddress.{i}.Enable
> Valeurs possibles :<br />
> `true` : Distribution de l'adresse IP en fonction de l'adresse MAC activée<br />
> `false` : Distribution de l'adresse IP en fonction de l'adresse MAC désactivée

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.DHCPStaticAddress.{i}.Alias
> Valeur possible :<br />
> *`Alias (Chaîne de caractères)`*

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.DHCPStaticAddress.{i}.Chaddr
> Valeur possible :<br />
> *`Adresse MAC concernée`*

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.DHCPStaticAddress.{i}.Yiaddr
> Valeur possible :<br />
> *`Adresse IP attribuée`*

<br />

#### Nombre d'adresses IP statiques dans la plage d'adresses IP distribuées : | ⚠️ NON VÉRIFIÉ ⚠️

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.DHCPStaticAddressNumberOfEntries
> Valeur possible :<br />
> *`Nombre`*

<br />

## NAT | ⚠️ NON VÉRIFIÉ ⚠️
#### Port extérieur utilisé par la règle NAT (côté WAN) :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.1.PortMapping.ExternalPort
> Valeur possible :<br />
> *`Port (nombre)`*  

<br />

#### Adresse IP (côté LAN) vers laquelle rediriger les requêtes :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.1.PortMapping.InternalClient
> Valeur possible :<br />
> *`Adresse IP`*  

<br />

#### Port intérieur utilisé par la règle NAT (côté LAN) :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.1.PortMapping.InternalPort

> Valeur possible :<br />
> *`Port (nombre)`*  

<br />

#### Nom de la règle NAT :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.1.PortMapping.PortMappingDescription
> Valeur possible :<br />
> *`Chaîne de caractères`*  

<br />

#### Définir si la règle NAT est activée ou non :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.1.PortMapping.PortMappingEnabled
> Valeurs possibles :<br />
> `true` : NAT activé<br />
> `false` : NAT désactivé  

<br />

#### Durée de la règle NAT :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.1.PortMapping.PortMappingLeaseDuration
> Valeurs possibles :<br />
> *`Durée (nombre)`*<br />
> `0` : Infini  

<br />

#### Protocole utilisé par la règle NAT :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.1.PortMapping.PortMappingProtocol
> Valeurs possibles :<br />
> `TCP` : Protocole TCP<br />
> `UDP` : Protocole UDP  

<br />

#### Définir si la fonctionnalité de boucle NAT est activée ou non :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.1.PortMapping.LoopBack
> Valeurs possibles :<br />
> `true` : Boucle NAT activé<br />
> `false` : Boucle NAT désactivé  

<br />

#### Ajouter une nouvelle règle NAT :
<pre><code>InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.<b>X</b>.<b>PARAMETRE</b></code></pre>
> Remplacer le **X**  par le numéro de la nouvelle règle NAT et **PARAMETRE** par le paramètre concerné.<br />
> *Exemple : Ajouter le nom de la deuxième règle NAT*
*`InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.2.PortMapping.PortMappingDescription`*  

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
