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
* `loadkeys fr`
### Phase 5:Analyse 
* aanpassing is succesvol keyboard is azerty

### Phase 1:Observatie
* pingen lukt nier
### Phase 2:Hypotese
* verkeerde ipinstellingen
### Phase 3:Voorspelling
* ip isntellingen aanpassen 
### Phase 4:Test
* `ip a`
### Phase 5:Analyse 
* default ip van vbox `10.0.2.15` state is: up


## End result



## Resources

List all sources of useful information that you encountered while completing this assignment: books, manuals, HOWTO's, blog posts, etc.
https://askubuntu.com/questions/550937/change-from-qwerty-to-azerty-in-command-line
