# 2 · Instalar VirtualBox

En este capítulo comprobamos que tu ordenador puede usar máquinas virtuales, descargamos VirtualBox de su web oficial y lo instalamos en Windows paso a paso.

**En este capítulo:**
- [Lo que necesita tu ordenador](#lo-que-necesita-tu-ordenador)
- [Comprobar que la virtualización está activada](#comprobar-que-la-virtualización-está-activada)
- [Descargar VirtualBox](#descargar-virtualbox)
- [Instalarlo paso a paso](#instalarlo-paso-a-paso)
- [El primer arranque](#el-primer-arranque)
- [Actualizar a una versión nueva](#actualizar-a-una-versión-nueva)

---

## Lo que necesita tu ordenador

| Requisito | Mínimo | Recomendado | Por qué |
|---|---|---|---|
| Sistema operativo | Windows 10 u 11 de 64 bits | Windows 11 | VirtualBox 7 solo funciona en sistemas de 64 bits. |
| Procesador | Con virtualización por hardware (**Intel VT-x** o **AMD-V**) | 4 núcleos o más | Desde la versión 6.1, VirtualBox **no funciona** sin esta función del procesador. |
| Memoria RAM | 8 GB | 16 GB o más | Tu Windows necesita su parte y cada máquina encendida se lleva la suya. |
| Espacio en disco | 30 GB libres | 100 GB o más, en SSD | Cada máquina virtual ocupa entre 10 y 80 GB. Un SSD hace que todo vaya mucho más rápido. |
| Permisos | Poder instalar programas | Cuenta de administrador | El instalador añade controladores de red y de USB. |

> [!NOTE]
> Casi todos los procesadores fabricados en los últimos diez años tienen virtualización por hardware. Lo que suele pasar es que viene **desactivada** de fábrica. El siguiente apartado explica cómo comprobarlo.

## Comprobar que la virtualización está activada

1. Pulsa **Ctrl + Mayúsculas + Esc** para abrir el **Administrador de tareas**.
2. Entra en **Rendimiento** y haz clic en **CPU**.
3. Abajo a la derecha busca la línea **Virtualización**:
   - Si pone **Habilitado**, todo está listo. Pasa a [Descargar VirtualBox](#descargar-virtualbox).
   - Si pone **Deshabilitado**, tienes que activarla en la UEFI (la antigua BIOS) de tu ordenador.

### Cómo activarla si está deshabilitada

1. En Windows abre **Configuración** → **Sistema** → **Recuperación**.
2. Junto a **Inicio avanzado** pulsa **Reiniciar ahora**.
3. Al reiniciar elige **Solucionar problemas** → **Opciones avanzadas** → **Configuración de firmware UEFI** → **Reiniciar**.
4. Se abre la pantalla de configuración de tu placa base. Cada fabricante la organiza a su manera, pero la opción suele estar en un menú llamado **Advanced**, **CPU Configuration** o **Overclocking**, y se llama:
   - En procesadores Intel: **Intel Virtualization Technology**, **VT-x** o **Vanderpool**.
   - En procesadores AMD: **SVM Mode**, **AMD-V** o **Virtualization**.
5. Ponla en **Enabled**, guarda los cambios (normalmente con la tecla **F10**) y deja que el ordenador arranque.

> [!WARNING]
> En la UEFI cambia **solo** esa opción. Si no estás seguro de lo que hace otra opción, no la toques. Si te equivocas, casi todas las placas tienen una opción para cargar los valores por defecto (**Load Defaults**).

## Descargar VirtualBox

1. Abre el navegador y entra en la web oficial: **[virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)**.
2. En la sección de paquetes de la plataforma (*platform packages*) haz clic en **Windows hosts**. Se descarga un archivo con un nombre parecido a `VirtualBox-7.1.8-168469-Win.exe` (los números cambian con cada versión).

> [!WARNING]
> Descarga VirtualBox **solo** desde su web oficial. Las webs de descargas de terceros a veces añaden programas no deseados al instalador.

El **Extension Pack** no hace falta para empezar. Si algún día lo necesitas, se descarga de la misma página y se instala desde la herramienta [Extensiones](05-herramientas-globales/01-extensiones.md).

## Instalarlo paso a paso

El instalador de VirtualBox está en inglés, aunque luego el programa se muestre en español. Estas son las pantallas que verás:

1. **Welcome to the Oracle VirtualBox Setup Wizard.** Es la bienvenida. Pulsa **Next**.
2. **Custom Setup.** Muestra las partes que se van a instalar:
   - **VirtualBox USB Support**: permite usar pendrives y otros USB dentro de las máquinas.
   - **VirtualBox Networking**: crea las tarjetas de red virtuales (modo puente y solo-anfitrión).
   - **VirtualBox Python Support**: solo para programadores que controlan VirtualBox con Python.

   Déjalo todo como está y pulsa **Next**. Puede aparecer otra pantalla con opciones de accesos directos (menú Inicio, escritorio, asociar archivos): déjalas también marcadas.
3. **Warning: Network Interfaces.** Avisa de que durante la instalación **se cortará la conexión de red unos segundos**. Es normal: cierra las descargas o videollamadas que tengas y pulsa **Yes**.
4. **Missing Dependencies Python Core / win32api.** Solo aparece si no tienes Python instalado. No lo necesitas para usar VirtualBox: pulsa **Yes** para continuar.
5. **Ready to Install.** Pulsa **Install**. Windows te preguntará si permites que el programa haga cambios en el equipo: pulsa **Sí**.
6. **Seguridad de Windows.** Pueden aparecer una o varias ventanas preguntando si quieres instalar software de dispositivo de **Oracle Corporation**. Son los controladores de red y USB: pulsa **Instalar** en todas.
7. **Oracle VirtualBox installation is complete.** Deja marcada la casilla para abrir VirtualBox y pulsa **Finish**.

> [!IMPORTANT]
> Si al ejecutar el instalador aparece un aviso de que falta **Microsoft Visual C++ 2019 Redistributable**, descárgalo de la web de Microsoft (el archivo de 64 bits, `vc_redist.x64.exe`, desde [aka.ms/vs/17/release/vc_redist.x64.exe](https://aka.ms/vs/17/release/vc_redist.x64.exe)), instálalo, reinicia y vuelve a ejecutar el instalador de VirtualBox.

## El primer arranque

Al abrir VirtualBox por primera vez verás la ventana principal vacía, sin ninguna máquina. En una instalación nueva VirtualBox arranca en **modo básico**, que muestra menos opciones para no abrumarte. Puedes cambiar al **modo experto** cuando quieras desde [Preferencias](04-preferencias.md).

> [!NOTE]
> Las capturas de esta guía están hechas en **modo experto**, porque es el que enseña todas las opciones. Cuando algo solo aparece en ese modo, la guía lo indica.

El idioma se elige automáticamente según el de tu Windows. Si te sale en inglés, cámbialo en **File** → **Preferences** → **Language** (lo verás en el [capítulo 4](04-preferencias.md#idioma)).

## Actualizar a una versión nueva

Para actualizar, descarga el instalador nuevo y ejecútalo encima de la versión que tienes: **tus máquinas virtuales no se borran**. Antes de hacerlo:

1. Apaga todas las máquinas virtuales (no las dejes en estado guardado).
2. Cierra VirtualBox.
3. Si tenías el **Extension Pack**, después de actualizar instala también el de la versión nueva: tienen que coincidir exactamente.
4. Si tus máquinas tienen instalados los **complementos del invitado**, actualízalos dentro de cada una (menú **Dispositivos** de la ventana de la máquina, ver el [capítulo 10](10-usar-una-maquina.md#los-complementos-del-invitado)).

---

<!-- nav -->
<div align="center">

[⬅️ 1 · Conceptos básicos](01-conceptos-basicos.md) &nbsp;·&nbsp; [🏠 Índice](../README.md) &nbsp;·&nbsp; [3 · La ventana principal ➡️](03-ventana-principal.md)

</div>
