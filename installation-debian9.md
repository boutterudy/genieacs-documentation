## Installation
> Cette installation est réalisée sous Debian 9.

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

    mv genieacs-documentation/Installation/Scripts/acs /etc/init.d/acs
    mv genieacs-documentation/Installation/Scripts/acs /etc/init.d/acs-v
    mv genieacs-documentation/Installation/Scripts/acs /etc/init.d/acs-clear-logs
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
    
## Démarrer uniquement GenieACS (sans GenieACS-GUI)
    cd /opt/genieacs/bin
    mongod --dbpath=/var/lib/mongodb &
    /opt/genieacs/bin/./genieacs-cwmp &
    /opt/genieacs/bin/./genieacs-nbi &
    /opt/genieacs/bin/./genieacs-fs &
