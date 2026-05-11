
# ⚡ Sprint 1: Instal·lació i configuració inicial

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

Escollim usuari i contrasenya.

<img width="968" height="738" alt="image" src="https://github.com/user-attachments/assets/4554eee7-86ed-449d-aa4b-051da6652e09" />

<img width="960" height="733" alt="image" src="https://github.com/user-attachments/assets/9545faa2-d6d0-499e-b2b8-2a9f3d01c0f1" />

Acabem de configurar les preguntes restants i finalment ja tindrem el nostre SO instal·lat a la màquina virtual.

<img width="1045" height="841" alt="image" src="https://github.com/user-attachments/assets/a9eb395a-fe05-43d8-b8d8-929f6bc7abaa" />


## 🔄 Punts de Restauració

Els punts de restauració són una eina de recuperació del sistema que permet revertir l'estat de l'equip a un moment anterior sense afectar els fitxers personals.

---

### 📌 Conceptes Clau
* **Què és:** Una "foto" (snapshot) dels fitxers de sistema, el Registre de Windows i els controladors (drivers).
* **Tecnologia:** Es basa en el servei **Shadow Copy (VSS)** de Windows.
* **Quan es creen:**
    * **Automàtics:** Abans d'instal·lar actualitzacions o nous programes.
    * **Manuals:** Creats per l'administrador abans de fer canvis crítics.

---

### ⚠️ Què es restaura i què no?

| Es recupera ✅ | No es toca ❌ |
| :--- | :--- |
| Fitxers de sistema (.exe, .dll) | Documents (.docx, .pdf) |
| Configuració del Registre | Imatges i Vídeos |
| Controladors (Drivers) | Missatges de correu |
| Programes instal·lats recentment | Contrasenyes canviades recentment |

---

### 🛠️ Administració per al Tècnic (ISO)
1.  **Espai en disc:** Es pot limitar quant espai ocupen (quan s'omple, s'esborren els més antics).
2.  **Desplegament:** En entorns corporatius, es pot gestionar mitjançant **GPO** (Polítiques de Grup) per assegurar que els usuaris no els desactivin.
3.  **Utilitat:** És el primer pas de recuperació davant d'una pantalla blava (BSOD) o un error de controlador després d'una actualització.

> [!TIP]
> Si el sistema no arrenca, els punts de restauració es poden aplicar des de l'**Entorn de Recuperació de Windows (WinRE)**.


### Creació d'un punt de restauració

Per a crear un punt de restauració a Windows primer hem de buscar a la barra de cerca "Crear un punt de restauració". Si seleccionem l'opció que ens ha aparegut s'obrirà una finestra amb totes les opcions disponibles.

<img width="1251" height="626" alt="image" src="https://github.com/user-attachments/assets/3d0aef20-4eaf-41b7-a561-0cc356449aa1" />

Per a crear-lo ens demana Configurar la restauració en una unitat del sistema i activar la protecció.

<img width="821" height="493" alt="image" src="https://github.com/user-attachments/assets/ea9acd45-d028-4b4e-8e7c-e5e1fd0e813c" />

Un cop fet això seleccionem Crear per a començar el procès de fer un punt de restauració. Lo primer serà escriure una descripció que ens ajudi a identificar el punt que anem a crear.

<img width="405" height="218" alt="image" src="https://github.com/user-attachments/assets/9fa1e7d5-4b74-445b-9f5a-8e21d9487e89" />

Acceptem i podem veure com el sistema comença a crear-lo i ens avisa quan termini.

<img width="271" height="79" alt="image" src="https://github.com/user-attachments/assets/4afb3e30-0274-4e7a-bbec-ff6566c6d7c8" /> <img width="346" height="122" alt="image" src="https://github.com/user-attachments/assets/40e27645-6be2-4853-bae1-2f32dfcbdde2" />

Ara anem a comprovar que s'hagi creat correctament, per fer-ho instal·larem una aplicació com per exemple Chrome.

<img width="770" height="781" alt="image" src="https://github.com/user-attachments/assets/6c0430b6-7e39-440c-8d21-435d3a4b8afc" />


Un cop instal·lat anem a restaurar el sistema. Per fer-ho hem d'accedir de nou al menú de creació de punts de restauració, on trobarem l'opció de restaurar sistema.

<img width="406" height="475" alt="image" src="https://github.com/user-attachments/assets/fd496154-c64b-4427-b372-0b28596415dc" />

Se'ns obrirà una nova finestra per a restaurar, premem següent.

<img width="560" height="450" alt="image" src="https://github.com/user-attachments/assets/0ae56b1c-f99b-4f76-b203-38dd172b3e41" />

Ara ens sortiran tots els punts de restauració disponibles, on podem trobar el que hem creat anteriorment. 

<img width="565" height="455" alt="image" src="https://github.com/user-attachments/assets/0c28833b-a560-4166-a35b-7cc701a74a80" />

Seleccionem següent i a continuació Finalitzar per a començar el procès de restauració.

<img width="635" height="342" alt="image" src="https://github.com/user-attachments/assets/6460c02f-844f-458a-88ef-26288fa3a643" />

Un cop restaurat tornem a mirar i podem observar que no tenim chrome instal·lat.

<img width="542" height="238" alt="image" src="https://github.com/user-attachments/assets/59370d91-6796-4c34-b09f-caa52302c0d7" />

<img width="771" height="780" alt="image" src="https://github.com/user-attachments/assets/1f6643b4-1b0c-40b0-8f0e-03b6293f0020" />


## 💻 El Llicenciament de Microsoft Windows

### 1. Introducció al Llicenciament
En la implantació de sistemes, el llicenciament no és només un tràmit legal, sinó una part del **disseny de la infraestructura**. Una elecció incorrecta pot:
* Incrementar els costos de forma innecessària.
* Impedir el desplegament per xarxa (imatges de sistema).
* Limitar la gestió centralitzada mitjançant dominis.

Quan adquirim Windows, no comprem el programari, sinó un **EULA** (*End User License Agreement*), un contracte que ens atorga el dret d'ús sota condicions específiques.

---

### 2. Canals de Venda i Tipus de Llicències
Segons com s'adquireixi el programari, la llicència té diferents propietats tècniques:

| Tipus | Descripció | Característica Clau |
| :--- | :--- | :--- |
| **OEM** (*Original Equipment Manufacturer*) | Venen preinstal·lades pel fabricant de l'ordinador (HP, Dell, etc.). | Queda lligada a la **placa base**. Si l'equip mor, la llicència es perd. |
| **Retail** (*FPP - Full Packaged Product*) | Adquirides en format físic o digital a través de Microsoft o distribuïdors. | Són **transferibles**. Es pot moure d'un ordinador vell a un de nou. |
| **Volume Licensing** (*VL*) | Contractes per a empreses (mínim 5 llicències). | Permeten el **Dret de Re-imatge**, necessari per a desplegaments massius (WDS/SCCM). |

---

### 3. Edicions de Windows i el seu Ús
En la **Implantació de Sistemes Operatius**, triem l'edició segons les necessitats de xarxa:

#### 🏠 Home
* Ús domèstic.
* **Limitació:** No permet unir-se a un Domini (Active Directory). No inclou BitLocker ni Escriptori Remot (servidor).

#### 💼 Pro
* Pensada per a petites i mitjanes empreses.
* Inclou gestió de dominis, BitLocker, Escriptori Remot i Hyper-V.

#### 🏢 Enterprise
* Dissenyada per a grans organitzacions.
* Funcions avançades: DirectAccess, AppLocker, i gestió de branques d'actualització més llargues (LTSC).

#### 🎓 Education
* Basada en l'edició Enterprise, però amb preus reduïts per a centres educatius i acadèmics.

---

### 4. Models d'Activació Corporativa
En entorns professionals, no s'activa cada equip manualment. S'utilitzen mètodes automatitzats:

1. **MAK (Multiple Activation Key):**
   - Una única clau per a múltiples activacions.
   - Cada ordinador connecta amb els servidors de Microsoft per validar-se.
   - Ideal per a equips que no sempre estan a la xarxa local.

2. **KMS (Key Management Service):**
   - Es configura un servidor local a la xarxa de l'empresa.
   - Els clients s'activen contra el servidor local, sense necessitat d'Internet.
   - Requereix un mínim d'equips (llindar) per començar a funcionar.

---

### 5. El Futur: Windows as a Service (WaaS)
Actualment, Microsoft està migrant cap a un model de **subscripció** dins de l'ecosistema **Microsoft 365**. 
- Es llicencia per **usuari** i no per dispositiu.
- Permet una gestió més àgil de les actualitzacions i la seguretat en el núvol.

---

> [!IMPORTANT]
> **Nota sobre Windows Server:** > A diferència de les versions de client, Windows Server es llicencia normalment per **nuclis (cores)** del processador. A més, calen les **CALs** (*Client Access Licenses*) per a cada usuari o dispositiu que accedeixi als serveis del servidor.

---

### Activació del sistema

Per a veure si tenim Windows activat hem d'anar a Configuració > Sistema > Activació i comprovem que no tenim Windows activat.

<img width="949" height="589" alt="image" src="https://github.com/user-attachments/assets/f1789226-ddc6-43cd-9f35-f9438906482a" />

Executem la comanda slmgr /xpr que serveix per comprovar l'estat d'expiració de la llicència actual del sistema.

<img width="731" height="363" alt="image" src="https://github.com/user-attachments/assets/43446907-b6dc-4f9d-a926-786f4827c906" />


### Edicions i preus

| Edició de Windows | Microsoft Store (Oficial / Retail) | Botigues de tercers (Claus OEM / Mercat gris)* |
| :--- | :--- | :--- |
| **Windows 11 Home** | ~ 145 € | 10 € - 20 € |
| **Windows 11 Pro** | ~ 259 € | 15 € - 30 € |

---

## Gestor d'arrencada

* **Pas 16 i 17:** Obrir Command Prompt com administrador i executar `bcdedit`.
  
    <img width="693" height="614" alt="image" src="https://github.com/user-attachments/assets/89e189c0-73a6-4ca4-aa06-bda14da78520" />

* **Pas 18 i 19:** Identificar els blocs i interpretar dades concretes (Boot Manager i Boot Loader).
    * **Boot Manager:** `default {current}` (sistema que arrenca per defecte), `timeout 30` (temps d'espera abans d'arrencar).
    * **Boot Loader:** `device partition=C:` (on està instal·lat Windows), `path \Windows\system32\winload.efi` (fitxer que carrega el sistema), `description Windows 11` (sistema operatiu).
* **Pas 20:** Respondre preguntes curtes.
    * Quin sistema s'està arrencant:   S'està arrencant **Windows 11** (es veu al paràmetre `description` del Cargador d'arrencada).
    * A quin disc o partició està instal·lat:   Està instal·lat a la **partició C:** (es veu al paràmetre `device` del Cargador d'arrencada).
    * Quant temps espera abans d'arrencar:  Espera **30 segons** (es veu al paràmetre `timeout` de l'Administrador d'arrencada).
    * Quin fitxer inicia Windows:  L'inicia el fitxer **`\WINDOWS\system32\winload.efi`** (es veu al paràmetre `path` del Cargador d'arrencada).
* **Pas 21:** Interpretació final. Explicar amb una frase:
    * Qui decideix l'arrencada (Boot Manager): És el gestor principal que llegeix la configuració inicial i decideix quin sistema operatiu s'ha d'executar, basant-se en l'opció per defecte i el temps d'espera.
    * Qui carrega el sistema (Boot Loader): És el programa específic (com `winload.efi`) que rep l'ordre del Boot Manager i s'encarrega de carregar físicament el nucli de Windows des del disc dur a la memòria RAM per iniciar-lo.

---

## Xarxa bàsica

* **Pas 22 i 23:** Obrir configuració de xarxa i consultar IP amb: `ipconfig`.

   <img width="629" height="291" alt="image" src="https://github.com/user-attachments/assets/f80f4123-5e0b-4733-af6b-a10e5fd65621" />

* **Pas 24:** Configurar IP dinàmica (DHCP automàtic).
  
    <img width="952" height="825" alt="image" src="https://github.com/user-attachments/assets/eb8f3933-2476-443b-9b07-0085e9dda6ec" />

* **Pas 25:** Configurar IP fixa (manual: IP, màscara, gateway, DNS).

    <img width="498" height="602" alt="image" src="https://github.com/user-attachments/assets/f9006c9d-21d3-47d4-aee6-7220f58071e9" />

* **Pas 26:** Comprovar connexió amb: `ping google.com`.

    <img width="689" height="311" alt="image" src="https://github.com/user-attachments/assets/60dbcba7-0dcd-42c4-9fb8-34445c797f80" />

---

## Comandes generals

* **Pas 27:** Obrir PowerShell.
    * *[Insereix la captura de pantalla aquí]*
* **Pas 28:** Diferenciar cmd i PowerShell.
    * **cmd:** Comandes bàsiques i clàssiques.
    * **PowerShell:** Més potent, permet treballar amb objectes i automatitzar tasques.
* **Pas 29:** Provar comandes bàsiques (`dir`, `cd`, `mkdir prova`, `echo hola > fitxer.txt`, `del fitxer.txt`).
    * *[Insereix la captura de pantalla aquí demostrant-ne l'ús]*
* **Pas 30:** Comandes útils del sistema (`tasklist`, `taskkill /IM notepad.exe /F`, `systeminfo`, `hostname`, `whoami`).
    * *[Insereix la captura de pantalla aquí demostrant-ne l'ús]*
* **Pas 31:** Comandes de xarxa (`ipconfig`, `ping google.com`, `netstat -an`).
    * *[Insereix la captura de pantalla aquí demostrant-ne l'ús]*
* **Pas 32:** Comandes interessants (`tree`, `cls`, `help`, `shutdown /s /t 0`).
    * *[Insereix la captura de pantalla aquí demostrant-ne l'ús]*
* **Pas 33:** Mini interpretació.
    * Indicar què mostra `tasklist`: [Escriu la resposta aquí]
    * Indicar què mostra `ipconfig`: [Escriu la resposta aquí]
    * Indicar què mostra `systeminfo`: [Escriu la resposta aquí]

---

## Instal·lació d'aplicacions

* **Pas 34, 35 i 36:** Descarregar un programa des del navegador (ex: Chrome o VS Code), instal·lar-lo seguint l'assistent, obrir-lo i comprovar que funciona.
    * *[Insereix la captura de pantalla aquí]*
* **Pas 37 i 38:** Instal·lar una aplicació des de Microsoft Store, obrir-la i comprovar funcionament.
    * *[Insereix la captura de pantalla aquí]*
* **Pas 39:** Desinstal·lar una aplicació: Configuració → Aplicacions → Desinstal·lar.
    * *[Insereix la captura de pantalla aquí]*
* **Pas 40:** Verificació: Comprovar que el programa ja no apareix al sistema.
    * *[Insereix la captura de pantalla aquí]*

























