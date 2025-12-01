# T05: Accés Remot SSH

### Abans d'iniciar la màquina Windows activem el segon adaptador i el fiquem en "Host Only"

<img width="688" height="304" alt="image" src="https://github.com/user-attachments/assets/d2159fc8-62aa-4f4e-956c-20ca4cc96049" />

### Primer de tot instal·lem el ssh

``` bash
sudo apt install ssh
```

<img width="315" height="17" alt="image" src="https://github.com/user-attachments/assets/e94dbc2b-8162-4620-95f3-767dca31b30d" />

<img width="897" height="663" alt="image" src="https://github.com/user-attachments/assets/a7f19a97-7503-4537-855b-27e09d2c381b" />

### Configurem la interfície de hostonly

<img width="181" height="159" alt="image" src="https://github.com/user-attachments/assets/43330f19-d25a-434c-876c-1fa2b2cdb111" />

### I apliquem els canvis amb aquesta comanda:

```bash
sudo netplan apply
```

### Després per mirar les IP's que s'estan usant en el Linux pots escriure les següents comandes:

``` bash
ip addr show
```
o també

``` bash
ip a
```
<img width="752" height="338" alt="image" src="https://github.com/user-attachments/assets/955d4201-7e9f-455b-a546-8bc08e9bfdad" />

### Després desde la màquina Windows fiquem la següent comanda per fer la comprovació ssh

```bash
ssh usuari@IP
```

<img width="725" height="571" alt="image" src="https://github.com/user-attachments/assets/749b5c2e-77f2-4e94-947e-5ef87f476cb0" />

### Ara introduïm aquesta comanda per veure que la màquina Windows està connectada amb la màquina Linux

```bash
hostname
```

<img width="247" height="41" alt="image" src="https://github.com/user-attachments/assets/64f97a01-4ded-476b-b3d4-de91d69d477d" />

### Ara haurem d'establir una contrasenya per l'usuari root, abans d'acceddir al arxiu de configuració.

```bash
sudo passwd root
```
<img width="299" height="63" alt="image" src="https://github.com/user-attachments/assets/97f054d0-a7ed-44e6-a8ec-defe096958ac" />

### Introduïm la següent comanda per accedir al arxiu ssh config.

```bash
sudo nano /etc/ssh/shhd_config
```
I al apartat de baix del arxiu fiquem AllowUsers (usuari).

<img width="757" height="742" alt="image" src="https://github.com/user-attachments/assets/a3148b78-f4b0-429f-b76c-d1442c16c336" />

I guardem la configuració.

### Ara per fer el login en local amb l'usuari root escriurem lo següent:

```bash
su - root
```
<img width="225" height="49" alt="image" src="https://github.com/user-attachments/assets/4caa0616-7e72-4fa0-9f00-a6a5326128bd" />

### Posteriorment escriurem la segúent comanda desde la terminal de la màquina Windows:

```bash
ssh root@192.168.56.102
```
(On la IP has d'introduïm la teva)
I veuras que et denega la contrasenya.

<img width="458" height="75" alt="image" src="https://github.com/user-attachments/assets/7ea36b36-4d87-4381-bdf9-172e91988d9f" />

### Ara per generar codis RSA, s'haurà d'introduir aquesta comanda, i haurem de donar-li ENTER fins que es completi.

```bash
ssh-keygen -t rsa
```
<img width="681" height="420" alt="image" src="https://github.com/user-attachments/assets/24086fcb-b3e9-46aa-b540-b9bcda7b0158" />

### Escrivim aquesta comanda per veure els arxius necessitats.

```bash
ls .\.ssh\
```
<img width="611" height="300" alt="image" src="https://github.com/user-attachments/assets/0c7c67dc-6f07-4b15-b801-498ea1d6f488" />

### Per passar el pub d'una màquina Linux al Windows es fa amb la següent comanda:

```bash
scp .\.ssh\id_rsa.pub usuari@192.168.56.102:/home/usuari
```
<img width="672" height="85" alt="image" src="https://github.com/user-attachments/assets/49bcd57a-1e54-4356-b5ce-2c96932660aa" />
<img width="684" height="291" alt="image" src="https://github.com/user-attachments/assets/87d575a6-81c5-4dcb-b7dd-c06f735b8cec" />


### Ara desde la màquina Linux, fiquem aquesta comanda per crear l'arxiu a la carpeta ssh.

```bash
touch .ssh/authorized_keys
```
<img width="348" height="27" alt="image" src="https://github.com/user-attachments/assets/9a10a069-8f3a-480e-8169-f470cff1fe16" />

### Amb la següent comanda copiem la clau de l'arxiu id_rsa.pub 

```bash
cat id_rsa.pub >> .ssh/authorized_keys
```
<img width="448" height="33" alt="image" src="https://github.com/user-attachments/assets/24f5c8ae-3582-46cd-a810-886f4f1516aa" />

### Ara en la màquina Windows fem un ssh a la ip per veure si ens accedeix.

```bash
ssh usuari@192.168.56.102
```
<img width="737" height="641" alt="image" src="https://github.com/user-attachments/assets/f71328d1-636c-45da-97d5-14908646b9c4" />


### Entrem a configuració, després Sistema i a característiques opcionals per permetre al equip fer canvis.

<img width="781" height="619" alt="image" src="https://github.com/user-attachments/assets/994a1685-faea-433a-8ad2-e805a75d15ec" />

### Ara a "ver característiques".

<img width="784" height="615" alt="image" src="https://github.com/user-attachments/assets/0966d60d-ef3c-4c62-8128-bdd585d99c1d" />

### Després a "Ver las característiques disponibles"

<img width="533" height="616" alt="image" src="https://github.com/user-attachments/assets/29cff0b3-3b7f-4e34-82ed-124a7d6aefe8" />

### Un cop aqui busquem OpenSSH i a afegir.

<img width="524" height="615" alt="image" src="https://github.com/user-attachments/assets/8cea637d-3bb0-40a6-9562-adcb57b2d80e" />









