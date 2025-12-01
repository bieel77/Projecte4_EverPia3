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

### Ara vas al Firewall i l'apaguem, per fer això busquem "Firewall" entrem i accedim a "red pública" i ho desactivem.

<img width="777" height="613" alt="image" src="https://github.com/user-attachments/assets/3ce6979f-43e3-4563-bce4-632e0437e322" />

<img width="562" height="460" alt="image" src="https://github.com/user-attachments/assets/6c4281cc-4094-4705-9ef5-a02106769abe" />

### Tornem a entrar a Powershell però aquest cop en Administrador i escrivim la següent comanda:

```bash
Start-Service sshd
```
<img width="358" height="42" alt="image" src="https://github.com/user-attachments/assets/c00f9514-7d94-4ad7-abcf-8b813705f25b" />

### I després amb la següent comanda, farem que el servei també s'activi, al iniciar la màquina.

```bash
Set-Service -Name sshd -StartupType "Automatic"
```
<img width="578" height="38" alt="image" src="https://github.com/user-attachments/assets/7c3a0df6-a8c7-40c7-80ff-2849585aea45" />

### Ara escrivim ipconfig per veure la IP que esta usant Host-Only.

```bash
ipconfig
```
<img width="626" height="386" alt="image" src="https://github.com/user-attachments/assets/d4deb7c0-d2df-442e-a49f-fbf0f7e723b6" />

### Ara farem ping desde la màquina Linux a la màquina Windows per veure so hi ha connexió

<img width="508" height="139" alt="image" src="https://github.com/user-attachments/assets/e9c796b6-5073-440e-91da-433e2999db4e" />

### Com ens indica que fa connexió ens connectem a la màquina Windows desde la màquina Linux

<img width="325" height="33" alt="image" src="https://github.com/user-attachments/assets/7dc10632-861a-4301-826a-fe14f9142605" />

## Creació Túnel

### Fiquem la següent comanda per començar a fer la creació del túnel

```bash
ssh -D 9876 usuari@192.168.56.102
```
<img width="651" height="477" alt="image" src="https://github.com/user-attachments/assets/2e57fd4c-dad4-4935-83ce-9297c2590e46" />

### Ara obrim el panel de control i ens dirigim a "Redes e Internet" per configurar-lo en proxy.

<img width="775" height="578" alt="image" src="https://github.com/user-attachments/assets/21cb45a5-85ce-4d5d-a78f-91d9621872ea" />

### I ara a "Opciones de Internet"

<img width="771" height="549" alt="image" src="https://github.com/user-attachments/assets/edeb276f-e25f-4846-9b31-b91aa5ef31cf" />

### Un cop aqui ens ubiquem a "Conexiones" i després a "Configuración de LAN"

<img width="408" height="566" alt="image" src="https://github.com/user-attachments/assets/59167c4f-4f6e-4e15-81f9-455a9417caee" />

### Ara a "Opciones avanzadas"

<img width="367" height="325" alt="image" src="https://github.com/user-attachments/assets/afe5dff2-56fa-4f1b-97c5-c7ab11fb5a7d" />

### I apliquem la següent configuració i "Aceptar".

<img width="379" height="421" alt="image" src="https://github.com/user-attachments/assets/bd644d9d-e1fe-40d2-ac88-73d48c91bd28" />

### I per últim instal·lem el wireshark al Windows per veure que el túnel funciona correctament.

