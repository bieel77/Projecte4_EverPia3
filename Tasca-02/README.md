# T02: DPR: còpies de seguretat. Cas pràctic

## Introducció al cas

A la tasca anterior heu dissenyat una política de còpies de seguretat pel nostre nou client **"Muntatges i Serveis Tècnics SL"**. Ara toca passar a l’acció i portar a la pràctica l’estudi anterior. El client demana que s’elaborin unes guies tècniques amb proves de concepte per tal que el seu personal estigui qualificat per implantar el pla de còpies de seguretat.

---

## Part 1: Còpia seguretat dels equips clients Windows

Encara que en principi el DPR no contemplaria fer còpia dels arxius locals dels equips clients, se’ns demana fer una excepció amb l’equip Windows del director de l’empresa. En aquest equip es guarda informació important que no es vol tenir accessible al servidor de fitxers de l’empresa.

Per aquest motiu és necessari definir una política de còpies de seguretat seguint l’esquema **3-2-1**:
Es farà una còpia de seguretat a un disc secundari que té el propi equip.
Una segona còpia al **cloud**, en aquest cas, **Google Drive** usant l’eina **Duplicati**.

### Prova de concepte
Creareu una màquina virtual **Windows 11** amb dos discos:
  - Un per instal·lar el sistema operatiu.
  - Un secundari de **10 GB** per emmagatzemar les còpies de seguretat.
Per simular la part de Google Drive, useu un compte que no sigui el d’escola (podeu crear un compte específic per l’activitat).
Es desitja fer còpies de seguretat del perfil de l’usuari:
  - Cada **hora** al disc secundari.
  - A les **18:00** a Google Drive.

### Tasques
1. Documenteu el procediment d’instal·lació de **Duplicati**.
2. Configureu els plans de còpies i observeu el funcionament.
3. Afegiu arxius a les carpetes de l’usuari, especialment a **Documents**.
4. Esborreu el contingut de **Documents** i procediu a fer una restauració des del disc secundari.
5. Comproveu com podeu fer una restauració des de la còpia que teniu emmagatzemada al **cloud**.

---

## Part 2: Còpia seguretat servidor Linux

Per fer les còpies del servidor Linux la solució proposada pel vostre responsable és **Duplicity**, que permet fer còpies tant contra un mitjà local com un servidor remot. Combinat amb el programador de tasques (**cron**) es poden implementar les polítiques de còpia que es desitgin.

### Prova de concepte
Usareu una màquina virtual amb **Ubuntu Server** instal·lat i li afegireu un segon disc de **10 GB** que simularà una unitat auxiliar.

#### Passos:
1. Inicialitza i formata en format **xfs**. Com simula una unitat externa, es muntarà manualment a /media/backup (primer cal crear la carpeta).
2. Instal·la **duplicity**.
3. Crea un parell d’usuaris més al sistema de manera que tinguin carpeta personal. Crea **4 arxius de 10 MB** a la carpeta home del teu usuari.
4. Fes una còpia de seguretat de la carpeta /home.
5. Esborra els arxius i fes un **restore** per comprovar com es recuperen els arxius.
6. Afegeix un nou arxiu de **4 MB** i fes una nova còpia. Observa com ara ha fet una còpia **incremental**.
7. Desmunta la unitat de backup.

---

### Automatització amb scripts i cron
Un aspecte molt important a nivell de seguretat és que la unitat de backup ha d’estar per defecte desmuntada. El primer pas sempre serà muntar la unitat i el darrer desmuntar-la, un cop s’ha fet la còpia.

#### Tasques:
1. Crea un script anomenat **fullbackup.sh** que realitzi la còpia completa de la carpeta /home i l’emmagatzemi al volum muntat.  
   - Usa la variable d’entorn PASSPHRASE (per donar valor a una variable d’entorn cal afegir a l’script una línia amb export PASSPHRASE=contrasenya) per no haver d’escriure la passphrase en el moment de l’execució.
   - Recorda donar permisos d’execució a l’script.
2. Programa al **cron** com a root l’execució de l’script els **diumenges a les 23:00**.
3. Crea un segon script anomenat **incrementalbackup.sh** que realitzi còpies incrementals de la mateixa carpeta que abans.  
   - Heu de fixar el valor de la variable PASSPHRASE igual que al punt anterior i donar permisos d’execució a l’script.
4. Programa al **cron** l’execució d’aquest script com a root de **dilluns a dissabte a les 23:00**.

---

[Guia Server Linux](LinuxServer.md)
[Guia Windows](Windows.md)
