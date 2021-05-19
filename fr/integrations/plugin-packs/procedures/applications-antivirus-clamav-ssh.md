---
id: applications-antivirus-clamav-ssh
title: Antivirus ClamAV
---

## Vue d'ensemble

*Describe quickly what the brand the associated devices are*

The Centreon Plugin Pack *Antivirus ClamAV* aims to collect...

## Contenu du Pack

### Objets supervisés

* Plugin Target 1 

* Plugin Target 2

* ...

### Monitored metrics

<!--DOCUSAURUS_CODE_TABS-->

<!--Update-Status-->

| Metric name    | Description |
|:---------------|:------------|
| engine-status  |             |
| maindb-status  |             |
| dailydb-status |             |
| daily          |             |
| main           |             |

<!--END_DOCUSAURUS_CODE_TABS-->

## Prérequis

*Specify prerequisites that are relevant. You may want to just provide a link to
the manufacturer official documentation BUT you should try to be as complete as
possible here as it will save time to everybody*

## Installation

<!--DOCUSAURUS_CODE_TABS-->

<!--Online IMP Licence & IT-100 Editions-->

1. Installer le Plugin Centreon sur tous les collecteurs Centreon devant superviser des resources *TO CHANGE*:

```bash
yum install centreon-plugin-Applications-Clamav-Ssh
```

2. Sur l'interface Integration de Centreon, installer le Plugin Pack *Antivirus ClamAV* depuis la page "Configuration > Plugin packs > Manager"

<!--Offline IMP License-->

1. Installer le Plugin Centreon sur tous les collecteurs Centreon devant superviser des resources *TO CHANGE*:

```bash
yum install centreon-plugin-Applications-Clamav-Ssh
```

2. Sur le serveur Central Centreon, installer le RPM du Pack *Antivirus ClamAV*:

 ```bash
yum install centreon-pack-applications-antivirus-clamav-ssh
```

3. Sur l'interface Integration de Centreon, installer le Plugin Pack *Antivirus ClamAV* depuis la page "Configuration > Plugin packs > Manager"

<!--END_DOCUSAURUS_CODE_TABS-->

## Configuration

### Hôte

* Ajoutez un Hôte à Centreon depuis la page "Configuration > Hôtes".
* Complétez les champs "Nom","Alias" & "IP Address / DNS" correspondant à votre serveur *TO CHANGE*
* Appliquez le Modèle d'Hôte *Applications-Antivirus-Clamav-Ssh-custom* * Une fois le modèle appliqué, les Macros ci-dessous indiquées comme requises (*Mandatory*) doivent être renseignées 

| Mandatory | Name         | Description                                                                        |
|:----------|:-------------|:-----------------------------------------------------------------------------------|
|           | EXTRAOPTIONS | Any extra option you may want to add to every command\_line (eg. a --verbose flag) |

## Comment puis-je tester le Plugin et que signifient les options des commandes ? 

 Une fois le Plugin installé, vous pouvez tester celui-ci directement en ligne 
 de commande depuis votre collecteur Centreon en vous connectant avec 
 l'utilisateur *centreon-engine*:

 ```bash
 /usr/lib/centreon/plugins//centreon_clamav_ssh.pl  \
    --plugin=apps::antivirus::clamav::local::plugin  \
    --mode=update-status  \
    --hostname=10.0.0.1  \
    --remote   \
    --warning-engine-status=''  \
    --critical-engine-status='' \
    --warning-maindb-status=''  \
    --critical-maindb-status='%{last_maindb_version} ne %{current_maindb_version}' \
    --warning-dailydb-status=''  \
    --critical-dailydb-status='%{last_dailydb_version} ne %{current_dailydb_version} || %{current_dailydb_timediff} > 432000'
 ```

 La commande devrait retourner un message de sortie similaire à :

 ```bash
OK : .... | 
 ```

  This command would trigger a WARNING alarm if *WHAT* is reported as (--warning-vault-availability-percentage) and a CRITICAL alarm if less than 50% (--critical-vault-availability-percentage='50:').

 La liste de toutes les options complémentaires et leur signification peut être 
 affichée en ajoutant le paramètre ```--help``` à la commande:

 Tous les modes disponibles peuvent être affichés en ajoute le paramètre 
 ```--list-mode``` à la commande:

 ```bash
 /usr/lib/centreon/plugins//centreon_clamav_ssh.pl  \
    --plugin=apps::antivirus::clamav::local::plugin  \
    --help
 ```

 ### Diagnostic des erreurs communes
 
 #### ```Error message```
 ...... 
