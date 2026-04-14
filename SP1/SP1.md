
# ⚡ Sprint 1: Instal·lació i Configuració Inicial

## Virtualització i instal·lació del SO Windows
Primer obrim VirtualBox i creem una nova màquina virtual. Seleccionem la ISO d'Ubuntu24 i configurem els paràmetres com la RAM,la xarxa i l'emmagatzematge.
<img width="1857" height="832" alt="image" src="https://github.com/user-attachments/assets/16100aea-2277-4bcf-9ada-725e5a7189d0" />


Obrim la MV i continuem amb la instal·lació del SO Windows de manera gràfica.

Seleccionem l'idioma del nostre SO.
<img width="1010" height="818" alt="image" src="https://github.com/user-attachments/assets/0fd14ab6-5280-4b64-aa68-665d4bc1ab82" />

Indiquem que volem Instal·lar Windows 11.
<img width="770" height="616" alt="image" src="https://github.com/user-attachments/assets/51e4eeb1-e682-4b88-b89c-3cfc71c720c9" />

Seleccionem que no tenim la clau del producte i continuem amb el procès. Escollim la versió de Windows desitjada, en aquest cas Windows 11 Pro.
<img width="749" height="596" alt="image" src="https://github.com/user-attachments/assets/71443093-8e18-47f2-8620-b396d53e5997" />

Acceptem els terminis de llicència i anem a la part del disc, on seleccionarem l'espai del disc on volem instal·lar el sistema.
<img width="750" height="600" alt="image" src="https://github.com/user-attachments/assets/a7b05361-2db7-4d9a-b652-33405a29f978" />

Un cop fet ja podem procedir amb la instal·lació.
<img width="756" height="599" alt="image" src="https://github.com/user-attachments/assets/afd4f920-c466-49b9-bb35-a51443d9ed48" />




## Llicenciament

Saber on és la llicencia y dcoumentar les que te el ubuntu y pe que  tal tal

Ubuntu és una distribució basada en Debian que inclou principalment programari amb llicències lliures i de codi obert. Cada paquet instal·lat a Ubuntu té un fitxer amb la llicència i els drets d'autor que es troba a /usr/share/doc/paquet/copyright.

Podem trobar les següents llicències que són les més habituals:
- GPL (General Public License): obliga a distriubir el codi font i les modificacions.
- LGPL: semblant però més flexible per a biblioteques compartides.
- MIT/BSD/Apache: llicències permissives, permeten ús comercial i redistribució amb algunes restriccions.
- Privatives (EULA): aplicades a alguns components com els controladors.

Legalment el sistema base es troba sota llicències lliures, les aplicacions de tercers poden variar segons el repositori d'origen i la documentació està sota llicències com la Creative Commons.

Els repositoris es poden dividir segons el tipus:
- Main: programari lliure.
- Restricted: controladors privatius.
- Universe: programari lliure mantingut per la comunitat.
- Multiverse: programari amb problemes de llicència o restriccions legals.
  
## Gestors d'arrencada per a instal·acions DUALS
Volem instal·lar Windows en mode DUAL en la nostra màquina virtual amb Ubuntu que hem creat anteriorment. Veurem dos escenaris diferents segons l'ordre d'instal·lació i l'ubicació de la misma. Per fer-ho, primer ens hem de descarregar la ISO de Windows y obrir el VirtualBox.

### Instal·lar Windows en DUAL desprès d'Ubuntu

Primer hem de preparar amb la nostra màquina Ubuntu tot lo necessari per a fer la instal·lació DUAL. Inserim la ISO de W10 Enterprise

<img width="951" height="463" alt="image" src="https://github.com/user-attachments/assets/8f10a503-4758-491c-bd81-1db90af77031" />

Procedim amb la instal·lació fins a arribar a les particions, on haurem de seleccionar l'espai buit que hem deixat abans i fer clic a Nou. 

<img width="852" height="821" alt="image" src="https://github.com/user-attachments/assets/111f7c0c-7bd1-483b-8d0f-177d7d174fb4" />

Seleccionem tot l'espai disponible i fem clic a següent per a acabar de fer la instal·lació. Quan acabi es reiniciarà la màquina i s'obrirà el Windows. Creem un compte i continuem amb la instal·lació fins a que se'ns obri Windows 10.
  
<img width="954" height="886" alt="image" src="https://github.com/user-attachments/assets/a580aada-c05e-410f-b149-c0700f4e0957" />

Ara quan tornem a iniciar la màquina veurem que s'obre Windows directament sense deixar-nos escollir el sistema que volem fer sevrir. Per solucionar-lo utilitzarem l'eina SuperGrub. El primer pas serà afegir la ISO del SuperGrub.

<img width="870" height="538" alt="image" src="https://github.com/user-attachments/assets/20a5c36c-551e-44e2-a575-964a02c8fe58" />

Un cop fet iniciem la màquina i mitjançant el boot manager obrim el SuperGrub.

<img width="628" height="531" alt="image" src="https://github.com/user-attachments/assets/026e6835-7f06-492a-9120-625cb1428057" />

Obrim el SuperGrub i seleccionem la segona opció que diu "Detect and show boot methods"

<img width="638" height="475" alt="image" src="https://github.com/user-attachments/assets/8d52805c-5974-4ee7-aaab-303fc8d79a5e" />

Trobem el linux que hem instal·lat i l'iniciem.

<img width="638" height="489" alt="image" src="https://github.com/user-attachments/assets/abb1826a-1b19-44a4-b95f-3dd5bcf17eae" />

Se'ns obrirà l'Ubuntu i haurem d'accedir a la terminal per a acabar de configurar el GRUB. Accedim al mode d'administrador amb la comanda "sudo su". EL primer que haurem de fer és reinstal·lar el grub amb la comanda "apt install --reinstall grub-pc".

<img width="857" height="543" alt="image" src="https://github.com/user-attachments/assets/69913466-32a8-4c5e-ae81-e3a75704bb70" />

A continuació executem la comanda "grub-install /dev/sda".

<img width="655" height="92" alt="image" src="https://github.com/user-attachments/assets/0666dc40-bf6d-4f09-a241-ea59d1564c6d" />

Anem a la carpeta /boot i mirem si tenim una subcarpeta anomenada /efi, si no la tenim la creem amb la comanda "mkdir efi".

<img width="818" height="378" alt="image" src="https://github.com/user-attachments/assets/97d7cad1-ca52-46cc-a30e-dc747041b47a" />

Anem a la carpeta que acabem de crear i executem la comanda "fdisk -l".

<img width="842" height="674" alt="image" src="https://github.com/user-attachments/assets/2e98f166-b03e-4b69-aa1e-bc90cf9f1854" />

Aquí hem de trobar la partició del Sistema EFI.

<img width="798" height="257" alt="image" src="https://github.com/user-attachments/assets/b2f29e03-136a-466d-b8b2-aa1b268dd18c" />

Amb aquesta informació executem la comanda "mount /dev/sda6 /boot/efi".

<img width="607" height="20" alt="image" src="https://github.com/user-attachments/assets/2a4c4067-b280-46a2-8f9b-5935cb187da1" />

Desprès executem aquesta comanda "grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=Ubuntu".

<img width="832" height="113" alt="image" src="https://github.com/user-attachments/assets/ce00727d-3ecb-4e93-b210-47fe365e4f86" />

Ara executem la comanda update-grub i podem trobar el Linux i el Windows.

<img width="838" height="294" alt="image" src="https://github.com/user-attachments/assets/07730bd5-0a7b-48e6-9664-29e78aa5c1bf" />

Ara instal·larem el gestor d'arrencada amb la comanda "apt install efibootmgr".

<img width="815" height="244" alt="image" src="https://github.com/user-attachments/assets/395de237-2e29-45fc-a277-cb2ad971d270" />

L'executem amb la comanda "efibootmgr" per a veure l'ordre d'arrencada, ens hem d'assegurar de que estigui primer el Ubuntu, si no és així es pot modificar amb la comanda "efibootmgr -o [ordre]".

<img width="839" height="576" alt="image" src="https://github.com/user-attachments/assets/cae04489-9815-4bc9-84b1-d28a6699fc92" />

Ara hem de modificar l'arxiu del grub amb la comanda "nano /etc/default/grub". Els paràmetres GRUB_TIMEOUT_STYLE=hidden i GRUB_TIMEOUT=0  han d'estar coments i el paràmetre GRUB_DISABLE_OS_PROBER=false sense comentar.

<img width="843" height="284" alt="image" src="https://github.com/user-attachments/assets/e1e59fbf-86ea-468f-b358-7f469f587d5c" />

Guardem l'arxiu i ja podem apagar la màquina i treiem la ISO de W10 per a iniciar-la i comprovar que podem accedir a ambdos sistemes operatius.

<img width="849" height="374" alt="image" src="https://github.com/user-attachments/assets/500e3534-0172-4c87-80c5-e1c773eb1e81" />



## Punts de restauració

Obrim la màquina virtual i li configurem un nou disc de 15GB on farem les còpies de seguretat.

<img width="858" height="456" alt="image" src="https://github.com/user-attachments/assets/82e85bf3-f444-4c43-9df3-63bb80207024" />

Obrim un terminal dins la màquina i executem la comanda apt install timeshift per a instal·lar Timeshift, la aplicació que farem servir per a fer les còpies de seguretat i els punts de restauració.

<img width="879" height="452" alt="image" src="https://github.com/user-attachments/assets/0444a6bb-382d-48d1-a9cf-fb4981e4851c" />

Ara mitjançant la comanda fdisk -l podem trobar el nostre disc, que en aquest cas és /dev/sdb. A continuació executem la comanda fdisk /dev/sdb.

<img width="690" height="230" alt="image" src="https://github.com/user-attachments/assets/18a3564a-81c3-4d3a-aade-a8e3a8a78d92" />

Un cop dins, premem N per a crear una nova partició dins del disc, que en aquest cas ocupa tot l'espai disponible.

<img width="884" height="582" alt="image" src="https://github.com/user-attachments/assets/d5f8f458-c954-4e33-b59b-dcf4a33ba197" />

Podem comprovar que tenim el disc afegit amb la partició creada amb la comanda fdisk -l.

<img width="625" height="256" alt="image" src="https://github.com/user-attachments/assets/c0c33db9-bfb8-4732-a106-3135a20f6062" />

Per donar-li un format a aquesta partició ho farem amb la comanda mkfs.ext4 /dev/sdb1 i tindrà el format ext4.

<img width="876" height="278" alt="image" src="https://github.com/user-attachments/assets/44c17985-f551-4948-913f-dff29490d169" />


Ara per a comprovar el correcte funcionament dels punts de restauració que farem més endavant crearem un arxiu i una carpeta d'exemple, anomenats hola i adeu respectivament.

<img width="860" height="200" alt="image" src="https://github.com/user-attachments/assets/6951cf4c-3c9b-469a-ae15-c3356262ecc6" />

A continuació obrirem l'aplicació TimeShift que hem instal·lat prèviament i configurarem el tipus d'instantània com a RSYNC.

<img width="742" height="808" alt="image" src="https://github.com/user-attachments/assets/de2400fe-e11a-4cd9-a479-8883e073999c" />

Un cop dins, seleccionem la ubicació on volem guardar la instantània, en aquest cas serà el nostre disc dur nou.

<img width="750" height="548" alt="image" src="https://github.com/user-attachments/assets/8814fb64-6455-4241-a7d3-f7218d7be9f1" />

Escollim que la instantània es faci quan arrenquem el dispositiu, tenint en compte que es creen 10 minuts després de l'inici del sistema.

<img width="825" height="805" alt="image" src="https://github.com/user-attachments/assets/94db82b3-01de-48b1-bb87-72493f64d966" />

En el següent pas és important escollir en el nostre usuari l'opció de Inclou tots els fitxers.

<img width="880" height="528" alt="image" src="https://github.com/user-attachments/assets/7258935a-8777-47aa-8b8f-840f9f67c9fe" />

Creem una captura manualment per a no esperar els 10 minuts.

<img width="849" height="846" alt="image" src="https://github.com/user-attachments/assets/b3471ccc-4d4f-436d-99be-80582ba391d0" />

I podem veure quan acabi la instantània com s'ha creat.

<img width="814" height="838" alt="image" src="https://github.com/user-attachments/assets/6a6f5403-0f01-4479-88c1-c27cbf2d4254" />

Ara esborrem els arxius de prova que hem creat abans amb la comanda rm hola i rm -r adeu. Un cop fet obrim el timeshift i seleccionem restaurar.

<img width="848" height="751" alt="image" src="https://github.com/user-attachments/assets/1633fc0c-189e-4010-88fd-38f5fd8acb0a" />

Tornem a obrir la màquina i fem un ls per a veure com s'han restaurat els nostres arxius.

<img width="764" height="348" alt="image" src="https://github.com/user-attachments/assets/50ee6598-9d90-4d0e-84bd-2a32ba62859e" />

## Configuració de xarxa

Per a canviar la IP podem fer-ho gràficament accedint a la configuració de xarxa i escrivint manualment l'adreça desitjada juntament amb altres paràmetres com la màscara o el DNS.

<img width="889" height="726" alt="image" src="https://github.com/user-attachments/assets/0453adb8-416c-43cf-b7d2-a646a86000ef" />

Obrim un terminal i fem un ping al servidor DNS per a comprovar que tenim connexió i hem configurat bé la IP.

<img width="693" height="241" alt="image" src="https://github.com/user-attachments/assets/fbbb115d-1e92-4b0b-b9b1-910c17ad3721" />

Repetim canviant l'adreça IP per el host www.google.es.

<img width="801" height="306" alt="image" src="https://github.com/user-attachments/assets/35228cfd-8c1e-4884-99ab-3726755ba8f5" />

Una altra manera de modificar els paràmetres de xarxa és accedint a l'arxiu de configuració i escrivint-lo manualment. Anem al directori /etc/netplan i executem la comanda ls per veure els arxius, veurem un que es diu 01-network-manager-all.yaml i accedim a ell amb la comanda nano. Un cop dins configurem els paràmetres de manera que quedi així. (Important vigilar els espais.) 

<img width="589" height="402" alt="image" src="https://github.com/user-attachments/assets/ee34c790-b4e0-4fd7-9516-e0b2c67f098f" />

Un cop modificat i guardat executem la comanda netplan apply per a comprovar que l'hem escrit correctament i fem un ping a les mateixes adreces que abans per veure que tot funciona bé.

<img width="875" height="641" alt="image" src="https://github.com/user-attachments/assets/2ca7d157-6b2f-4efb-a951-ed76a90ca921" />


## Comandes generals i instal·lacions

Amb la comanda apt-cache policy nompaquet podem veure quina és la versió candidata a ser instal·lada quan instal·lem un paquet.

<img width="797" height="158" alt="image" src="https://github.com/user-attachments/assets/7f8efc15-74f1-40d5-99b3-ce4140d54f1b" />

Accedim a la carpeta /etc/apt/preferences.d i creem un nou arxiu on modificarem la prioritat i la versió que volem.

<img width="795" height="221" alt="image" src="https://github.com/user-attachments/assets/91bb921d-cba8-455e-a425-7fde7458ad2e" />
