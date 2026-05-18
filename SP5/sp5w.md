# Autorització i auditories en Windows Server

## Introducció

En aquesta pràctica es treballa la configuració d’auditories i autorització en Windows Server. L’objectiu és entendre com controlar els accessos al sistema, registrar activitats dels usuaris i analitzar els esdeveniments generats mitjançant el Visor d’esdeveniments.

Les auditories permeten registrar accions importants com:

- Inicis de sessió correctes o fallits
- Accés a carpetes i fitxers
- Creació i eliminació d’usuaris
- Execució de processos

Aquest sistema és essencial per a la seguretat i el control d’un servidor Windows.

---

# Autorització en Windows

L’autorització serveix per controlar què poden fer els usuaris dins del sistema.

Mitjançant permisos es pot decidir:

- Qui pot llegir fitxers
- Qui pot modificar carpetes
- Qui pot eliminar arxius
- Qui només té accés de lectura

Aquests permisos es configuren des de:

```text
Propietats → Seguretat
```

També es poden aplicar directives de seguretat locals per controlar el comportament dels usuaris i del sistema.

---

# Què són les auditories

Les auditories registren activitats importants del sistema per poder controlar i detectar possibles accessos no autoritzats.

Exemples:

- Qui inicia sessió
- Qui accedeix a una carpeta
- Qui modifica un arxiu
- Qui crea o elimina usuaris

Els resultats es poden consultar al:

```text
eventvwr.msc
```

Alguns Event ID importants:

| Event ID | Descripció |
|---|---|
| 4624 | Inici de sessió correcte |
| 4625 | Inici de sessió fallit |
| 4663 | Accés a objectes |
| 4688 | Procés iniciat |
| 4689 | Procés finalitzat |
| 4720 | Usuari creat |
| 4722 | Usuari activat |
| 4725 | Usuari desactivat |
| 4726 | Usuari eliminat |

---

# Part pràctica

# 1. Activar les polítiques d’auditoria

Primer obrim les directives de seguretat locals.

```text
Win + R → secpol.msc
```

Anem a:

```text
Directivas locales → Directiva de auditoría
```

Activem les opcions:

- Auditar eventos de inicio de sesión
- Auditar el acceso a objetos

Configurarem tant:

- Correcto
- Erróneo

## Captura 1

<img width="785" height="386" alt="image" src="https://github.com/user-attachments/assets/8fa8406f-72cc-4236-9ebe-924eb2c17edd" />

---

# 2. Verificar inici de sessió correcte

Iniciem sessió amb qualsevol usuari del sistema.

Després obrim:

```text
Win + R → eventvwr.msc
```

Ruta:

```text
Registros de Windows → Seguridad
```

Busquem l’Event ID:

```text
4624
```

Aquest event indica que l’inici de sessió ha estat correcte.

## Captura 2

<img width="959" height="933" alt="image" src="https://github.com/user-attachments/assets/594e53d6-784a-4eec-ae96-cc09867bb3b9" />

---

# 3. Crear carpeta per auditar accessos

Creem una carpeta nova.

Exemple:

```text
C:\Auditoria
```

Botó dret sobre la carpeta:

```text
Propiedades → Seguridad → Opciones avanzadas → Auditoría
```

Afegim l’usuari:

```text
Administrador
```

Permisos:

```text
Lectura
```

## Captura 3

<img width="763" height="511" alt="image" src="https://github.com/user-attachments/assets/0d22a3d1-cad4-4ee8-84c9-8a4acd187418" />

---

# 4. Afegir administrador amb control total

Afegim també:

```text
Administrador
```

Permisos:

```text
Control total
```

Això permetrà provar diferents accions dins la carpeta.

## Captura 4

<img width="763" height="511" alt="image" src="https://github.com/user-attachments/assets/5f06e8d8-f0df-43c0-b61c-af911102f41c" />

---

# 5. Generar Event ID 4663

Realitzem accions dins la carpeta:

- Crear fitxers
- Obrir fitxers
- Modificar arxius
- Eliminar fitxers

Després revisem:

```text
eventvwr.msc
```

Busquem:

```text
Event ID 4663
```

Aquest event indica accés a objectes.

## Captura 5

<img width="961" height="899" alt="image" src="https://github.com/user-attachments/assets/a8fc35e1-cf4d-4283-8744-a5dd5e0f238d" />

---

# 6. Auditar seguiment de processos

Tornem a:

```text
secpol.msc
```

Activem:

```text
Auditar el seguimiento de procesos
```

Opcions:

- Correcto
- Erróneo

## Captura 6

<img width="789" height="414" alt="image" src="https://github.com/user-attachments/assets/a144f2e2-d9ba-44b3-825f-e24ec867e99f" />

---

# 7. Generar Event ID 4688

Obrim un programa.

Exemple:

```text
Microsoft Edge
```

Després revisem el visor d’esdeveniments i busquem:

```text
4688
```

Aquest event indica que s’ha iniciat un procés.

## Captura 7

<img width="956" height="894" alt="image" src="https://github.com/user-attachments/assets/6f6c7939-b4b1-464e-a1e8-95738c6d6141" />

---

# 8. Generar Event ID 4689

Tanquem Edge des del:

```text
Administrador de tareas
```

Busquem ara:

```text
4689
```

Aquest event indica finalització d’un procés.

## Captura 8

<img width="957" height="891" alt="image" src="https://github.com/user-attachments/assets/bb1b062a-7b74-47b6-919b-8b7caa397b4a" />

---

# 9. Auditar administració de comptes

Tornem a:

```text
secpol.msc
```

Activem:

```text
Auditar la administración de cuentas
```

Opcions:

- Correcto
- Erróneo

## Captura 9

<img width="790" height="445" alt="image" src="https://github.com/user-attachments/assets/6bda16e2-3a4a-4429-95a4-0116105d3615" />

---

# 10. Crear un usuari nou

Creem un usuari nou des de:

```text
Administración de equipos → Usuarios y grupos locales
```

Exemple:

```text
UsuariProva
```

Després revisem el visor d’esdeveniments.

Events esperats:

| Event ID | Significat |
|---|---|
| 4720 | Usuari creat |
| 4722 | Usuari activat |

## Captura 10

<img width="955" height="904" alt="image" src="https://github.com/user-attachments/assets/6ea76802-0138-4367-a0d6-2e193ef38f94" />

## Captura 11

<img width="960" height="912" alt="image" src="https://github.com/user-attachments/assets/0fd74973-c651-4efd-a1e8-c4e6a1f9a034" />

---

# 11. Desactivar l’usuari

Desactivem l’usuari creat.

Busquem:

```text
4725
```

Aquest event indica que el compte ha estat desactivat.

## Captura 12

<img width="957" height="880" alt="image" src="https://github.com/user-attachments/assets/074783b9-56b7-45f1-ae3a-d51d01974dd2" />

---

# 12. Eliminar l’usuari

Eliminem l’usuari.

Després revisem:

```text
4726
```

Aquest event indica que el compte ha estat eliminat.

## Captura 13

<img width="957" height="883" alt="image" src="https://github.com/user-attachments/assets/26b194e0-04f4-4f03-9501-a48d499d59b0" />

---

# Conclusions

Les auditories de Windows Server permeten controlar i registrar activitats importants del sistema. Això ajuda a detectar accessos no autoritzats, comprovar accions dels usuaris i augmentar la seguretat del servidor.

Mitjançant el Visor d’esdeveniments es poden analitzar tots els esdeveniments generats i verificar si el sistema funciona correctament.

També és important no activar auditories innecessàries perquè poden afectar el rendiment del sistema.

---


# Supervisió i Diagnòstic del Rendiment a Windows Server

## 1. Fonaments de la Monitorització del Sistema

La **supervisió del sistema** és el procés d'avaluació en temps real dels recursos de programari i maquinari del servidor, com ara el processador (CPU), la memòria RAM, l'emmagatzematge (disc) i el trànsit de xarxa. 

A diferència d'una auditoria del sistema (que té un caràcter de control per registrar quins usuaris han fet accions concretes), la monitorització té un objectiu tècnic: descriure l'estat operatiu del servidor de manera instantània per anticipar incidències, localitzar colls d'ampolla o detectar aplicacions anòmales que absorbeixen massa potència.

Per dur a terme aquesta tasca, Windows Server 2022 compta amb dues utilitats fonamentals:

| Utilitat | Mètode d'accés | Profunditat de l'anàlisi |
| :--- | :--- | :--- |
| **Administrador de tasques** | `Ctrl + Shift + Esc` | Diagnòstic superficial i visualització ràpida. |
| **Monitor de recursos** | Ordre `resmon` (o des de l'Administrador de tasques) | Diagnòstic exhaustiu detallat per filtres i processos. |

---

## 2. Guia Pràctica d'Anàlisi Pas a Pas

### Pas 1: Diagnòstic inicial des de l'Administrador de tasques
En obrir la utilitat amb la combinació `Ctrl + Shift + Esc`, la pestanya de **Processos** ens mostra l'activitat general dividida per tipologies d'execució:
* **Aplicacions (3):** Programes en primer pla com l'`Administrador de tareas` (40 MB) i el `Server Manager` (57,6 MB).
* **Processos en segon pla (30):** Tasques del nucli de l'entorn com `AggregatorHost.exe`, `AntiMalware Definition Update` o l'`Experiencia de entrada de Windows`.

<img width="764" height="580" alt="image" src="https://github.com/user-attachments/assets/aedcdc5e-b217-44b3-8886-a884e3f7d416" />


### Pas 2: Diagnòstic del Processador (CPU)
A la secció **Rendimiento → CPU**, observem les mètriques d'activitat dels últims 60 segons:
* **Maquinari utilitzat:** Intel(R) Core(TM) i7-10700 @ 2,90 GHz
* **Taxa d'ús instantani:** 17%
* **Freqüència de rellotge:** 2,11 GHz
* **Mètriques d'execució:** 119 processos, 1.200 subprocessos (fils d'execució) i 43.000 identificadors.
* **Temps de funcionament acumulat:** 0:00:03:23
* **Arquitectura lògica:** 2 processadors virtuals (detectat com a entorn virtualitzat).

<img width="757" height="572" alt="image" src="https://github.com/user-attachments/assets/f0876cc5-01fc-4bce-80a8-a415e8c676b9" />


### Pas 3: Diagnòstic de la Memòria RAM
Mitjançant l'apartat **Rendimiento → Memoria**, s'avalua la capacitat d'emmagatzematge temporal:
* **Memòria física detectada:** 10,8 GB
* **En ús (dades comprimides):** 2,1 GB
* **Espai lliure immediat:** 6,5 GB
* **Memòria confirmada (total/límit):** 1,6 / 5,4 GB
* **Dades en memòria cau:** 4,3 GB
* **Bloc paginat / no paginat:** 237 MB / 125,4 MB

<img width="710" height="573" alt="image" src="https://github.com/user-attachments/assets/54d5bc2f-7b29-4c04-bf1a-34a731499124" />


### Pas 4: Diagnòstic de la Interfície de Xarxa
Navegant cap a **Rendimiento → Ethernet**, es visualitza el flux de dades de la targeta de xarxa:
* **Controlador actiu:** Intel(R) PRO/1000 MT Desktop Adapter
* **Trànsit de pujada (Enviament):** 0,0 Kbps
* **Trànsit de baixada (Recepció):** 0,0 Mbps
* **Ample de banda de la línia:** 11 Mbps
* **Configuració de xarxa:** IPv4 (`10.0.2.15`) i IPv6 (`fd17:625c:f037:2:3d:f43c:caf8:bb83`)

<img width="713" height="576" alt="image" src="https://github.com/user-attachments/assets/17cb9bef-189e-420d-98ad-8b70cf011a71" />


### Pas 5: Accés Avançat amb el Monitor de Recursos
Per a un nivell de detall superior, s'executa l'eina avançada prement `Windows + R` i teclejant `resmon`. Aquest panell ofereix un desglossament exhaustiu creuant dades de PID, serveis subjacents i interaccions amb el programari.

### Pas 6: Anàlisi de CPU Avançada (Monitor de Recursos)
Dins la pestanya de **CPU**, l'anàlisi es segmenta en dues capes (Ús total del processador: 35%):
1. **Processos en execució:**
   * `svchost.exe (netsvcs -p)` — PID 2664, amb 23 fils, consumint un **9,63% de CPU**.
   * `perfmon.exe` — PID 5816 (correspon a la mateixa finestra del monitor), amb un 7,28% de CPU.
   * `svchost.exe (LocalServiceNo...)` — PID 1264, requeriment de l'1,06%.
   * `SearchApp.exe` i `ShellExperienceHost.exe` — En estat de suspensió (0%).
2. **Serveis vinculats (Càrrega de serveis: 23%):**
   * `wuauserv` (Windows Update) — Vinculat al PID 2664, genera el major impacte amb un **9,63% de CPU**.
   * `mpssvc` (Cortafocs de Windows) — Vinculat al PID 1264, amb un consum de l'1,06%.

<img width="782" height="587" alt="image" src="https://github.com/user-attachments/assets/791e1f9c-f9e6-4803-8072-e991a9aed4f8" />


### Pas 7: Anàlisi de Memòria Avançada (Monitor de Recursos)
A la pestanya de **Memoria**, s'avalua el comportament de la RAM mitjançant el concepte de memòria privada:
* **Rànquing de processos per ús privat:**
   * `MsMpEng.exe` (Antivirus Windows Defender): 270.448 KB reservats (161.508 KB privats).
   * `dns.exe` (Servidor DNS): 130.892 KB reservats (120.676 KB privats).
   * `lsass.exe` (Seguretat local/Autenticació): 56.672 KB reservats (32.840 KB privats).
   * `dwm.exe` (Interfície gràfica de finestres): 35.420 KB reservats (31.460 KB privats).
* **Balanç del Maquinari:**
   * Total del sistema: 8997 MB
   * Consum real: 3289 MB
   * Marge lliure disponible: 2.483 MB
   * Emmagatzematge en memòria cau: 5926 MB
   * Memòria en espera: 5700 MB | Memòria lliure real: 410 MB

<img width="776" height="584" alt="image" src="https://github.com/user-attachments/assets/959434b7-a6a8-4220-83b8-25aa8cc493af" />


### Pas 8: Anàlisi de Disc Avançada (Monitor de Recursos)
Dins l'apartat de **Disco**, es monitoritzen els fluxes de lectura i escriptura:
* **Processos actius a l'emmagatzematge:**
   * `System` (PID 4): Lectura a 4.287 B/s i Escriptura a 5.762 B/s .
   * `svchost.exe (LocalSystemNet...)` (PID 3672): Lectura de 106.496 B/s.
   * `fontdrvhost.exe`: Lectura de 100.864 B/s.
* **Activitat general del disc:** Transferència global de 126.149 B/s amb un temps d'activitat de la unitat del 5%.
* **Estat de les unitats:**
   * Disc local `C:` — Temps de resposta: 4,72 ms | Capacitat en ús: 68,1 GB | Volum total: 81,2 GB.

<img width="783" height="517" alt="image" src="https://github.com/user-attachments/assets/cd3e911f-8d25-460c-9386-ec7794da1ef8" />


### Pas 9 i 10: Anàlisi de Xarxa i Ports Oberts (Monitor de Recursos)
La secció de **Red** mostra les interaccions externes de les aplicacions i els serveis que esperen connexions:
* **Processos amb trànsit de xarxa:**
   * `svchost.exe (NetworkService...)` (PID 1904): Recepció dominant de **261 B/s**.

<img width="785" height="556" alt="image" src="https://github.com/user-attachments/assets/75b190e2-c681-4a23-be03-585ed8960da1" />


---

## 3. Conclusions i Balanç Clínic del Servidor

L'ús combinat de l'Administrador de tasques i el Monitor de recursos ens capacita per fer auditories mètriques detallades de la infraestructura de sistemes.

### Quadre resum de mètriques trobades

| Component de Maquinari | Utilitat de diagnòstic | Valor registrat | Estat / Valoració |
| :--- | :--- | :--- | :--- |
| **CPU (General)** | Administrador de tasques | 9% d'ús (Intel i7-10700) | ✅ Càrrega Baixa / Estable |
| **Memòria RAM** | Administrador de tasques | 1,6 de 4,0 GB (40%) | ✅ Volum Acceptable |
| **Xarxa (Ethernet)** | Administrador de tasques | Baixada: 9,2 Mbps / Pujada: 80 Kbps | ⚠️ Trànsit alt (Descàrrega) |
| **CPU (Detall)** | Monitor de recursos | 35% global (`wuauserv` 9,63%) | ⚠️ Windows Update operant |
| **Memòria (Detall)** | Monitor de recursos | 37% de línia base (`MsMpEng` 161 MB) | ✅ Correcte (Antivirus actiu) |
| **Emmagatzematge** | Monitor de recursos | Procés `System` 939 KB/s (5% actiu) | ✅ Rang de treball Normal |
| **Xarxa (Detall)** | Monitor de recursos | `svchost.exe` rebent 1,1 MB/s | ⚠️ Descàrrega de paquets activa |
| **Seguretat de Ports** | Monitor de recursos | Ports 53 (DNS) i 88 (Kerberos) | ✅ Validat (Estandard per AD) |

### Lliçons i observacions clau per a l'administrador
1. **L'Administrador de tasques és orientatiu:** Ofereix una foto ràpida de l'estat del sistema, però es queda curt per resoldre problemes complexos perquè no pot obrir el contingut dels processos agregats (`svchost.exe`). Per a això, és obligatori fer servir el **Monitor de recursos**.
2. **Identificació de l'impacte de Windows Update:** Durant les proves, el servei `wuauserv` ha estat el causant directe de l'augment de la CPU (9,63%) i de l'ús de la línia de xarxa (9,2 Mbps), verificant una tasca de manteniment programada en segon pla.
3. **Validació del Directori Actiu:** L'absència de ports estranys i la presència exclusiva dels ports 53 (DNS) i 88 (Kerberos) garanteixen que els rols de seguretat s'estan executant sota un entorn protegit i previst.
4. **Proactivitat vs Reactivitat:** Recorda que la *monitorització* descriu el present del servidor de forma proactiva. Per conèixer accions del passat o fer un seguiment històric forense, cal recórrer al *Visor d'esdeveniments* (auditoria reactiva). Ambdues pràctiques són complementàries per a una gestió professional.

