# Fase 1: Treball individual

De forma individual, heu de donar resposta a les següents preguntes basant-se en el cas pràctic:

---

### 1. Què copiar? (Priorització)
**Pregunta:** Quines són les dades més crítiques del servidor? Cal fer còpia dels 10 equips clients? Justifica-ho.

**Resposta:**  
Les dades més crítiques del servidor són les bases de dades de **Comptabilitat** i **Clients**, seguides dels documents de **projectes** i les **carpetes personals** dels usuaris.  
No cal copiar completament els 10 equips clients; només és necessari fer còpia de la carpeta *Documents* dels tècnics que hi guardin informació important.

---

### 2. Periodicitat i Tipus de Còpia
**Pregunta:** Proposa un calendari bàsic per a la setmana (Diari/Setmanal/Mensual) i quin tipus de còpia aplicaràs (Completa, Diferencial, Incremental) per a les dades crítiques.

| Freqüència                        | Tipus de Còpia | Funció Principal |
|----------------------------------|----------------|------------------|
| Completa (Dominical/Mensual)     | Completa       | Serveix com a base per a la retenció mensual i proporciona la restauració més ràpida. |
| Diària (Dilluns a Dijous)        | Incremental    | Garanteix la còpia més ràpida possible, guardant només els canvis respecte el dia anterior. |
| Setmanal (Divendres)             | Diferencial    | Simplifica la restauració de final de setmana, ja que només necessita la còpia completa més aquesta. |

---

### 3. Mitjans i Ubicació
**Pregunta:** Quin tipus de mitjà de còpia utilitzaries (Discs durs externs, NAS, Cloud, Cintes)? On s'hauria de guardar físicament la còpia més recent (Regla 3-2-1)?

**Resposta:**  
S'utilitzaria una combinació de **NAS (Network Attached Storage)** i **Cloud Storage**.  
El NAS actua com a mitjà primari per la seva rapidesa dins la xarxa local, essencial per complir un RTO inferior a 4 hores.  
El Cloud serveix com a ubicació *off-site* per complir la **Regla 3-2-1** i gestionar la retenció mensual.

La còpia més recent s'ha de guardar al **NAS local**, ja que permet iniciar la restauració immediatament sense dependre del temps de descàrrega des d’Internet.

---

