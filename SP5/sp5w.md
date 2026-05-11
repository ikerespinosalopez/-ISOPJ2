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

# Webgrafia

- Microsoft Learn  
https://learn.microsoft.com/es-es/windows-server/identity/solution-guides/deploy-security-auditing-with-central-audit-policies--demonstration-steps

- Vídeo YouTube — Cómo configurar auditorías en Windows Server  
https://www.youtube.com/watch?v=4UgQnVhA9sU

- Vídeo YouTube — Auditorías en Windows Server 2019  
https://www.youtube.com/watch?v=FqOYtkzNs8U

- Micromouse — Política de auditoría en Windows  
https://www.micromouse.com/2023/07/21/politica-auditoria-windows/

- Blog UGR — Activar la auditoría de inicio de sesión en Windows  
https://blogs.ugr.es/seguridadinformatica/activar-la-auditoria-de-inicio-de-sesion-en-windows/

