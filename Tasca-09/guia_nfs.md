# Tasca 09: Servidor NFS

## Procés instal·lació Ubuntu Server

### En primer lloc, li fiquem un nom a la màquina i li assignem la ISO d'Ubuntu Server, i marquem la casella que diu "Skip Unattended Installation", clickem "Finish" i obrim la màquina

<img width="733" height="574" alt="image" src="https://github.com/user-attachments/assets/d6c5b39b-c6e2-4942-8c83-e480840dda04" />

### Després marquem l'idioma que vulguem

<img width="839" height="493" alt="image" src="https://github.com/user-attachments/assets/eaca6afd-fbc9-4ad9-947d-43b9701d1777" />

### Seleccionem l'idioma de teclat també i seguim

<img width="954" height="750" alt="image" src="https://github.com/user-attachments/assets/c07220b2-a58d-40cb-96e2-bb09d71aa59c" />

### Marquem les següents opcions i premem "Hecho"

<img width="960" height="758" alt="image" src="https://github.com/user-attachments/assets/c92beb96-9d83-457c-8921-48d5b5d3808a" />


### "Hecho"

<img width="959" height="754" alt="image" src="https://github.com/user-attachments/assets/aeaad366-8558-46a3-bf68-91bcbf8892c6" />

### No fiquem ninguna adreça proxy i premem "Hecho"

<img width="957" height="757" alt="image" src="https://github.com/user-attachments/assets/76c69d32-a1c9-4bc6-8239-6aa3590e74be" />

### Esperem una mica i premem a "Hecho" per continuar

<img width="957" height="750" alt="image" src="https://github.com/user-attachments/assets/083c243b-776f-4e79-87e4-0eb8173b338c" />

### Marquem les següents opcions i seleccionem "Hecho" per seguir

<img width="960" height="755" alt="image" src="https://github.com/user-attachments/assets/08258c94-5ed3-463c-84d9-bc535a32a367" />

### Marquem "Hecho" també i "Continuar"

<img width="957" height="750" alt="image" src="https://github.com/user-attachments/assets/d14f128c-e7b8-4de1-af18-3a456d93bd18" />

<img width="585" height="209" alt="image" src="https://github.com/user-attachments/assets/5dc12bdb-8a62-44e1-b952-e5a8443d7bab" />

### Apliquem la següent informació establint la contrasenya que vulguem i premem a "Hecho"

<img width="961" height="751" alt="image" src="https://github.com/user-attachments/assets/5a6c5f18-6d50-4e11-a431-5de7f5d2de4b" />

### Marquem la següent opció i a "Continuar"

<img width="955" height="752" alt="image" src="https://github.com/user-attachments/assets/1315f4a4-2e2f-4590-a3a4-d4c0d1f296ee" />

### No marquem l'opció de OpenSSH si no volem fer servir el SSH (es pot instalar més endavant en comanda) i premem "Continuar"

<img width="957" height="754" alt="image" src="https://github.com/user-attachments/assets/30f77afa-2f73-4d5a-b99c-9642bcdba451" />

### No marquem ninguna opció i premem "Hecho" i esperem a que s'acabi d'instal·lar

<img width="956" height="755" alt="image" src="https://github.com/user-attachments/assets/d95163b0-ae65-467c-9381-ca20fb2d29bc" />

<img width="957" height="781" alt="image" src="https://github.com/user-attachments/assets/a624d713-5480-41d4-b76c-76059a019355" />

### Seleccionem a "Reiniciar Ahora"

<img width="960" height="790" alt="image" src="https://github.com/user-attachments/assets/a4d88c59-3ce2-454b-95ba-4befb3886e0b" />

### Li donem a ENTER per seguir amb l'execució i esperem a que es obri la màquina

<img width="962" height="798" alt="image" src="https://github.com/user-attachments/assets/548728d6-20a9-461d-a84a-53771d33e714" />

### I ja estaria l'instal·lació feta

<img width="881" height="508" alt="image" src="https://github.com/user-attachments/assets/e794c41b-7b29-4364-9a76-2a1c8dc146e0" />

## Guia NFS

### Abans d'obrir les màquines fiquem les interfícies de xarxa en NAT i Host-Only

<img width="857" height="486" alt="image" src="https://github.com/user-attachments/assets/70b08955-79c6-4907-a861-6505b8531f21" />

<img width="858" height="487" alt="image" src="https://github.com/user-attachments/assets/25b1b832-a739-4d29-8021-4519dabea3c2" />

### Primer de tot en la màquina servidor actualitzem amb la següent comanda:

```bash
sudo apt upgrade && sudo apt update
```

<img width="439" height="33" alt="image" src="https://github.com/user-attachments/assets/d993048a-e3e0-4b15-a467-cfa3f39d0f1c" />

## Fase 2

### En la màquina del servidor començem creant els grups: devs i admins

```bash
sudo groupadd devs
sudo groupadd admins
```

<img width="309" height="32" alt="image" src="https://github.com/user-attachments/assets/1c2130d4-bde6-48a6-bea5-43fa12293f08" />

### Un cop creats creem ara els usuaris, de moment el de dev01 que pertanyerà al grup devs

```bash
sudo useradd -G devs -m -s /bin/bash dev01
```

<img width="481" height="13" alt="image" src="https://github.com/user-attachments/assets/28a73013-5b0e-4662-b21c-a632fd5eb72b" />

### Ara el mateix amb admin01 al grup admins

```bash
sudo useradd -G admins -m -s /bin/bash admin01
``` 

<img width="533" height="14" alt="image" src="https://github.com/user-attachments/assets/352af637-a8fc-44f5-90a0-fdc80aa3768b" />

### I a la màquina física instal·lem la següent aplicació:

<img width="1033" height="298" alt="image" src="https://github.com/user-attachments/assets/dc8b9bd1-ccf7-4c04-b1b2-538b2eff5870" />

### I creem els usuaris dev01 i admin01

<img width="736" height="424" alt="image" src="https://github.com/user-attachments/assets/e8a5d042-6dc7-4ba5-a56d-d29356d08b74" />

### Posteriorment creem el directori per els projectes de desenvolupament

```bash
sudo mkdir /srv/nfs/dev_projects -p
```

<img width="458" height="17" alt="image" src="https://github.com/user-attachments/assets/d5cfc500-958e-427f-93b3-f09d44299168" />

### I ara creem el directori per les eines d'administració

```bash
sudo mkdir /srv/nfs/admin_tools
```

<img width="400" height="16" alt="image" src="https://github.com/user-attachments/assets/f0f158ee-7f12-4679-aec4-6c2f6bb457db" />

 ### Ara fiquem la següent comanda perquè tingui propietat

 ```bash
sudo chown root:devs /srv/nfs/dev_projects
```

<img width="485" height="16" alt="image" src="https://github.com/user-attachments/assets/f608cde3-fab6-4334-bdf5-96c0eb031a41" />

### El mateix però amb l'altre carpeta

```bash
sudo chown root:admins /srv/nfs/admin_tools
```

<img width="494" height="18" alt="image" src="https://github.com/user-attachments/assets/e70974a9-c295-4a68-80bf-4d0a9daa8cc2" />

### Ara per assignar els permisos perquè tingui control total al grup

```bash
sudo chmod -R 770 /srv/nfs/dev_projects
```

<img width="465" height="17" alt="image" src="https://github.com/user-attachments/assets/319d5bd0-067a-4382-b40f-1ba6ee2e7325" />

### El mateix però amb l'altre grup

```bash

sudo chmod -R 770 /srv/nfs/admin_tools
```

<img width="444" height="20" alt="image" src="https://github.com/user-attachments/assets/0397619b-c580-4a1b-bc35-988722a050ed" />

### I comprovem els permisos de les carpetes amb les següents comandes:

```bash
ls -ld /srv/nfs/admin_tools
```
```bash
ls -ld /srv/nfs/dev_projects
```

<img width="521" height="86" alt="image" src="https://github.com/user-attachments/assets/14bfbae7-904b-4ee7-8334-1da24f9bf030" />

### Ara haurem d'instal·lar el servidor NFS aplicant la següent comanda:

```bash
sudo apt install nfs-kernel-server
```

<img width="959" height="705" alt="image" src="https://github.com/user-attachments/assets/04280f5b-3442-4a31-84eb-f55c1226da53" />

### (Usuaris i grups creats, amb cada usuari al seu grup)

<img width="353" height="92" alt="image" src="https://github.com/user-attachments/assets/830a8eb1-2ac1-4233-8caa-c0ffb0a93e30" />

## Fase 3





