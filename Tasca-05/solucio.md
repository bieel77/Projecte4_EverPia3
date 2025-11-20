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



