# Enterprise Linux Lab Report - Troubleshooting

- Student name: NAME
- Class/group: TIN-TI-3B (Gent) [weglaten wat niet past]

## Instructions

- Write a detailed report in the "Report" section below (in Dutch or English)
- Use correct Markdown! Use fenced code blocks for commands and their output, terminal transcripts, ...
- The different phases in the bottom-up troubleshooting process are described in their own subsections (heading of level 3, i.e. starting with `###`) with the name of the phase as title.
- Every step is described in detail:
    - describe what is being tested
    - give the command, including options and arguments, needed to execute the test, or the absolute path to the configuration file to be verified
    - give the expected output of the command or content of the configuration file (only the relevant parts are sufficient!)
    - if the actual output is different from the one expected, explain the cause and describe how you fixed this by giving the exact commands or necessary changes to configuration files
- In the section "End result", describe the final state of the service:
    - copy/paste a transcript of running the acceptance tests
    - describe the result of accessing the service from the host system
    - describe any error messages that still remain

## Report

## Netwerklaag
### Phase 1:Observatie
* Bij het starten van de VM: error: following physical network interfaces were not found:vboxnet0
### Phase 2:Hypotese
* verkeerde netwerkinstellingen vbox
### Phase 3:Voorspelling
* 2e adapter uitschakelen
### Phase 4:Test
* network settings van de vm -> 2e adapter uitschakelen
### Phase 5:Analyse 
* aanpassing is succesvol vm start op


### Phase 1:Observatie
* keyboard staat in qwery
### Phase 2:Hypotese
* verkeerde keyboardinstelling
### Phase 3:Voorspelling
* keyboardinstellingen veranderen 
### Phase 4:Test
* `loadkeys be`
### Phase 5:Analyse 
* aanpassing is succesvol keyboard is azerty

## Internet laag
### Phase 1:Observatie
* pingen lukt niet
### Phase 2:Hypotese
* verkeerde ipinstellingen
### Phase 3:Voorspelling
* ip isntellingen aanpassen 
### Phase 4:Test
* `ip a`
### Phase 5:Analyse 
* default ip van vbox `10.0.2.15` state is: up


### Phase 1:Observatie
* pingen lukt niet
### Phase 2:Hypotese
* verkeerde default gateway instellingen
### Phase 3:Voorspelling
* default gateway isntellingen aanpassen 
### Phase 4:Test
* `ip r`
### Phase 5:Analyse 
* juiste default gateway van vbox `10.0.2.2` 


### Phase 1:Observatie
* pingen lukt niet
### Phase 2:Hypotese
* verkeerde dns gateway instellingen
### Phase 3:Voorspelling
* dns isntellingen aanpassen 
### Phase 4:Test
* `cat \etc\resolv.conf`
### Phase 5:Analyse 
* juiste dns van vbox `10.0.2.3` 

### Phase 1:Observatie
* dig lukt niet
### Phase 2:Hypotese
* package niet geinstaleerd
### Phase 3:Voorspelling
* package waar dig inzit instaleren 
### Phase 4:Test
* `yum install bind-utils`
### Phase 5:Analyse 
* dig commando kan gebruit worden

## Transportlaag
### Phase 1:Observatie
* nginix is niet bereikbaar
### Phase 2:Hypotese
* is de service wel active?
### Phase 3:Voorspelling
* service activeren
### Phase 4:Test
* `systemctl status nginx.service`
* output: `Active: inactive (dead)`
* activeren service `service nginx restart`
* output:failed
* permissios checken `namei -om /usr/share/nginx/html/index.html`
* errorlogs checken
* errorlogs openen geeft een error
* nginx.conf edit `underscores_in_headers on;` en `sendfile off;`
* firewall
```
sudo firewall-cmd --permanent --zone=public --add-service=http 
sudo firewall-cmd --permanent --zone=public --add-service=https
sudo firewall-cmd --reload
```
* apache is uitgeschakeld
```
systemctl stop httpd
systemctl disable httpd
```
* ssl keys
* Gevonden dat het pad naar de ssl verkeerd genoteerd was aangepast met vi
### Phase 5:Analyse 
* service nginx is running
## End result



## Resources

List all sources of useful information that you encountered while completing this assignment: books, manuals, HOWTO's, blog posts, etc.
https://askubuntu.com/questions/550937/change-from-qwerty-to-azerty-in-command-line
https://techglimpse.com/install-bind-utils-linux-yum-tutorial/
https://serverfault.com/questions/213185/how-to-restart-nginx
https://www.digitalocean.com/community/tutorials/how-to-create-an-ssl-certificate-on-nginx-for-ubuntu-14-04
