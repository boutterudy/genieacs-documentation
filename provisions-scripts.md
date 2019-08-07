# Provisions Scripts
## Sommaire
 - [Reboot un CPE](#reboot-un-cpe)
 - [Refresh toutes les valeurs paramètres d'un CPE](#refresh-toutes-les-valeurs-paramètres-dun-cpe)

## Reboot un CPE
Name : `reboot`
Script :

    declare("Reboot", null, {value: Date.now() - (10 * 1000)});
## Refresh toutes les valeurs paramètres d'un CPE
Name : `refreshAll`
Script :

    declare("*", {value: Date.now()});
    declare("*.*", {value: Date.now()});
    declare("*.*.*", {value: Date.now()});
    declare("*.*.*.*", {value: Date.now()});
    declare("*.*.*.*.*", {value: Date.now()});
    declare("*.*.*.*.*.*", {value: Date.now()});
    declare("*.*.*.*.*.*.*", {value: Date.now()});
    declare("*.*.*.*.*.*.*.*", {value: Date.now()});
    declare("*.*.*.*.*.*.*.*.*", {value: Date.now()});
