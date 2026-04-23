
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




























