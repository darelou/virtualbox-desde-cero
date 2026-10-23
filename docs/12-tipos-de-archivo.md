# 12 · Tipos de archivo

Trabajando con VirtualBox te vas a encontrar muchos archivos con extensiones raras. Este capítulo explica **qué es cada uno**, **dónde aparece** y **qué puedes hacer con él** sin romper nada. Los ejemplos son las carpetas reales de las máquinas usadas en la guía.

> [!TIP]
> Para ver las extensiones en Windows: Explorador de archivos → **Ver** → **Mostrar** → **Extensiones de nombre de archivo**.

**En este capítulo:**
- [Resumen de todas las extensiones](#resumen-de-todas-las-extensiones)
- [La carpeta de una máquina](#la-carpeta-de-una-máquina)
- [La carpeta de configuración de VirtualBox](#la-carpeta-de-configuración-de-virtualbox)
- [Lo que te descargas](#lo-que-te-descargas)
- [Qué se puede borrar y qué no](#qué-se-puede-borrar-y-qué-no)

---

## Resumen de todas las extensiones

### Configuración de las máquinas

| Extensión | Qué es | Qué hacer con él |
|---|---|---|
| **`.vbox`** | La **configuración** de una máquina: memoria, procesadores, discos, red... Es un archivo de texto en formato XML. | Para traer una máquina a la lista: [**Añadir**](07-anadir-importar-exportar.md#añadir-una-máquina-que-ya-existe), o doble clic sobre él. No lo edites a mano con VirtualBox abierto. |
| **`.vbox-prev`** | Una **copia automática** de la configuración anterior. VirtualBox la crea cada vez que guarda cambios. | Si el `.vbox` se daña, cierra VirtualBox, copia el `.vbox-prev` y cámbiale la extensión a `.vbox`. |
| **`.vbox-tmp`** | Un archivo temporal mientras VirtualBox guarda la configuración. | Normalmente desaparece solo. |
| **`nombre-1.16.vbox`** (u otro número) | Una copia de la configuración en el formato de una versión antigua de VirtualBox. Se crea al abrir una máquina hecha con una versión anterior. | Puedes dejarla, sirve si quieres volver a abrir la máquina con la versión vieja. |
| **`.nvram`** | La memoria de la "BIOS" de las máquinas con **EFI** activado (por ejemplo, Windows 11): opciones de arranque, claves de Secure Boot... | No lo borres: la máquina podría no arrancar. |

### Discos

| Extensión | Qué es | Qué hacer con él |
|---|---|---|
| **`.vdi`** | **VirtualBox Disk Image**: el disco duro virtual en el formato propio de VirtualBox. Es el archivo **más grande** y el **más importante**: dentro está todo el sistema invitado. | Gestionarlo desde la herramienta [Medio](05-herramientas-globales/02-medio.md). Para copiarlo, usa el botón **Copiar** de esa herramienta, no el Explorador. |
| **`.vmdk`** | **Virtual Machine Disk**: el formato de disco de VMware. VirtualBox lo usa sin problemas. También es el formato del disco dentro de un `.ova`. | Se puede conectar directamente a una máquina en [Almacenamiento](08-configuracion/04-almacenamiento.md), como `Metasploitable.vmdk`. |
| **`-s001.vmdk`, `-s002.vmdk`...** | Las partes de un disco VMDK dividido en trozos de 2 GB. | Mantenlas todas juntas en la misma carpeta. |
| **`.vhd`** | **Virtual Hard Disk**: el formato de disco de Microsoft (Hyper-V, Windows). | Se usa igual que un `.vdi`. |
| **`.hdd`** | El formato de disco de Parallels (Mac). | VirtualBox también puede usarlo. |
| **`{xxxxxxxx-...}.vdi`** (en `Snapshots`) | **Discos diferenciales**: guardan los cambios desde una [instantánea](09-herramientas-de-la-maquina/02-instantaneas.md). Su nombre es un identificador entre llaves. | **Nunca los borres a mano.** Elimina la instantánea desde VirtualBox. |

### Imágenes de CD, DVD y disquete

| Extensión | Qué es | Qué hacer con él |
|---|---|---|
| **`.iso`** | La copia exacta de un CD o DVD en un archivo. Así se distribuyen casi todos los sistemas operativos. | Meterla en la unidad óptica de una máquina para [instalar un sistema](06-crear-una-maquina.md) o arrancar un sistema "live". |
| **`.img`**, **`.flp`**, **`.vfd`** | Imágenes de **disquete**. | Para la disquetera virtual. Hoy casi no se usan. |
| **`VBoxGuestAdditions.iso`** | La ISO con los [complementos del invitado](10-usar-una-maquina.md#los-complementos-del-invitado). Viene con VirtualBox, en `C:\Program Files\Oracle\VirtualBox`. | Se mete con **Dispositivos** → **Insertar imagen de CD de los complementos del invitado...** |

### Máquinas empaquetadas

| Extensión | Qué es | Qué hacer con él |
|---|---|---|
| **`.ova`** | **Open Virtual Appliance**: una máquina completa empaquetada en un solo archivo (en realidad un paquete *tar* con los tres archivos de abajo). | [**Importar**](07-anadir-importar-exportar.md#importar-una-máquina-ova). |
| **`.ovf`** | **Open Virtualization Format**: la descripción de la máquina en texto XML (memoria, CPU, discos...). Va dentro del `.ova`, o suelto junto a sus discos. | Si lo tienes suelto, también se importa. |
| **`.mf`** | El **manifiesto**: sumas de comprobación de cada archivo para saber si alguno se ha dañado o modificado. | Lo comprueba VirtualBox al importar. |
| **`.cert`** | Un certificado opcional que **firma** el paquete para demostrar quién lo creó. | Lo comprueba VirtualBox al importar. |

### Estado, registros y extras

| Extensión | Qué es | Qué hacer con él |
|---|---|---|
| **`.sav`** | El **estado guardado**: el contenido de la memoria de la máquina cuando la cierras con *Guardar el estado* o tomas una instantánea con ella encendida. Ocupa aproximadamente lo mismo que la memoria usada. | No lo borres a mano. Para quitarlo, usa **Descartar** (estado guardado) o elimina la instantánea. |
| **`.log`** | Los [registros](09-herramientas-de-la-maquina/03-trazas.md) de la máquina (`VBox.log`, `VBoxHardening.log`) o de VirtualBox. Los antiguos llevan un número detrás (`VBox.log.1`, `.2`, `.3`). | Leerlos para resolver problemas. Se pueden borrar sin peligro con la máquina apagada. |
| **`.vbox-extpack`** | El instalador del [paquete de extensiones](05-herramientas-globales/01-extensiones.md). | Doble clic para instalarlo. |
| **`.webm`** | Un vídeo grabado con la [grabación de pantalla](08-configuracion/03-pantalla.md#grabación) (por ejemplo `Kali-screen0.webm`). | Se abre con cualquier navegador o reproductor de vídeo. |
| **`.png`** | Una captura hecha con **Ver** → **Tomar captura de pantalla...** | Una imagen normal. |

---

## La carpeta de una máquina

Cada máquina tiene su carpeta dentro de la [carpeta predeterminada de máquinas](04-preferencias.md#general) (`C:\Users\TuUsuario\VirtualBox VMs`). Este es el contenido real de **Mi primera VM** después de arrancarla y tomar dos instantáneas:

```text
Mi primera VM\
├── Mi primera VM.vbox                        8 KB    configuración
├── Mi primera VM.vbox-prev                   9 KB    copia anterior de la configuración
├── Mi primera VM.vdi                         2 MB    disco duro (dinámico: casi vacío)
├── Logs\
│   ├── VBox.log                            220 KB    registro del último arranque
│   └── VBoxHardening.log                   542 KB    comprobaciones de seguridad al arrancar
└── Snapshots\
    ├── {3a2d1cf4-26c8-430e-944b-8abadaf05ae3}.vdi      2 MB    disco diferencial
    ├── {ece0c32e-8781-4c8d-a2fb-599ce95c6c65}.vdi      2 MB    disco diferencial
    └── 2026-10-21T12-19-14-652624300Z.sav            217 MB    memoria de la instantánea "Sistema arrancado"
```

Y este el de **Lubuntu**, recién importada desde su `.ova` (todavía no se ha arrancado, por eso no tiene `Logs`):

```text
Lubuntu\
├── Lubuntu.vbox                3 KB    configuración
└── Lubuntu-disk001.vdi       7,5 GB    disco duro convertido a VDI al importar
```

## La carpeta de configuración de VirtualBox

VirtualBox guarda su propia configuración (la de **todo** el programa, no la de cada máquina) en `C:\Users\TuUsuario\.VirtualBox`. Contenido real, simplificado:

```text
.VirtualBox\
├── VirtualBox.xml                      lista de máquinas y discos registrados, redes, preferencias
├── VirtualBox.xml-prev                 copia anterior
├── VirtualBox-1.12-windows.xml         copia en formato de una versión antigua
├── VBoxSVC.log  (.1 ... .10)           registro del servicio de VirtualBox que funciona en segundo plano
├── selectorwindow.log  (.1 ... .10)    registro de la ventana principal
├── Eurofirms-Dhcpd.config              configuración del DHCP de la red NAT "Eurofirms"
├── Eurofirms-Dhcpd.leases              direcciones IP que ese DHCP ha repartido
├── Eurofirms-Dhcpd.log  (.1 ... .5)    registro de ese DHCP
└── HostInterfaceNetworking-VirtualBox Host-Only Ethernet Adapter-Dhcpd.*
                                        lo mismo para la red sólo anfitrión
```

> [!WARNING]
> No borres `VirtualBox.xml`: VirtualBox "olvidaría" todas tus máquinas (aunque sus carpetas sigan en el disco, tendrías que volver a añadirlas una a una).

## Lo que te descargas

Así queda una carpeta de descargas típica de un laboratorio, con lo usado en esta guía:

```text
ISOs & OVAs\
├── DVWA-1.0.7.iso                               480 MB   imagen de CD: se mete en la unidad óptica
├── Lubuntu.ova                                  3,7 GB   máquina empaquetada: se importa
├── Metasploitable.vmdk                          1,8 GB   disco suelto: se conecta a una máquina nueva
├── kali-linux-2026.2-virtualbox-amd64.7z        3,7 GB   máquina comprimida: se descomprime y se añade
└── kali-linux-2026.2-virtualbox-amd64\          (lo que sale al descomprimir el .7z)
    ├── kali-linux-2026.2-virtualbox-amd64.vbox
    ├── kali-linux-2026.2-virtualbox-amd64.vbox-prev
    ├── kali-linux-2026.2-virtualbox-amd64-1.16.vbox
    ├── kali-linux-2026.2-virtualbox-amd64.vdi    15 GB
    └── Logs\
```

**Qué hacer con cada cosa:**

| Tienes... | Haz esto |
|---|---|
| Un `.iso` | [Crea una máquina nueva](06-crear-una-maquina.md) y elígela en **Imagen ISO**. |
| Un `.ova` | [Impórtala](07-anadir-importar-exportar.md#importar-una-máquina-ova). |
| Un `.7z` o `.zip` | Descomprímelo. Si dentro hay un `.vbox`, [añádelo](07-anadir-importar-exportar.md#añadir-una-máquina-que-ya-existe). Si hay un `.ova`, impórtalo. |
| Un `.vmdk` o `.vdi` suelto | Crea una máquina nueva y, en el paso del disco, elige **Usar un archivo de disco duro virtual existente**. |

## Qué se puede borrar y qué no

| Se puede borrar sin peligro | **No** se debe borrar a mano |
|---|---|
| El `.ova` después de importarlo (si no lo quieres como copia) | Los `.vdi`, `.vmdk` y `.vhd` de una máquina que usas |
| El `.7z` o `.zip` después de descomprimirlo y añadir la máquina | Cualquier archivo de la carpeta `Snapshots` |
| Los registros viejos (`VBox.log.1`, `.2`, `.3`) | El `.vbox` y el `.nvram` |
| Las ISO que ya no vas a usar (primero sácalas de las máquinas) | Los `.sav` (usa **Descartar** en su lugar) |
| | `VirtualBox.xml` |

> [!IMPORTANT]
> Para borrar una máquina entera, usa siempre **Máquina** → **Eliminar...** → **Eliminar todos los archivos** ([capítulo 7](07-anadir-importar-exportar.md#eliminar-una-máquina)). Así VirtualBox borra todo lo que le pertenece y actualiza su lista.

---

<!-- nav -->
<div align="center">

[⬅️ 11 · Las redes explicadas](11-redes-explicadas.md) &nbsp;·&nbsp; [🏠 Índice](../README.md) &nbsp;·&nbsp; [13 · Problemas frecuentes ➡️](13-problemas-frecuentes.md)

</div>
