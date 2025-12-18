# Guia Linux: Còpies de seguretat

### Creem el disc secundari

<img width="617" height="416" alt="image" src="https://github.com/user-attachments/assets/1278045b-1c22-4a5f-aa57-e8efd466aa00" />

### Premem a "Crea"

<img width="949" height="367" alt="image" src="https://github.com/user-attachments/assets/0e1b79e6-7ef4-4cff-b1e1-2ef3d7dd9c0d" />

### Li assignem 10 GB d'espai

<img width="521" height="349" alt="image" src="https://github.com/user-attachments/assets/46ecef8f-d030-457c-aa69-670b41777cdd" />

### I un cop aqui seleccionem el disc i premem a "Choose", i ja tindriem el disc creat

<img width="954" height="791" alt="image" src="https://github.com/user-attachments/assets/def2e207-909b-4e36-b72b-6e34dcbe0d1e" />

## 1. Formateja amb XFS i muntatge manualment

### Comencem l'activitat creant la partició

```bash
sudo fdisk /dev/sdb
```

### Primer fiquem la "n" per indicar que volem fer partició, després "p" per seleccionar primària i ENTER per seleccionar configuració per defecte i per acabar "w" per guardar i ja haurem guardat la partició.

<img width="816" height="493" alt="image" src="https://github.com/user-attachments/assets/8a431cfc-042d-4423-b8a8-0e8b4d5756d3" />

### Ara fem el format XFS, amb la següent comanda:

```bash
sudo mkfs.xfs /dev/sdb1
```
<img width="731" height="208" alt="image" src="https://github.com/user-attachments/assets/26234ad4-362f-474a-b5a1-50f4d33d8c09" />

### Un cop formatejat, creem la carpeta on ficarem el punt de muntatge

```bash
sudo mkdir -p /media/backup
```
### I fem el muntatge manualment

```bash
sudo mount /dev/sdb1 /media/backup
```

<img width="523" height="38" alt="image" src="https://github.com/user-attachments/assets/243d1f53-f13a-46ef-b478-8f9f7f953052" />

## 2. Instal·lació de Duplicity

### Instal·lem Duplicity

```bash
sudo apt install duplicity
```

<img width="921" height="421" alt="image" src="https://github.com/user-attachments/assets/47316784-11e2-4e43-b194-8aac53d37c23" />

### I comprovem que s'ha instal·lat correctament

<img width="341" height="33" alt="image" src="https://github.com/user-attachments/assets/102d6c60-b192-4a3e-bcbb-10f14ecd27f0" />

## 3. Creació d'usuaris i arxius

### Creem uns usuaris amb la seva carpeta personal

```bash
sudo useradd -m -s /bin/bash usuari2
sudo useradd -m -s /bin/bash usuari3
```

### I comprovem que els hem creats correctament

```bash
grep -E "usuari2|usuari3" /etc/passwd
````

<img width="539" height="58" alt="image" src="https://github.com/user-attachments/assets/9b6d6908-d6a9-42bf-a7a4-6d5a4f45fbd7" />

### I creem les contrasenyes pels usuaris: (usuari2)

```bash
sudo passwd usuari2
```
<img width="365" height="76" alt="image" src="https://github.com/user-attachments/assets/1e85522a-411f-4368-b777-f3b5456b85ac" />

### I ara pel usuari 3:

```bash
sudo passwd usuari3
```
<img width="353" height="79" alt="image" src="https://github.com/user-attachments/assets/a6937bf7-eec1-42a8-a26d-aade3d88f143" />

### Creem els arxius de 10 MB a la carpeta

```bash
fallocate -l 10MB arxiu11
fallocate -l 10MB arxiu22
fallocate -l 10MB arxiu33
fallocate -l 10MB arxiu44
```

<img width="388" height="115" alt="image" src="https://github.com/user-attachments/assets/74fe8f74-0a8c-4492-99e1-b3ec950c8b0e" />

## 4. Còpia de seguretat de la carpeta /home.

### Fem la còpia amb la següent comanda:

```bash
sudo duplicity full /home/ file:///media/backup/
```
<img width="623" height="419" alt="image" src="https://github.com/user-attachments/assets/9edac37f-c5b3-4d9e-bab4-186a5b2db085" />

### I amb la següent comanda podem veure que s'han creat els arxius a la còpia, (abans hem de fer; cd /media/backup per poder veure els arxius)

```bash
ls
```

<img width="487" height="79" alt="image" src="https://github.com/user-attachments/assets/465d608b-146c-4701-ad24-d316ef1e8181" />

## 5. Restauració 

### Comencem esborrant els arxius amb la següent comanda:

```bash
rm arxiu*
```

### I fem la restauració, abans fes: cd /media/backup i escriu la comanda

```bash
sudo duplicity restore file:///media/backup/ /home/usuari
```

<img width="801" height="192" alt="image" src="https://github.com/user-attachments/assets/ee1bd180-58c3-4656-bc64-33f35f32ffb4" />


### I veiem que s'han restaurat correctament:

<img width="333" height="39" alt="image" src="https://github.com/user-attachments/assets/9ee6ad3a-5055-4650-90a9-42981067ef5c" />

## 6. Afegir un nou arxiu de 4Mb

### Afegim el nou arxiu

```bash
fallocate -l 4MB arxiu55
```

<img width="449" height="56" alt="image" src="https://github.com/user-attachments/assets/9ecb4c9b-73d4-471a-9c62-c92bed28f494" />

### Fem una altre còpia on només detecta un arxiu nou i fa una còpia incremental

```bash
sudo duplicity /home/ file:///media/backup/
```

<img width="927" height="455" alt="image" src="https://github.com/user-attachments/assets/e25897fb-ffae-4b93-8b54-c3b893b9a1c1" />

### I desmuntem la unitat del backup

```bash
sudo umount /media/backup
```

## 7. Creem l'script fullbackup.sh

```bash
!/bin/bash

export PASSPHRASE="usuariusuari1234"

mount /dev/sdb1 /media/backup

duplicity full /home file:///media/backup/homebackup

umount /media/backup
```

### I donem els permisos d'execució

```bash
sudo chmod +x incrementalbackup.sh
```
<img width="481" height="31" alt="image" src="https://github.com/user-attachments/assets/bf63a1d0-fcb7-4974-a632-0eaa2df72787" />

## 8. Programació del clon

### I programem perque executi el backup de dilluns a dissabte a les 23h

```bash
sudo crontab -e
```

### I premem  "1" per entrar al arxiu, i introduïm la següent informació a la part d'abaix del arxiu

<img width="699" height="533" alt="image" src="https://github.com/user-attachments/assets/46af9750-2661-4a87-a680-32cd5f573e60" />




