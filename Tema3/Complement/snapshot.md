# Cómo hacer un snapshot en VirtualBox

[Guía](https://raywoodcockslatest.wordpress.com/2018/02/20/virtualbox-snapshots/)

* Abre **VirtualBox**. En la ventana principal verás la lista de máquinas virtuales. Selecciona la máquina de **Windows**, pero no hace falta entrar todavía.

* Con la máquina seleccionada, busca la zona donde aparecen las opciones de la máquina. Ahí debe aparecer una pestaña o apartado llamado **Snapshots** o **Instantáneas**. En algunas versiones está en la parte superior derecha y en otras puede aparecer como un botón o icono.

* Entra en **Snapshots**. Ahora pulsa en **Take Snapshot** o **Tomar instantánea**. VirtualBox te pedirá un nombre. Escribe por ejemplo:

`Antes de cambios`

* Acepta y espera un momento. Cuando termine, verás que la instantánea ya aparece guardada.

* Ahora puedes iniciar la máquina virtual. Una vez dentro de Windows, crea un archivo en el escritorio, por ejemplo:

`archivo.txt`

Escribe dentro algo como:

`version1`

* Después apaga o deja abierta la máquina, y vuelve a VirtualBox para crear otra instantánea si quieres, o haz primero la instantánea y luego cambia el archivo. Por ejemplo, después del snapshot cambia el contenido del archivo a:

`version2`

* Para restaurar la instantánea, vuelve a la ventana principal de **VirtualBox**. Selecciona otra vez la máquina virtual y entra en **Snapshots**. Verás la instantánea que habías creado. Haz clic derecho sobre ella o selecciónala y pulsa **Restore** o **Restaurar**.

* VirtualBox te preguntará si quieres volver a ese estado. Acepta. Si la máquina estaba encendida, normalmente se apagará o volverá al estado guardado por la instantánea.

* Cuando vuelvas a arrancar Windows, el sistema estará exactamente como estaba en el momento en que hiciste el snapshot. Si el archivo se creó antes del snapshot, volverá a esa versión. Si el cambio se hizo después, desaparecerá al restaurar.

* La idea importante es esta: el snapshot no lo hace NTFS, lo hace **VirtualBox** sobre la máquina completa. Por eso funciona aunque dentro tengas Windows con NTFS.

