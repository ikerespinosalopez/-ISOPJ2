# Sprint 4
## RAIDS
### Què és un RAID?

**RAID** són les sigles de *Redundant Array of Independent Disks* (Matriu Redundant de Discos Independents).

L'objectiu principal d'un sistema RAID és agafar diversos discos durs físics i combinar-los perquè l'ordinador (o servidor) els vegi com una única unitat lògica. Això es fa per aconseguir dues coses fonamentals:

1. **Més velocitat (Rendiment):** Llegir i escriure dades més ràpidament repartint la càrrega de treball entre diversos discos simultàniament.
2. **Més seguretat (Redundància):** Protegir la informació i evitar perdre dades en cas que un dels discos durs pateixi una fallada mecànica o electrònica.

A continuació, s'expliquen els tres nivells RAID més utilitzats:

---

#### RAID 0 (Fraccionament o *Striping*)

Aquest nivell divideix els arxius en petits blocs i els reparteix a parts iguals entre dos o més discos.

* **✅ Avantatge:** És increïblement ràpid. Com que el sistema guarda la informació en diversos discos al mateix temps, la velocitat de lectura i escriptura es multiplica.
* **❌ Inconvenient:** **No té cap seguretat (no hi ha redundància).** Com que les dades estan repartides, si només un dels discos es trenca, es perd absolutament tota la informació de l'array de manera irrecuperable.

#### RAID 1 (Emmirallament o *Mirroring*)

Aquest nivell no divideix les dades, sinó que fa una còpia exacta i automàtica de tota la informació (un "mirall") en dos o més discos. 

* **✅ Avantatge:** Màxima seguretat i continuïtat. Si un disc s'espatlla físicament de cop, el sistema continua funcionant perfectament perquè el segon disc té una rèplica al 100% idèntica.
* **❌ Inconvenient:** Sacrifiques el 50% de l'espai d'emmagatzematge. Si muntes dos discos d'1 TB cadascun, la capacitat total utilitzable serà d'1 TB (l'altre es dedica exclusivament a la redundància).

#### RAID 5 (Fraccionament amb Paritat)

Aquest és un dels sistemes més utilitzats en entorns empresarials perquè busca un equilibri. Requereix un mínim de **3 discos**. Reparteix les dades en blocs com el RAID 0 per ser ràpid, però alhora calcula i distribueix un codi de recuperació (anomenat "paritat") entre tots els discos.

* **✅ Avantatge:** És ràpid, aprofita molt millor l'espai total que el RAID 1 i és segur. Si **un disc** es trenca, el sistema fa servir els codis de paritat de la resta de discos per "reconstruir" matemàticament les dades perdudes quan insereixes un disc nou.
* **❌ Inconvenient:** Si fallen dos discos alhora, es perd tota la informació. A més, el procés de reconstrucció (quan canvies el disc trencat per un de nou) pot trigar hores o dies, i alenteix considerablement el rendiment del servidor mentre s'està executant.

#### Creació d'un RAID 1

Primer instal·lem el paquet mdadm.
<img width="648" height="24" alt="image" src="https://github.com/user-attachments/assets/d8f75fd0-d4a2-4bbe-9d4c-d9e751b61922" />

Amb la comanda  `fdisk -l` comprovem el nom dels nostres discs de 2 GB que hem afegit per a fer el RAID.
<img width="620" height="292" alt="image" src="https://github.com/user-attachments/assets/ab5dea1c-7f27-40a4-9f04-c4fac949d090" />

Ara creem una partició a cada disc amb la comanda fdisk.
<img width="811" height="586" alt="image" src="https://github.com/user-attachments/assets/c3ba011b-08f6-4ffd-b72b-7b7b312d31cc" />

Un cop fet comprovem que s'hagin creat correctament.
<img width="660" height="513" alt="image" src="https://github.com/user-attachments/assets/3c5d8384-647a-4eb2-b0da-81e00986e4b4" />

Creem una carpeta i li donem permisos per a fer el RAID.
<img width="590" height="160" alt="image" src="https://github.com/user-attachments/assets/b380dc43-d811-4288-8d73-4b8a18ca5b2f" />

I amb la comanda mdadm creem el RAID, indicant el nivell del RAID, el número de discos i els dicos en qüestió.
<img width="884" height="245" alt="image" src="https://github.com/user-attachments/assets/d60bc671-4225-44b3-85bc-a80a30053501" />

I li donem format.
<img width="874" height="265" alt="image" src="https://github.com/user-attachments/assets/a68572a5-e486-4876-94f2-9c9e647f6635" />

I per veure l'estat del RAID utilitzem la comanda `mdadm --detail [nom del RAID]`
<img width="817" height="628" alt="image" src="https://github.com/user-attachments/assets/7dc3b644-bf94-4cbe-8119-ecf91e4d6b26" />

ARa executemla següent comanda per veure el UID i la enviem a l'arxiu de configuració de mdadm.
<img width="746" height="74" alt="image" src="https://github.com/user-attachments/assets/0cc93438-fbfb-4274-818f-4b2e3eea1d80" />

Ara entrem a l'arxiu i afegim la següent línia:
<img width="709" height="94" alt="image" src="https://github.com/user-attachments/assets/9aa49d07-09d2-476f-a040-e8293d58d471" />

Ara anem a l'arxiu fstab i li afegim la següent línia per a que es munti automàticament i reiniciem.
<img width="812" height="327" alt="image" src="https://github.com/user-attachments/assets/24fc4918-d10d-42e8-ace4-f348905df799" />

Ara amb la comanda mdadm i el paràmetre -f farem que falli un dels discos, comprovem que és així.
<img width="791" height="747" alt="image" src="https://github.com/user-attachments/assets/8ce640a0-464d-4571-a63c-4bce079d0e5b" />

I comprovem que tot i haver fallat encara podem veure els arxius i treballar amb ells.
<img width="665" height="177" alt="image" src="https://github.com/user-attachments/assets/98c4f874-4c6c-4c98-81f1-a1bb9920fbe8" />

Ara eliminem el disc que ha fallat amb el aràmetre -r.
<img width="644" height="42" alt="image" src="https://github.com/user-attachments/assets/c908e9f7-fb68-4a02-92fc-0438db15d149" />

I el tornem a afegir amb el paràmetre -a .
<img width="648" height="46" alt="image" src="https://github.com/user-attachments/assets/ca11d6a5-0ecb-4357-a64d-2b7708eabbdf" />

I comprovem que s'està resincronitzant.
<img width="762" height="658" alt="image" src="https://github.com/user-attachments/assets/78d6cfa1-aa0c-4155-916b-2d0106669610" />

I podem veure que tot i haver treballat amb un sol disc podem veure que es conserven tots els arxius.
<img width="511" height="43" alt="image" src="https://github.com/user-attachments/assets/90ebb9fa-90d2-4ccc-9ba5-e124b40387c5" />

#### Esborrar RAID
Ara per fer una altra prova anem a esborrar el raid. Ho farem primer eliminant o comentant la línia de fstab.
<img width="823" height="342" alt="image" src="https://github.com/user-attachments/assets/4dc17280-6889-44dc-8602-ecd375bdeb14" />

I executem una sèrie de comandes per a eliminar les carpetas i desmuntar-lo, i comprovem que no existeix res.
<img width="880" height="232" alt="image" src="https://github.com/user-attachments/assets/9170f70d-f086-4a67-89e0-5a07af9dc795" />

Buidem també el contingut de l'arxiu mdadm.conf.
<img width="607" height="115" alt="image" src="https://github.com/user-attachments/assets/4cdb1c0c-9b74-41d2-aa14-9bd5c33f7edb" />

Executem la comanda mdadm amb el paràemtre --detail per veure que no tenim res.
<img width="681" height="45" alt="image" src="https://github.com/user-attachments/assets/fc1eea8a-e7ae-4e86-af1a-0773c8c1448e" />




