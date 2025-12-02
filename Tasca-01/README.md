# T01: DRP — Còpies de Seguretat  
## Estudi de cas client (treball cooperatiu)

---

## **Introducció**
La primera hora el vostre responsable de seguretat us presenta el tema de les còpies de seguretat a partir d’un material didàctic. A continuació, caldrà que treballeu els aspectes del tema i ho fareu mitjançant una dinàmica cooperativa.

---

## **Presentació del cas client**

**"Muntatges i Serveis Tècnics SL"** és una petita empresa dedicada a la instal·lació i manteniment d'equips industrials.

### **Infraestructura Tècnica**
- **Servidor de Fitxers (Ubuntu Server)**: Conté tota la documentació crítica:
  - **Documents de Projectes**: Plànols, especificacions tècniques (300 GB, creixement moderat).
  - **Bases de Dades (Comptabilitat i Clients)**: Crítiques i d'ús diari (20 GB, canvi constant).
  - **Carpetes Personals dels Usuaris**: Per a la feina diària (100 GB).
- **10 Equips Clients (Windows 10/11)**: Els usuaris treballen principalment amb fitxers del servidor, però alguns tècnics guarden temporalment informes i documents importants a *Documents*.
- **Connexió a Internet**: Fibra òptica de 600 Mbps (simètrica).

### **Requisits de Recuperació**
- **RTO (Temps de Recuperació)**: Les dades de Comptabilitat/Clients han d'estar disponibles en menys de 4 hores.
- **RPO (Pèrdua de Dades Admesa)**:  
  - Dades generals → es pot admetre una pèrdua màxima de 24 h  
  - Comptabilitat/Clients → màxim 4 h de pèrdua de treball
- **Retenció**: Històric d’almenys **1 mes**.

---

# **Fase 1: Treball individual**

De forma individual, heu de donar resposta a les preguntes següents basant-se en el cas pràctic:

### **1. Què copiar? (Priorització)**
Quines són les dades més crítiques del servidor?  
Cal fer còpia dels 10 equips clients? Justifica-ho.

---

### **2. Periodicitat i Tipus de Còpia**
Proposa un calendari bàsic per a la setmana (Diari/Setmanal/Mensual) i quin tipus de còpia aplicaràs (Completa, Diferencial, Incremental) per a les dades crítiques.

---

### **3. Mitjans i Ubicació**
Quin tipus de mitjà de còpia utilitzaries (Discs durs externs, NAS, Cloud, Cintes)?  
On s'hauria de guardar físicament la còpia més recent segons la **Regla 3-2-1**?

---

# **Fase 2: Treball per parelles**

Treballant per parelles:

### **1. Discussió i Consens**
Comparau les vostres respostes individuals (Fase 1).

### **2. Elaboració d'una Proposta Unificada**
Heu de consensuar i dissenyar el vostre propi **Esquema 3-2-1** (3 còpies, 2 mitjans, 1 fora de lloc).

| Element | Proposta de la Parella | Justificació |
|--------|-------------------------|--------------|
| Dades Crítiques |  |  |
| Periodicitat (BD) |  |  |
| Tipus de Còpia (BD) |  |  |
| Mitjà 1 (Local) |  |  |
| Mitjà 2 (Extern) |  |  |

---

# **Fase 3: Treball en grup**

### **1. Debat i Selecció**
Cada parella presenta el seu esquema.  
El grup debat pros i contres de cada proposta (cost, temps de recuperació, seguretat, simplicitat).

### **2. Disseny de la Política Final**
El grup ha de redactar la **Política de Còpies de Seguretat Definitiva** per a l'empresa *Muntatges i Serveis Tècnics SL*.

---

# **Document Final (Fase 3)**

El grup ha de generar un document amb els punts següents resolts:

---

## **1) Dades Objecte de Còpia**
Quines dades es copien i amb quina freqüència  
(separant Servidor/Clients i dades crítiques/no crítiques).

---

## **2) Cronograma Setmanal Detallat**

| Dia | Dades (Ex: BD) | Tipus de Còpia | Mitjà |
|-----|----------------|----------------|-------|
| Dilluns |  |  |  |
| Dimarts |  |  |  |
| ... |  |  |  |
| Diumenge |  |  |  |

---

## **3) Elecció de Mitjans i Ubicació (Regla 3-2-1)**

- **Mitjà 1 (Local)**: Quin mitjà concret (p. ex., Disc dur USB, NAS...).  
- **Mitjà 2 (Extern)**: Quin mitjà (Cloud, LTO...) i quin proveïdor (Azure, Google Cloud, etc.).  
- **Ubicació Fora de Lloc**: On es guarda la còpia externa i qui en és responsable.

---

## **4) Estratègia de Recuperació (RTO/RPO)**

Com es garanteix que les dades de Comptabilitat/Clients compleixen amb:
- **RPO ≤ 4 hores**
- **RTO ≤ 4 hores**

---

# **Materials i links de suport**
- Moodle 0226 Seguretat Informàtica. RA2.AA3 Còpies  
- INCIBE — *Copias de seguridad. Una guía de aproximación para el empresario.*  
- Xataka — *Backup 3-2-1, el método definitivo para mantener a salvo tus datos.*  
  (YouTube, setembre 2017)  
  https://youtu.be/PM_M4Iz6I4o?si=F7DRyDDTZE3hjWn8

---
## Entregues
[Treball 1: Individual](solucio_individual.md)
---
[Treball 2: Individual](solucio_parelles.md)
---
[Treball 3: Individual](solucio_grupal.md)
---
