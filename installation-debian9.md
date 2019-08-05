## Installation de GenieACS & GenieACS GUI
GenieACS & GenieACS GUI dépendent de nombreux autres programmes, ce qui explique un si grand nombre de procédures d'installation.<br />

> Cette installation est réalisée sous Debian 9.

## Dépendances
* Libssl
* MongoDB
* Gem
* Openssl
* Zlib
* Ruby
* Node
* Redis

## Sommaire
1. [Prérequis](#pr%C3%A9requis-)
1. [Installation de Libssl](#installation-de-libssl-)
1. [Installation de MongoDB](#installation-de-mongodb-)
1. [Installation de Gem](#installation-de-gem-)
1. [Installation d'Openssl](#installation-dopenssl-)
1. [Installation de Zlib](#installation-de-zlib-)
1. [Installation de Ruby](#installation-de-ruby-)
1. [Installation de Node](#installation-de-node-)
1. [Installation de Redis](#installation-de-redis-)
1. [Installation de GenieACS](#installation-de-genieacs-)
1. [Installation de GenieACS-GUI](#installation-de-genieacs-gui-)
1. [Création du service "acs"](#cr%C3%A9ation-du-service-acs-)
1. [Démarrer manuellement GenieACS & GenieACS-GUI](#d%C3%A9marrer-manuellement-genieacs--genieacs-gui-)
1. [Démarrer uniquement GenieACS \(sans GenieACS-GUI\)](#d%C3%A9marrer-uniquement-genieacs-sans-genieacs-gui)

### Prérequis :

    apt-get install git-core curl build-essential openssl libssl-dev  libgdm1 libgdm-dev zlib1g zlib1g-dbg zlib1g-dev zlibc zlib-gst libedit* tcl bundler dirmngr software-properties-common curl g++ gcc autoconf automake bison libc6-dev libffi-dev libgdbm-dev libncurses5-dev libsqlite3-dev libtool libyaml-dev make pkg-config sqlite3 zlib1g-dev libgmp-dev libreadline-dev libssl-dev
    git clone https://github.com/boutterudy/genieacs-documentation.git /opt/

> Toutes les opérations qui suivent doivent être effectuées depuis le dossier `/opt/genieacs-documentation/Installation`
### Installation de Libssl :

    dpkg -i libssl1.0.0_1.0.1t-1+deb8u11_amd64.deb

### Installation de MongoDB :

    dpkg -i mongodb-org-server_3.4.20_amd64.deb

### Installation de Gem :

    \curl -L https://get.rvm.io | bash -s stable --ruby
    source /usr/local/rvm/scripts/rvm

### Installation d'Openssl :

    rvm pkg install openssl
    gpg --keyserver keys.gnupg.net --recv-keys 3602B07F55D0C732

### Installation de Zlib :

    tar -zxvf zlib_1.2.8.dfsg.orig.tar.gz -C /opt/
    cd /opt/zlib-1.2.8/
    ./configure
    make
    make install

### Installation de Ruby :

    tar -zxvf ruby-2.6.3.tar.gz -C /opt/
    cd /opt/ruby-2.6.3
    ./configure
    make
    make install
    gem install rails
    gem install bundle

### Installation de Node :

    tar -zxvf zlib_1.2.8.dfsg.orig.tar.gz -C /opt/
    cd /opt/node-v8.16.0
    ./configure
    make
    make install

### Installation de Redis :

    tar -zxvf redis-5.0.5.tar.gz -C /opt/
    cd /opt/redis-5.0.5
    make
    make test
    make install
    curl -L https://npmjs.org/install.sh | sh

### Installation de GenieACS :

    tar -zxvf genieacs.tar.gz -C /opt/
    cd /opt/genieacs
    npm install -D ts-node
    npm install -D typescript
    npm install -D esm
    npm install libxmljs
    npm audit fix
    npm update js-yaml --depth 5
    npm run configure
    npm install
    cp config/config-sample.json config/config.json

### Installation de GenieACS-GUI :

    tar -zxvf genieacs-gui.tar.gz -C /opt/
    cd /opt/genieacs-gui
    gem install rake -v 12.3.1
    gem install concurrent-ruby -v 1.0.5
    gem install i18n -v 1.1.1
    gem install activesupport -v 5.2.1
    gem install erubi -v 1.7.1
    gem install mini_portile2 -v 2.3.0
    gem install nokogiri -v 1.8.5
    gem install loofah -v 2.2.2
    gem install actionview -v 5.2.1
    gem install rack -v 2.0.5
    gem install actionpack -v 5.2.1
    gem install actioncable -v 5.2.1
    gem install globalid -v 0.4.1
    gem install activejob -v 5.2.1
    gem install actionmailer -v 5.2.1
    gem install activemodel -v 5.2.1
    gem install activerecord -v 5.2.1
    gem install mimemagic -v 0.3.2
    gem install activestorage -v 5.2.1
    gem install bigdecimal -v 1.3.5
    gem install bindex -v 0.5.0
    gem install byebug -v 10.0.2
    gem install method_source -v 0.9.0
    gem install thor -v 0.20.0
    gem install railties -v 5.2.1
    gem install coffee-rails -v 4.2.2
    gem install ffi -v 1.9.25
    gem install jbuilder -v 2.7.0
    gem install rb-inotify -v 0.9.10
    gem install listen -v 3.0.8
    gem install puma -v 3.12.0
    gem install rails -v 5.2.1
    gem install sass -v 3.6.0
    gem install tilt -v 2.0.8
    gem install sqlite3 -v 1.3.13
    gem install uglifier -v 4.1.19
    gem install web-console -v 3.7.0
    gem install tzinfo-data
    gem install websocket-extensions -v 0.1.3
    gem install websocket-driver -v 0.7.0
    gem install jquery-rails -v 4.3.3
    gem install libv8 -v 3.16.14.19
    gem install ref -v 2.0.0
    gem install sass-rails -v 5.0.7
    gem install spring -v 2.0.2
    gem install spring-watcher-listen -v 2.0.1
    gem install therubyracer -v 0.12.3
    gem install turbolinks-source -v 5.2.0
    gem install turbolinks -v 5.2.0
    bundle
    cp config/summary_parameters-sample.yml config/summary_parameters.yml
    cp config/index_parameters-sample.yml config/index_parameters.yml
    cp config/parameter_renderers-sample.yml config/parameter_renderers.yml
    cp config/parameters_edit-sample.yml config/parameters_edit.yml
    cp config/roles-sample.yml config/roles.yml
    cp config/users-sample.yml config/users.yml
    cp config/graphs-sample.json.erb config/graphs.json.erb
    cd /opt/genieacs/bin
    mongod --dbpath=/var/lib/mongodb
    cd /opt/genieacs-gui/bin
    rails db:migrate RAILS_ENV=development

## Création du service "acs" :

    mv /opt/genieacs-documentation/Installation/Scripts/acs /etc/init.d/acs
    mv /opt/genieacs-documentation/Installation/Scripts/acs /etc/init.d/acs-v
    mv /opt/genieacs-documentation/Installation/Scripts/acs /etc/init.d/acs-clear-logs
    chmod +x /etc/init.d/acs
    chmod +x /etc/init.d/acs-v
    chmod +x /etc/init.d/acs-clear-logs
    update-rc.d acs defaults
    crontab -e

Ajouter les lignes suivantes (après *`crontab -e`*) :

    # Démarrage de l'ACS
	@reboot /etc/init.d/acs start > /dev/null 2>&1

	# Vérification de l'état de l'ACS
	* * * * * sleep 5; su root /etc/init.d/acs-v > /dev/null 2>&1

	# Suppression des logs datant d'un mois
	@daily /etc/init.d/acs-clear-logs
	@daily rm -rf /opt/genieacs/logs/interruptions

## Démarrer manuellement GenieACS & GenieACS-GUI :

    cd /opt/genieacs/bin
    mongod --dbpath=/var/lib/mongodb &
    /opt/genieacs/bin/./genieacs-cwmp &
    /opt/genieacs/bin/./genieacs-nbi &
    /opt/genieacs/bin/./genieacs-fs &
    cd /opt/genieacs-gui
    rails s
    
## Démarrer uniquement GenieACS (sans GenieACS-GUI) :
    cd /opt/genieacs/bin
    mongod --dbpath=/var/lib/mongodb &
    /opt/genieacs/bin/./genieacs-cwmp &
    /opt/genieacs/bin/./genieacs-nbi &
    /opt/genieacs/bin/./genieacs-fs &

## Configuration de GenieACS GUI :
* Si nécessaire, rajouter une clé secrète dans `/opt/genieacs-gui/config/secrets.yml`.
* Si nécessaire modifier les paramètres inscrits dans `/opt/genieacs-gui/config/summary_parameters.yml`
	> Pour l'Innbox V45, il est nécessaire de modifier la ligne de l'adresse MAC pour qu'elle corresponde au bon paramètre TR-069 : `MAC: InternetGatewayDevice.DeviceInfo.SerialNumber`

## Erreurs possibles durant l'installation :
### ERREUR 1 : `The dependency tzinfo-data (>= 0) will be unused by any of the platforms Bundler is installing for. Bundler is installing for ruby but the dependency is only for x86-mingw32, x86-mswin32, x64-mingw32, java. To add those platforms to the bundle, run 'bundle lock --add-platform x86-mingw32 x86-mswin32 x64-mingw32 java'.`

* ### Explications :
	Lors de l’installation de GenieACS-GUI, vous devez saisir la commande `bundle` après quelques étapes, cependant il y a de grandes chances que l’exécution de cette commande ne se termine jamais, en ayant affiché le message d'erreur précédemment cité.<br />
	Cela vous empêche donc d’installer GenieACS-GUI car l’installation ne se fait pas.

* ### Solution :
	Il s’agit en fait d’un problème de dépendances manquantes, lorsque vous effectuez la commande “bundle check”, vous verrez toutes les dépendances manquantes.

	    The following gems are missing
	    * rake (12.3.1)
	    * concurrent-ruby (1.0.5)
	    * i18n (1.1.1)
	    * activesupport (5.2.1)
	    * erubi (1.7.1)
	    * mini_portile2 (2.3.0)
	    * nokogiri (1.8.5)
	    * loofah (2.2.2)
	    * actionview (5.2.1)
	    * rack (2.0.5)
	    * actionpack (5.2.1)
	    * actioncable (5.2.1)
	    * globalid (0.4.1)
	    * activejob (5.2.1)
	    * actionmailer (5.2.1)
	    * activemodel (5.2.1)
	    * activerecord (5.2.1)
	    * mimemagic (0.3.2)
	    * activestorage (5.2.1)
	    * bigdecimal (1.3.5)
	    * bindex (0.5.0)
	    * byebug (10.0.2)
	    * coffee-script-source (1.12.2)
	    * execjs (2.7.0)
	    * coffee-script (2.4.1)
	    * method_source (0.9.0)
	    * thor (0.20.0)
	    * railties (5.2.1)
	    * coffee-rails (4.2.2)
	    * ffi (1.9.25)
	    * multi_json (1.13.1)
	    * jbuilder (2.7.0)
	    * jquery-rails (4.3.3)
	    * libv8 (3.16.14.19)
	    * rb-fsevent (0.10.3)
	    * rb-inotify (0.9.10)
	    * listen (3.0.8)
	    * puma (3.12.0)
	    * rails (5.2.1)
	    * ref (2.0.0)
	    * sass-listen (4.0.0)
	    * sass (3.6.0)
	    * tilt (2.0.8)
	    * sass-rails (5.0.7)
	    * spring (2.0.2)
	    * spring-watcher-listen (2.0.1)
	    * sqlite3 (1.3.13)
	    * therubyracer (0.12.3)
	    * turbolinks-source (5.2.0)
	    * turbolinks (5.2.0)
	    * uglifier (4.1.19)
	    * web-console (3.7.0)

	Il faudra donc les installer soit par la commande `bundle install`, soit par l’installation manuelle des dépendances une par une :

		gem install rake -v 12.3.1
		gem install concurrent-ruby -v 1.0.5
		gem install i18n -v 1.1.1
		gem install activesupport -v 5.2.1
		gem install erubi -v 1.7.1
		gem install mini_portile2 -v 2.3.0
		gem install nokogiri -v 1.8.5
		gem install loofah -v 2.2.2
		gem install actionview -v 5.2.1
		gem install rack -v 2.0.5
		gem install actionpack -v 5.2.1
		gem install actioncable -v 5.2.1
		gem install globalid -v 0.4.1
		gem install activejob -v 5.2.1
		gem install actionmailer -v 5.2.1
		gem install activemodel -v 5.2.1
		gem install activerecord -v 5.2.1
		gem install mimemagic -v 0.3.2
		gem install activestorage -v 5.2.1
		gem install bigdecimal -v 1.3.5
		gem install bindex -v 0.5.0
		gem install byebug -v 10.0.2
		gem install method_source -v 0.9.0
		gem install thor -v 0.20.0
		gem install railties -v 5.2.1
		gem install coffee-rails -v 4.2.2
		gem install ffi -v 1.9.25
		gem install jbuilder -v 2.7.0
		gem install rb-inotify -v 0.9.10
		gem install listen -v 3.0.8
		gem install puma -v 3.12.0
		gem install rails -v 5.2.1
		gem install sass -v 3.6.0
		gem install tilt -v 2.0.8
		gem install sqlite3 -v 1.3.13
		gem install uglifier -v 4.1.19
		gem install web-console -v 3.7.0
		gem install tzinfo-data
	Il est ensuite possible d’installer GenieACS-GUI avec la commande `bundle`.
	Si le problème persiste, vérifiez les dépendances avec la commande `bundle check`.
### ERREUR 2 & 2 bis : `!!! WARNING The following tests failed: *** [err]: Setup slave in tests/unit/wait.tcl Replication not started.[...]` & <i>Forcing process 25910 to exit... Logged warnings (pid 25910):(none)[exception]: Executing test client: ERR.[...]`
* ### Erreur 2 :
	
	    !!! WARNING The following tests failed:
	    *** [err]: Setup slave in tests/unit/wait.tcl
	    Replication not started.
	    *** [err]: WAIT should not acknowledge 1 additional copy if slave is blocked in
	    tests/unit/wait.tcl
	    Expected condition '[$master wait 1 3000] == 0' to be true ([::redis::redisHandle4 wait
	    1 3000] == 0)
	    *** [err]: slave buffer are counted correctly in tests/unit/maxmemory.tcl
	    Replication not started.
	    *** [err]: replica buffer don't induce eviction in tests/unit/maxmemory.tcl
	    Replication not started.
	    Cleanup: may take some time... OK
	    Makefile:262 : la recette pour la cible « test » a échouée
	    make[1]: *** [test] Erreur 1
	    make[1] : on quitte le répertoire « /root/installation/redis-5.0.5/src »
	    Makefile:6 : la recette pour la cible « test » a échouée
	    make: *** [test] Erreur 2

* ### Erreur 2 bis :

	    Forcing process 25910 to exit...
	    Logged warnings (pid 25910):
	    (none)
	    [exception]: Executing test client: ERR.
	    ERR
	    while executing
	    "[srv $level "client"] {*}$args"
	    (procedure "r" line 7)
	    invoked from within
	    "r debug loadaof"
	    ("uplevel" body line 5)
	    invoked from within
	    "uplevel 1 $code"
	    (procedure "test" line 47)
	    invoked from within
	    "test {SET - use EX/PX option, TTL should not be reseted after loadaof} {
	    r config set appendonly yes
	    r set foo bar EX 100
	    afte..."
	    ("uplevel" body line 208)
	    invoked from within
	    "uplevel 1 $code "
	    (procedure "start_server" line 3)
	    invoked from within
	    "start_server {tags {"expire"}} {
	    test {EXPIRE - set timeouts multiple times} {
	    r set x foobar
	    set v1 [r expire x 5]
	    set v2..."
	    (file "tests/unit/expire.tcl" line 1)
	    invoked from within
	    "source $path"
	    (procedure "execute_tests" line 4)
	    invoked from within
	    "execute_tests $data"
	    (procedure "test_client_main" line 10)
	    invoked from within
	    "test_client_main $::test_server_port "
	    Killing still running Redis server 25751
	    Killing still running Redis server 26734
	    Killing still running Redis server 26762
	    Killing still running Redis server 26788
	    Killing still running Redis server 26929
	    Killing still running Redis server 27974
	    Killing still running Redis server 28525
	    Killing still running Redis server 28902
	    Killing still running Redis server 28950
	    Killing still running Redis server 28976
	    Killing still running Redis server 29411
	    Killing still running Redis server 29431
	    Killing still running Redis server 29455
	    Killing still running Redis server 29755
	    Killing still running Redis server 30163
	    I/O error reading reply
	    while executing
	    "{*}$r type $k"
	    (procedure "createComplexDataset" line 43)
	    invoked from within
	    "createComplexDataset $r $ops"
	    (procedure "bg_complex_data" line 4)
	    invoked from within
	    "bg_complex_data [lindex $argv 0] [lindex $argv 1] [lindex $argv 2] [lindex $argv 3]"
	    (file "tests/helpers/bg_complex_data.tcl" line 10)I/O error reading reply
	    while executing
	    "{*}$r lpush $k $v"
	    ("uplevel" body line 1)
	    invoked from within
	    "uplevel 1 [lindex $args $path]"
	    (procedure "randpath" line 3)
	    invoked from within
	    "randpath {{*}$r lpush $k $v} {{*}$r rpush $k $v} {{*}$r lrem $k 0 $v} {{*}$r rpop $k} {{*}$r lpop $k}"
	    (procedure "createComplexDataset" line 51)
	    invoked from within
	    "createComplexDataset $r $ops"
	    (procedure "bg_complex_data" line 4)
	    invoked from within
	    "bg_complex_data [lindex $argv 0] [lindex $argv 1] [lindex $argv 2] [lindex $argv 3]"
	    (file "tests/helpers/bg_complex_data.tcl" line 10)
	    I/O error reading reply
	    while executing
	    "{*}$r zunionstore $k2 2 $k $otherzset"
	    ("uplevel" body line 2)
	    invoked from within
	    "uplevel 1 [lindex $args $path]"
	    (procedure "randpath" line 3)
	    invoked from within
	    "randpath {
	    {*}$r zunionstore $k2 2 $k $otherzset
	    } {
	    ..."
	    ("uplevel" body line 4)
	    invoked from within
	    "uplevel 1 [lindex $args $path]"
	    (procedure "randpath" line 3)
	    invoked from within
	    "randpath {{*}$r zadd $k $d $v} {{*}$r zrem $k $v} {
	    set otherzset [findKeyWithType {*}$r zset]
	    ..."
	    (procedure "createComplexDataset" line 68)
	    invoked from within
	    "createComplexDataset $r $ops"
	    (procedure "bg_complex_data" line 4)
	    invoked from within
	    "bg_complex_data [lindex $argv 0] [lindex $argv 1] [lindex $argv 2] [lindex $argv 3]"
	    (file "tests/helpers/bg_complex_data.tcl" line 10)
	    Killing still running Redis server 30179
	    Makefile:262 : la recette pour la cible « test » a échouée
	    make[1]: *** [test] Erreur 1
	    make[1] : on quitte le répertoire « /opt/redis-5.0.5/src »
	    Makefile:6 : la recette pour la cible « test » a échouée
	    make: *** [test] Erreur 2

* ### Explications :
	Lors de l’installation de Redis, il est possible qu’une des erreurs suivantes apparaisse lorsque vous saisirez la commande `make test`.
* ### Solution :
	Dans les deux cas, relancez la commande “make test” jusqu’à ce que cela fonctionne. Toutefois, veillez à ce qu’il n’y ai que ces deux types d’erreurs, car s’il y en a une ou plusieurs autres, cette solution ne fonctionnera peut-être pas.

### ERREUR 3 :`npm WARN lifecycle genieacs@1.2.0-dev~install: cannot run in wd genieacs@1.2.0-dev npm run configure (wd=/opt/genieacs)`
* ### Explications :
	Durant l’installation de GenieACS, il se peut que lors de la saisie de la commande `npm install` l’erreur citée précédemment survienne.
* ### Solution :
	Dans ce cas là, utiliser la commande `npm install --unsafe-perm` au lieu de `npm install`.
