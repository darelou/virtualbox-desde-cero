# 14 · Glosario

Las palabras técnicas que aparecen en la guía, en orden alfabético y explicadas en una o dos líneas.

| Término | Significado |
|---|---|
| **ACPI** | El sistema que permite apagar el ordenador "pulsando el botón". *Apagado ACPI* es pedirle al sistema invitado que se apague ordenadamente. |
| **Adaptador puente** | Modo de red en el que la máquina se conecta a tu red real como un ordenador más. Ver [Redes](11-redes-explicadas.md#adaptador-puente). |
| **Anfitrión** (*host*) | Tu ordenador de verdad, donde está instalado VirtualBox. |
| **BIOS / UEFI** | El programa que arranca un ordenador antes que el sistema operativo. La UEFI es la versión moderna. En las máquinas virtuales, "Habilitar EFI" activa la UEFI. |
| **Captura (de teclado o ratón)** | Cuando la máquina virtual se queda con el teclado y el ratón. Se suelta con la tecla anfitrión. |
| **Clon** | Copia de una máquina. *Completo* si copia todo, *enlazado* si reutiliza los discos de la original. |
| **Complementos del invitado** (*Guest Additions*) | Controladores que se instalan dentro de la máquina para que funcione mejor (pantalla, ratón, portapapeles, carpetas compartidas...). |
| **Controlador** (de almacenamiento) | La pieza a la que se conectan los discos: IDE, SATA, SCSI, NVMe... |
| **CPU** | El procesador. En VirtualBox, el número de "procesadores" es cuántos núcleos le prestas a la máquina. |
| **DHCP** | Servicio que da una dirección IP automáticamente a los equipos de una red. |
| **Disco dinámico** | Disco virtual que empieza pequeño y crece según se usa. |
| **Disco diferencial** | Archivo que guarda solo los cambios hechos desde una instantánea. |
| **Disco fijo** | Disco virtual que ocupa todo su tamaño desde el principio. |
| **Estado guardado** | La memoria de la máquina guardada en un archivo `.sav` al cerrarla con *Guardar el estado*. |
| **Extension Pack** | Paquete oficial con funciones extra (escritorio remoto, webcam, cifrado...). Tiene su propia licencia. |
| **Hipervisor** | El programa que crea y controla las máquinas virtuales. VirtualBox es un hipervisor de tipo 2. |
| **Host Key** (tecla anfitrión) | La tecla que recupera el teclado y el ratón y se usa para los atajos de la máquina. Por defecto, **Ctrl derecha**. |
| **Hyper-V** | El hipervisor de Microsoft que viene con Windows. Si está activo, VirtualBox puede ir más lento. |
| **Imagen ISO** | Un archivo `.iso` que es la copia exacta de un CD o DVD. |
| **Instantánea** (*snapshot*) | Una "foto" del estado de la máquina para poder volver a él. |
| **Invitado** (*guest*) | El sistema operativo que funciona dentro de la máquina virtual. |
| **IP** | La dirección de un equipo en una red, por ejemplo `192.168.56.101`. |
| **MAC** | El identificador único de una tarjeta de red. |
| **Máquina virtual** (MV o VM) | Un ordenador simulado por software dentro de tu ordenador. |
| **Medio** | En VirtualBox, cualquier disco virtual: disco duro, ISO o disquete. |
| **Modo básico / experto** | Los dos niveles de la interfaz de VirtualBox 7.1: el básico muestra menos opciones, el experto, todas. |
| **NAT** | Técnica para que varios equipos salgan a Internet con una sola IP. También es el modo de red por defecto de VirtualBox. |
| **OVA / OVF** | Formatos estándar para empaquetar y compartir máquinas virtuales. |
| **Paravirtualización** | Técnica por la que el sistema invitado colabora con el hipervisor para ir más rápido. |
| **Portapapeles compartido** | Poder copiar y pegar entre tu ordenador y la máquina. |
| **RAM** | La memoria de trabajo. Se borra al apagar. |
| **Red interna** | Modo de red en el que solo se ven entre sí las máquinas virtuales. |
| **Red NAT** | Modo de red en el que varias máquinas se ven entre sí y salen a Internet. |
| **Reenvío de puertos** | Regla que abre un puerto de tu ordenador hacia una máquina en NAT. |
| **Secure Boot** | Arranque seguro: solo arrancan sistemas firmados. Lo exige Windows 11. |
| **Servicio virtualizado** (*appliance*) | Una máquina empaquetada para compartirla, normalmente en un `.ova`. |
| **Sistema "live"** | Un sistema que arranca y funciona directamente desde un CD o USB, sin instalarse. |
| **Sistema operativo** | El programa principal del ordenador: Windows, Linux, macOS... |
| **Sólo anfitrión** (*host-only*) | Modo de red que conecta las máquinas con tu ordenador, sin Internet. |
| **TPM** | Chip de seguridad que guarda claves de cifrado. Windows 11 exige TPM 2.0. |
| **Trazas** (*logs*) | Archivos donde VirtualBox apunta todo lo que pasa en una máquina. |
| **USB** | El tipo de conexión de memorias, ratones, discos externos... |
| **UUID** | Identificador único que VirtualBox da a cada máquina y a cada disco. |
| **VDI / VMDK / VHD** | Formatos de disco virtual de VirtualBox, VMware y Microsoft. |
| **VRDP** | El escritorio remoto de VirtualBox, para manejar una máquina desde otro ordenador. Lo añade el Extension Pack. |
| **VT-x / AMD-V** | La función del procesador (Intel o AMD) que permite la virtualización por hardware. Es obligatoria para VirtualBox. |

---

<!-- nav -->
<div align="center">

[⬅️ 13 · Problemas frecuentes](13-problemas-frecuentes.md) &nbsp;·&nbsp; [🏠 Índice](../README.md)

</div>
