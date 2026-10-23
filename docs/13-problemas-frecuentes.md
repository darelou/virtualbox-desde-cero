# 13 · Problemas frecuentes

Los errores más habituales al empezar con VirtualBox, con su causa y su solución. Si tu problema no está aquí, mira las [trazas](09-herramientas-de-la-maquina/03-trazas.md) de la máquina y busca el código de error (empieza por `VERR_`) en Internet o en los [foros oficiales](https://forums.virtualbox.org/).

**Índice de problemas:**
- [Al instalar falta "Microsoft Visual C++ 2019 Redistributable"](#al-instalar-falta-microsoft-visual-c-2019-redistributable)
- [Error VT-x is not available o AMD-V is disabled](#error-vt-x-is-not-available-o-amd-v-is-disabled)
- [Solo aparecen versiones de 32 bits al crear la máquina](#solo-aparecen-versiones-de-32-bits-al-crear-la-máquina)
- [La máquina va muy lenta o aparece una tortuga verde](#la-máquina-va-muy-lenta-o-aparece-una-tortuga-verde)
- [No bootable medium found](#no-bootable-medium-found)
- [La máquina vuelve a arrancar el instalador](#la-máquina-vuelve-a-arrancar-el-instalador)
- [El ratón o el teclado se quedan atrapados](#el-ratón-o-el-teclado-se-quedan-atrapados)
- [La pantalla es pequeña y no cambia de tamaño](#la-pantalla-es-pequeña-y-no-cambia-de-tamaño)
- [No funciona copiar y pegar ni arrastrar archivos](#no-funciona-copiar-y-pegar-ni-arrastrar-archivos)
- [La máquina no tiene Internet](#la-máquina-no-tiene-internet)
- [Dos máquinas no se ven entre ellas](#dos-máquinas-no-se-ven-entre-ellas)
- [La máquina o un disco aparecen como inaccesibles](#la-máquina-o-un-disco-aparecen-como-inaccesibles)
- [La máquina se cierra sola o no llega a arrancar](#la-máquina-se-cierra-sola-o-no-llega-a-arrancar)
- [Error "already locked for a session"](#error-already-locked-for-a-session)
- [Un USB no aparece en la máquina](#un-usb-no-aparece-en-la-máquina)
- [Las máquinas ocupan demasiado espacio](#las-máquinas-ocupan-demasiado-espacio)
- [Falla la importación de un .ova](#falla-la-importación-de-un-ova)
- [El paquete de extensiones da error](#el-paquete-de-extensiones-da-error)

---

## Al instalar falta "Microsoft Visual C++ 2019 Redistributable"

**Causa:** algunos instaladores de VirtualBox 7 no incluyen esta pieza de Microsoft.

**Solución:** descarga e instala `vc_redist.x64.exe` desde la web de Microsoft ([aka.ms/vs/17/release/vc_redist.x64.exe](https://aka.ms/vs/17/release/vc_redist.x64.exe)), reinicia el ordenador y vuelve a ejecutar el instalador de VirtualBox.

## Error VT-x is not available o AMD-V is disabled

Mensajes como `VT-x is not available (VERR_VMX_NO_VMX)` o `AMD-V is disabled in the BIOS (VERR_SVM_DISABLED)`.

**Causa:** la virtualización por hardware está desactivada en la UEFI de tu ordenador.

**Solución:** actívala siguiendo los pasos del [capítulo 2](02-instalar-virtualbox.md#cómo-activarla-si-está-deshabilitada).

## Solo aparecen versiones de 32 bits al crear la máquina

**Causa:** VirtualBox no puede usar la virtualización por hardware: o está desactivada en la UEFI, o la está ocupando Hyper-V (ver el problema siguiente).

**Solución:** comprueba en el Administrador de tareas que la **Virtualización** está **Habilitada** ([capítulo 2](02-instalar-virtualbox.md#comprobar-que-la-virtualización-está-activada)) y revisa el apartado siguiente.

## La máquina va muy lenta o aparece una tortuga verde

En la [barra de estado](10-usar-una-maquina.md#la-barra-de-estado), el icono de características muestra una **tortuga verde** en lugar de una **V**.

**Causa:** en tu Windows está activo **Hyper-V** o alguna función que lo usa por debajo: **Plataforma de máquina virtual** (la necesita WSL 2), **Espacio aislado de Windows**, o la **Integridad de memoria** de *Seguridad de Windows → Seguridad del dispositivo → Aislamiento del núcleo*. Entonces VirtualBox no puede usar el procesador directamente y tiene que pasar por Hyper-V, que es mucho más lento.

**Soluciones:**

1. Comprueba primero lo más sencillo: que no tengas demasiadas máquinas encendidas y que la máquina tenga suficiente memoria y procesadores ([Sistema](08-configuracion/02-sistema.md)).
2. Si usas WSL 2, Docker Desktop o el Espacio aislado de Windows, **necesitan Hyper-V**: tendrás que elegir entre esas herramientas y la máxima velocidad de VirtualBox.
3. Si no los usas, puedes desactivar Hyper-V. En Windows busca **Activar o desactivar las características de Windows** y desmarca **Hyper-V**, **Plataforma de máquina virtual** y **Plataforma del hipervisor de Windows**. Reinicia.

> [!WARNING]
> La **Integridad de memoria** es una protección de seguridad de Windows. Desactivarla hace tu ordenador algo más vulnerable. **En un ordenador de empresa o de un centro educativo no la toques sin permiso del departamento de informática.**

## No bootable medium found

La máquina arranca y muestra `FATAL: No bootable medium found! System halted.`

**Causa:** la máquina no encuentra nada desde lo que arrancar: el disco está vacío (no has instalado el sistema) y no hay ninguna ISO en la unidad óptica.

**Solución:** apaga la máquina, mete la ISO del sistema en [Almacenamiento](08-configuracion/04-almacenamiento.md#tareas-frecuentes) y comprueba que **Óptica** está marcada en el [orden de arranque](08-configuracion/02-sistema.md#placa-base).

## La máquina vuelve a arrancar el instalador

**Causa:** la ISO del instalador sigue puesta y la unidad óptica arranca antes que el disco duro.

**Solución:** cuando termine la instalación, saca la ISO: **Dispositivos** → **Unidades ópticas** → **Remove Disk From Virtual Drive** (o desde [Almacenamiento](08-configuracion/04-almacenamiento.md#tareas-frecuentes)).

## El ratón o el teclado se quedan atrapados

**Causa:** la máquina ha capturado el ratón y el teclado (es normal si no tiene los complementos del invitado).

**Solución:** pulsa una vez la **tecla anfitrión**, que es **Ctrl derecha** ([capítulo 10](10-usar-una-maquina.md#la-tecla-anfitrión)). Para que no vuelva a pasar, instala los [complementos del invitado](10-usar-una-maquina.md#los-complementos-del-invitado) y usa **Tableta USB** como [dispositivo apuntador](08-configuracion/02-sistema.md#placa-base).

## La pantalla es pequeña y no cambia de tamaño

**Causa:** faltan los complementos del invitado, o el controlador gráfico no es el adecuado.

**Solución:**
1. Instala los [complementos del invitado](10-usar-una-maquina.md#los-complementos-del-invitado) y reinicia la máquina.
2. Comprueba el [controlador gráfico](08-configuracion/03-pantalla.md#pantalla): **VMSVGA** para Linux, **VBoxSVGA** para Windows.
3. Activa **Ver** → **Autoredimensionar pantalla del invitado**.
4. Mientras tanto, puedes usar **Ver** → **Modo escalado** (**Host + C**) o **Ver** → **Pantalla virtual 1** para cambiar la resolución.

## No funciona copiar y pegar ni arrastrar archivos

**Causa:** el portapapeles compartido está **Inhabilitado** (es lo que viene por defecto) o faltan los complementos del invitado.

**Solución:** instala los complementos del invitado y en la ventana de la máquina elige **Dispositivos** → **Portapapeles compartido** → **Bidireccional** (y lo mismo en **Arrastrar y soltar**).

## La máquina no tiene Internet

Comprueba, en este orden:

1. En [Configuración → Red](08-configuracion/06-red.md), que el adaptador está **habilitado**, con **Cable conectado** marcado y conectado a **NAT** o **Red NAT** (la **Red interna** y la **Sólo anfitrión** no tienen Internet).
2. Que **tu ordenador** tiene Internet.
3. Dentro de la máquina, que la tarjeta ha recibido una IP (`ip a` en Linux, `ipconfig` en Windows). En NAT debería ser `10.0.2.15`.
4. Si usas una **VPN** en tu ordenador, desconéctala y prueba otra vez: algunas VPN bloquean el tráfico de las máquinas virtuales.
5. Si usas **Adaptador puente** con Wi-Fi, prueba con **NAT**: algunas redes Wi-Fi no aceptan equipos puenteados.

## Dos máquinas no se ven entre ellas

**Causa:** están en **NAT** (en NAT cada máquina está aislada en su propia red) o en redes distintas.

**Solución:** conéctalas a la **misma** **Red NAT**, **Red interna** (con el mismo nombre) o red **Sólo anfitrión**. Ver [Las redes explicadas](11-redes-explicadas.md). En una red interna, recuerda ponerles una IP fija a mano. Si aun así no se ven, revisa el cortafuegos dentro de cada sistema.

## La máquina o un disco aparecen como inaccesibles

**Causa:** sus archivos se han movido, borrado, o estaban en un disco externo que no está conectado.

**Solución:**
- Si estaban en un disco externo, conéctalo y usa **Máquina** → **Actualizar**.
- Si moviste la carpeta a mano, quita la máquina de la lista (**Eliminar** → **Solo borrar**) y vuelve a [añadirla](07-anadir-importar-exportar.md#añadir-una-máquina-que-ya-existe) desde su nueva ubicación.
- Para un disco suelto, ver [Un disco inaccesible](05-herramientas-globales/02-medio.md#un-disco-inaccesible).

## La máquina se cierra sola o no llega a arrancar

Mensajes como *The virtual machine has terminated unexpectedly* o *Failed to open a session for the virtual machine*.

**Solución:**
1. Abre las [trazas](09-herramientas-de-la-maquina/03-trazas.md) de la máquina y busca `error`, `failed` o `VERR_` en **VBox.log**. Si la máquina ni siquiera llega a arrancar, mira **VBoxHardening.log**.
2. Comprueba que tu ordenador tiene **memoria libre** suficiente para la que le has dado a la máquina.
3. Algunos **antivirus** interfieren con VirtualBox. Prueba a añadir la carpeta de VirtualBox a sus excepciones (en un ordenador de empresa, pídelo al departamento de informática).
4. Reinstala VirtualBox por encima (tus máquinas no se borran).

## Error "already locked for a session"

Mensaje parecido a *The machine 'X' is already locked for a session (or being unlocked)*.

**Causa:** la máquina ya está abierta (quizá en segundo plano, si la arrancaste **sin pantalla**) o un proceso de VirtualBox se ha quedado colgado.

**Solución:** en la ventana principal mira si está **Corriendo** y pulsa **Mostrar**. Si no aparece ninguna ventana, abre el Administrador de tareas, busca **VirtualBoxVM** y finaliza esa tarea. Después vuelve a arrancarla.

## Un USB no aparece en la máquina

1. Comprueba que el [controlador USB](08-configuracion/08-usb.md) está **habilitado** (y elige USB 3.0 si el dispositivo es moderno).
2. Con la máquina encendida, conéctalo desde **Dispositivos** → **USB** y haz clic en el dispositivo.
3. Si tu ordenador lo está usando (por ejemplo, una memoria con un archivo abierto), ciérralo antes.
4. Si no aparece en la lista, reinstala VirtualBox asegurándote de que **USB Support** está marcado.

## Las máquinas ocupan demasiado espacio

- Elimina las [instantáneas](09-herramientas-de-la-maquina/02-instantaneas.md) que ya no necesites (su espacio se recupera).
- Descarta los estados guardados que no te hagan falta.
- Borra los `.ova`, `.7z` e ISO que ya no uses ([qué se puede borrar](12-tipos-de-archivo.md#qué-se-puede-borrar-y-qué-no)).
- [Mueve](07-anadir-importar-exportar.md#mover-una-máquina) las máquinas a un disco más grande.
- Recuerda que los discos dinámicos **no se reducen solos** cuando borras archivos dentro de la máquina.

## Falla la importación de un .ova

- **Espacio insuficiente:** el disco importado ocupa bastante más que el `.ova` (en el ejemplo, 3,65 GB pasaron a 7,49 GB).
- **El archivo está dañado:** si el error habla del *manifest* o de sumas de comprobación (*digest*), vuelve a descargar el `.ova`.
- **Viene de VMware:** a veces hay que cambiar después el controlador de disco o la tarjeta de red en la configuración para que el sistema arranque.

## El paquete de extensiones da error

**Causa:** su versión no coincide **exactamente** con la de VirtualBox.

**Solución:** mira tu versión en **Ayuda** → **Acerca de VirtualBox...**, descarga el paquete de esa misma versión e instálalo desde [Extensiones](05-herramientas-globales/01-extensiones.md).

---

<!-- nav -->
<div align="center">

[⬅️ 12 · Tipos de archivo](12-tipos-de-archivo.md) &nbsp;·&nbsp; [🏠 Índice](../README.md) &nbsp;·&nbsp; [14 · Glosario ➡️](14-glosario.md)

</div>
