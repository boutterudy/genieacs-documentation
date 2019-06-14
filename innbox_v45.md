# Référentiel des paramètres TR-069 de l’Innbox V45
Le modèle Innbox V45 d'Iskratel peut être configuré via un serveur ACS grâce au protocole TR-069. Il existe donc différents paramètres auxquels on peut attribuer différentes valeurs en fonction de nos besoins.

## Sommaire
  1. [WiFi](#wifi)
      - [SSID du réseau WiFi](#ssid-du-réseau-wifi-)
      - [Méthode de cryptage du mot de passe du WiFi](#méthode-de-cryptage-du-mot-de-passe-du-wifi-)
      - [Mot de passe du WiFi](#mot-de-passe-du-wifi-)
      - [Adresse IP de l'Innbox V45](#adresse-ip-de-linnbox-v45-)
  2. [DHCP](#dhcp)
      - [Définir si l’Innerbox V45 utilisera le DHCP ou non pour l'adressage du réseau local](#définir-si-linnerbox-v45-utilisera-le-dhcp-ou-non-pour-ladressage-du-réseau-local-)
      - [Définir l’adresse IP la plus basse de celles distribuées par le serveur DHCP dans le réseau local](#définir-ladresse-ip-la-plus-basse-de-celles-distribuées-par-le-serveur-dhcp-dans-le-réseau-local-)
      - [Définir l’adresse IP la plus haute de celles distribuées par le serveur DHCP dans le réseau local](#définir-ladresse-ip-la-plus-haute-de-celles-distribuées-par-le-serveur-dhcp-dans-le-réseau-local-)
      - [Réserver des adresses IP](#réserver-des-adresses-ip-)
      - [Masque de sous-réseau](#masque-de-sous-réseau-)
      - [Passerelle par défaut (gateway)](#passerelle-par-défaut-gateway-)
      - [DNS (Domain Name System)](#dns-domain-name-system-)
      - [Nom de domaine](#nom-de-domaine-)
      - [Durée des sessions (DHCP Lease Time)](#durée-des-sessions-dhcp-lease-time-)
      - [Adresses MAC autorisées](#adresses-mac-autorisées-)
      - [Adresses IP statiques](#adresses-ip-statiques-)
      - [Nombre d'adresses IP statiques dans la plage d'adresses IP distribuées](#nombre-dadresses-ip-statiques-dans-la-plage-dadresses-ip-distribuées-)
  3. [NAT](#nat)
      - [Port extérieur utilisé par la règle NAT (côté WAN)](#port-extérieur-utilisé-par-la-règle-nat-côté-wan-)
      - [Adresse IP (côté LAN) vers laquelle rediriger les requêtes](#adresse-ip-côté-lan-vers-laquelle-rediriger-les-requêtes-)
      - [Port intérieur utilisé par la règle NAT (côté LAN)](#port-intérieur-utilisé-par-la-règle-nat-côté-lan-)
      - [Nom de la règle NAT](#nom-de-la-règle-nat-)
      - [Définir si la règle NAT est activée ou non](#définir-si-la-règle-nat-est-activée-ou-non-)
      - [Durée de la règle NAT](#durée-de-la-règle-nat-)
      - [Protocole utilisé par la règle NAT](#durée-de-la-règle-nat-)
      - [Définir si la fonctionnalité de boucle NAT est activée ou non](#définir-si-la-fonctionnalité-de-boucle-nat-est-activée-ou-non-)
      - [Ajouter une nouvelle règle NAT](#ajouter-une-nouvelle-règle-nat-)
  4. [DMZ](#dmz)
      - [Adresse IP qui fera parti de la DMZ (demilitarized zone)](#adresse-ip-qui-fera-parti-de-la-dmz-demilitarized-zone-)
  5. [PPPoE](#pppoe)
      - [Définir la connexion en IP_Routed](#définir-la-connexion-en-ip_routed-)
      - [Nom de la connexion](#nom-de-la-connexion-)
      - [Définir si le pare-feu (firewall) est activé ou non](#définir-si-le-pare-feu-firewall-est-activé-ou-non-)
      - [Quality of Service (QoS)](#quality-of-service-qos-)
      - [ID VLAN](#id-vlan-)
      - [VLAN Tag Protocol IDentifier (TPID)](#vlan-tag-protocol-identifier-tpid-)
      - [Interface Linux](#interface-linux-)
      - [Maximum Transmission Unit (MTU, taille maximale des paquets pouvant être transmis)](#maximum-transmission-unit-mtu-taille-maximale-des-paquets-pouvant-être-transmis-)
      - [Définir si la fonctionnalité NAT est activée ou non](#définir-si-la-fonctionnalité-nat-est-activée-ou-non-)
      - [Nom d'utilisateur pour la connexion PPPoE](#nom-dutilisateur-pour-la-connexion-pppoe-)
      - [Mot de passe pour la connexion PPPoE](#mot-de-passe-pour-la-connexion-pppoe-)
      - [Définir si la connexion PPPoE est activée ou non](#définir-si-la-connexion-pppoe-est-activée-ou-non-)
      - [Passerelle secondaire du CPE (interface Linux)](#passerelle-secondaire-du-cpe-interface-linux-)
      - [Définir la connexion PPPoE comme serveur DNS secondaire](#définir-la-connexion-pppoe-comme-serveur-dns-secondaire-)
  6. [Pare-feu (firewall)](#pare-feu--firewall-)
      - [Adresse IP de destination](#adresse-ip-de-destination-)
      - [Masque de sous-réseau de l’adresse IP de destination](#masque-de-sous-réseau-de-ladresse-ip-de-destination-)
      - [Port de début du destinataire](#port-de-début-du-destinataire-)
      - [Port de fin du destinataire](#port-de-fin-du-destinataire-)
      - [Adresse IP source](#adresse-ip-source-)
      - [Masque de sous-réseau de l’adresse IP source](#masque-de-sous-réseau-de-ladresse-ip-source-)
      - [Port de début de la source](#port-de-début-de-la-source-)
      - [Port de fin de la source](#port-de-fin-de-la-source-)
      - [Version d’adresse IP](#version-dadresse-ip-)
      - [Protocole de communication](#protocole-de-communication-)
      - [Nom de la règle](#nom-de-la-règle-)
      - [Définir si la règle de pare-feu est activée ou non](#définir-si-la-règle-de-pare-feu-est-activée-ou-non-)
  7. [VoIP (SIP)](#voip--sip-)
      - [Interface Linux utilisée par l'application VoIP](#interface-linux-utilisée-par-lapplication-voip-)
      - [Définir si l'application VoIP est activée ou non](#définir-si-lapplication-voip-est-activée-ou-non-)
      - [Adresse IP du serveur proxy VoIP](#adresse-ip-du-serveur-proxy-voip-)
      - [Port du serveur proxy VoIP](#port-du-serveur-proxy-voip-)
      - [Adresse IP du serveur proxy VoIP sortant](#adresse-ip-du-serveur-proxy-voip-sortant-)
      - [Port du serveur proxy VoIP sortant](#port-du-serveur-proxy-voip-sortant-)
      - [Adresse IP du serveur Registrar](#adresse-ip-du-serveur-registrar-)
      - [Port du serveur Registrar](#port-du-serveur-registrar-)
      - [Définir si le premier compte SIP (SIP 1) est activé ou non](#définir-si-le-premier-compte-sip-sip-1-est-activé-ou-non-)
      - [Directory Number (extension) du compte SIP 1](#directory-number-extension-du-compte-sip-1-)
      - [Uniform Ressource Identifier (URI) du compte SIP 1](#uniform-ressource-identifier-uri-du-compte-sip-1-)
      - [Nom d'utilisateur d'authentification du compte SIP 1](#nom-dutilisateur-dauthentification-du-compte-sip-1-)
      - [Mot de passe d'authentification du compte SIP 1](#mot-de-passe-dauthentification-du-compte-sip-1-)
      - [Caller Line IDentification (CLID) du compte SIP 1](#caller-line-identification-clid-du-compte-sip-1-)
      - [Définir si le deuxième compte SIP (SIP 2) est activé ou non](#définir-si-le-deuxième-compte-sip-sip-2-est-activé-ou-non-)
      - [Directory Number (extension) du compte SIP 2](#directory-number-extension-du-compte-sip-2-)
      - [Uniform Ressource Identifier (URI) du compte SIP 2](#uniform-ressource-identifier-uri-du-compte-sip-2-)
      - [Nom d'utilisateur d'authentification du compte SIP 2](#nom-dutilisateur-dauthentification-du-compte-sip-2-)
      - [Mot de passe d'authentification du compte SIP 2](#mot-de-passe-dauthentification-du-compte-sip-2-)
      - [Caller Line IDentification (CLID) du compte SIP 2](#caller-line-identification-clid-du-compte-sip-2-)
      - [DigitMap du service SIP](#digitmap-du-service-sip-)
      - [Confirmer ou non la modification des paramètres en supprimant les anciennes valeurs](#confirmer-ou-non-la-modification-des-paramètres-en-supprimant-les-anciennes-valeurs-)


## WiFi
#### SSID du réseau WiFi :

    InternetGatewayDevice.LANDevice.1.WLANConfiguration.1.SSID
> Valeur possible :<br />
>  *Chaîne de caractères* 

<br />

#### Méthode de cryptage du mot de passe du WiFi :

    InternetGatewayDevice.LANDevice.1.WLANConfiguration.1.BeaconType
>  Valeurs possibles :<br />
>   `Basic` : Pas de cryptage<br />
>   `11i` : Correspond au WPA2-PSK<br />
>   `WPA` : Correspond au WPA-PSK<br />
>   `WPAand11i` : Correspond au WPA/WPA2-PSK mixed<br />

<br />

#### Mot de passe du WiFi :

    InternetGatewayDevice.LANDevice.1.WLANConfiguration.1.PreSharedKey.1.KeyPassphrase
> Valeur possible :<br />
> *`Chaîne de caractères`*  

<br />

#### Adresse IP de l'Innbox V45 :

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.IPInterface.1.IPInterfaceIPAddress
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
> *`Liste d'adresses IP (maximum 64, séparés par une virgule)`*

<br />

#### DNS (Domain Name System) :

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.DNSServers
> Valeur possible :<br />
> *`Liste d'adresses IP (maximum 64, séparés par une virgule)`*

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

#### Adresses MAC autorisées :

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.AllowedMACAddresses
> Valeur possible :<br />
> *`Liste d'adresses MAC (maximum 512, séparés par une virgule)`*

<br />

#### Adresses IP statiques :
**Attention : Le `{i}` est à remplacer par le numéro de la règle que vous souhaitez créer ou modifier.**

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.DHCPStaticAddress.{i}.Enable
> Valeurs possibles :<br />
> `true` : Distribution de l'adresse IP en fonction de l'adresse MAC activée<br />
> `false` : Distribution de l'adresse IP en fonction de l'adresse MAC désactivée

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.DHCPStaticAddress.{i}.Alias
> Valeur possible :<br />
> *`Alias (Chaîne de caractères, maximum 64)`*

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.DHCPStaticAddress.{i}.Chaddr
> Valeur possible :<br />
> *`Adresse MAC concernée`*

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.DHCPStaticAddress.{i}.Yiaddr
> Valeur possible :<br />
> *`Adresse IP attribuée`*

<br />

#### Nombre d'adresses IP statiques dans la plage d'adresses IP distribuées :

    InternetGatewayDevice.LANDevice.1.LANHostConfigManagement.DHCPStaticAddressNumberOfEntries
> Valeur possible :<br />
> *`Nombre`*

<br />

## NAT
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

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.ConnectionType
> Valeur possible :<br />
> `IP_Routed`  

<br />

#### Nom de la connexion :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.Name
> Valeur possible :<br />
> *`Chaîne de caractères`*  

<br />

#### Définir si le pare-feu (firewall) est activé ou non :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.X_BROADCOM_COM_FirewallEnabled
> Valeurs possibles :<br />
> `1` : Pare-feu (firewall) activé<br />
> `0` : Pare-feu (firewall) désactivé  

<br />

#### Quality of Service (QoS) :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.X_BROADCOM_COM_VlanMux8021p
> Valeur possible :<br />
> *`Nombre`*  

<br />

#### ID VLAN :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.X_BROADCOM_COM_VlanMuxID
> Valeur possible :<br />
> *`ID VLAN (nombre)`*  

<br />

#### VLAN Tag Protocol IDentifier (TPID) :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.X_BROADCOM_COM_VlanTpid
> Valeur possible :<br />
> *`VLAN TPID (nombre)`*  

<br />

#### Interface Linux :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.X_BROADCOM_COM_IfName
> Valeur possible :<br />
> *`Chaîne de caractères`*  

<br />

#### Maximum Transmission Unit (MTU, taille maximale des paquets pouvant être transmis) :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.MTU
> Valeur possible :<br />
> *`Nombre`*  

<br />

#### Définir si la fonctionnalité NAT est activée ou non :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.NATEnabled
> Valeurs possibles :<br />
> `true` : Fonctionnalité NAT activée<br />
> `false` : Fonctionnalité NAT désactivée  

<br />

#### Nom d'utilisateur pour la connexion PPPoE :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.Username
> Valeur possible :<br />
> *`Chaîne de caractères`*  

<br />

#### Mot de passe pour la connexion PPPoE :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.Password
> Valeur possible :<br />
> *`Chaîne de caractères`*  

<br />

#### Définir si la connexion PPPoE est activée ou non :

    InternetGatewayDevice.WANDevice.1.WANConnectionDevice.1.WANPPPConnection.Enable
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
> *`Interface Linux (Chaîne de caractères)`*  

<br />

## Pare-feu (firewall)
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

    InternetGatewayDevice.Services.VoiceService.1.X_BROADCOM_COM_BoundIfName
> Valeur possible :<br />
> *`Interface Linux (Chaîne de caractères)`*  

<br />

#### Définir si l'application VoIP est activée ou non :

    InternetGatewayDevice.Services.VoiceService.1.VoiceProfile.1.Enable
> Valeur possible :<br />
> `Enabled` : Application VoIP activée  

<br />

#### Adresse IP du serveur proxy VoIP :

    InternetGatewayDevice.Services.VoiceService.1.VoiceProfile.1.SIP.ProxyServer
> Valeur possible :<br />
> *`Adresse IP`*  

<br />

#### Port du serveur proxy VoIP :

    InternetGatewayDevice.Services.VoiceService.1.VoiceProfile.1.SIP.ProxyServerPort
> Valeur possible :<br />
> *`Port (nombre)`*  

<br />

#### Adresse IP du serveur proxy VoIP sortant :

    InternetGatewayDevice.Services.VoiceService.1.VoiceProfile.1.SIP.OutboundProxy
> Valeur possible :<br />
> *`Adresse IP`*  

<br />

#### Port du serveur proxy VoIP sortant :

    InternetGatewayDevice.Services.VoiceService.1.VoiceProfile.1.SIP.OutboundProxyPort
> Valeur possible :<br />
> *`Port (nombre)`*  

<br />

#### Adresse IP du serveur Registrar :

    InternetGatewayDevice.Services.VoiceService.1.VoiceProfile.1.SIP.RegistrarServer
> Valeur possible :<br />
> *`Adresse IP`*  

<br />

#### Port du serveur Registrar :

    InternetGatewayDevice.Services.VoiceService.1.VoiceProfile.1.SIP.RegistrarServerPort
> Valeur possible :<br />
> *`Port (nombre)`*  

<br />

#### Définir si le premier compte SIP (SIP 1) est activé ou non :

    InternetGatewayDevice.Services.VoiceService.1.VoiceProfile.1.Line.1.Enable
> Valeur possible :<br />
> `Enabled` : Premier compte SIP activé  

<br />

#### Directory Number (extension) du compte SIP 1 :

    InternetGatewayDevice.Services.VoiceService.1.VoiceProfile.1.Line.1.DirectoryNumber
> Valeur possible :<br />
> *`Port FXS (nombre)`*  

<br />

#### Uniform Ressource Identifier (URI) du compte SIP 1 :

    InternetGatewayDevice.Services.VoiceService.1.VoiceProfile.1.Line.1.SIP.URI
> Valeur possible :<br />
> *`Port FXS (nombre)`*  

<br />

#### Nom d'utilisateur d'authentification du compte SIP 1 :

    InternetGatewayDevice.Services.VoiceService.1.VoiceProfile.1.Line.1.SIP.AuthUserName
> Valeur possible :<br />
> *`Port FXS (nombre)`*  

<br />

#### Mot de passe d'authentification du compte SIP 1 :

    InternetGatewayDevice.Services.VoiceService.1.VoiceProfile.1.Line.1.SIP.AuthPassword
> Valeur possible :<br />
> *`Port FXS (nombre)`*  

<br />

#### Caller Line IDentification (CLID) du compte SIP 1 :

    InternetGatewayDevice.Services.VoiceService.1.VoiceProfile.1.Line.1.CallingFeatures.CallerIDName
> Valeur possible :<br />
> *`Port FXS (nombre)`*  

<br />

#### Définir si le deuxième compte SIP (SIP 2) est activé ou non :

    InternetGatewayDevice.Services.VoiceService.1.VoiceProfile.1.Line.2.Enable
> Valeur possible :<br />
> `Enabled` : Premier compte SIP activé  

<br />

#### Directory Number (extension) du compte SIP 2 :

    InternetGatewayDevice.Services.VoiceService.1.VoiceProfile.1.Line.2.DirectoryNumber
> Valeur possible :<br />
> *`Port FXS (nombre)`*  

<br />

#### Uniform Ressource Identifier (URI) du compte SIP 2 :

    InternetGatewayDevice.Services.VoiceService.1.VoiceProfile.1.Line.2.SIP.URI
> Valeur possible :<br />
> *`Port FXS (nombre)`*  

<br />

#### Nom d'utilisateur d'authentification du compte SIP 2 :

    InternetGatewayDevice.Services.VoiceService.1.VoiceProfile.1.Line.2.SIP.AuthUserName
> Valeur possible :<br />
> *`Port FXS (nombre)`*  

<br />

#### Mot de passe d'authentification du compte SIP 2 :

    InternetGatewayDevice.Services.VoiceService.1.VoiceProfile.1.Line.2.SIP.AuthPassword
> Valeur possible :<br />
> *`Port FXS (nombre)`*  

<br />

#### Caller Line IDentification (CLID) du compte SIP 2 :

    InternetGatewayDevice.Services.VoiceService.1.VoiceProfile.1.Line.2.CallingFeatures.CallerIDName
> Valeur possible :<br />
> *`Port FXS (nombre)`*  

<br />

#### DigitMap du service SIP :

    InternetGatewayDevice.Services.VoiceService.1.VoiceProfile.1.DigitMap
> Valeur possible :<br />
> *`DigitMap (format : xxxxxxx)`*  

<br />

#### Confirmer ou non la modification des paramètres en supprimant les anciennes valeurs :

    InternetGatewayDevice.Services.VoiceService.1.VoiceProfile.1.Reset
> Valeurs possibles :<br />
> `true` : Modifications validées et suppression de l'ancienne configuration<br />
> `false` : Modifications annulées et maintient de l'ancienne configuration
