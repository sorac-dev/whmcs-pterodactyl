## WHMCS

Módulo WHMCS para el [Panel Pterodactyl](https://github.com/pterodactyl/panel/).

## Soporte de configuración

Por favor, utiliza el [Discord de Pterodactyl](https://discord.gg/pterodactyl) para soporte relacionado con la configuración en lugar de los issues de GitHub.

## NOTA

Este módulo requiere que el panel esté en la versión 1.0.0 o superior. Si necesitas uno para las versiones 0.7.x, revisa la [rama 0.7.](https://github.com/pterodactyl/whmcs/tree/0.7)

## Instalación

[Tutorial en Video](https://www.youtube.com/watch?v=wURpRD9vfj4) (usa la versión 0.7 del panel pero no ha cambiado nada en cuanto a funcionalidad)

1. Descarga/Clona este repositorio.
2. Mueve la carpeta ``pterodactyl/`` a ``<ruta a whmcs>/modules/servers/``.
3. Crea Credenciales API con estos permisos: ![Imagen](https://i.imgur.com/oeoTyBO.png)
4. En WHMCS 8+ navega a Configuración del Sistema → Servidores. En WHMCS 7 o inferior navega a Configuración → Productos/Servicios → Servidores.
5. Crea un nuevo servidor, llena el nombre con lo que desees, el nombre del host como la URL del panel ya sea como IP o dominio. Por ejemplo: ``123.123.123.123`` o ``mi.pterodactyl.panel``
6. Cambia el Tipo de Servidor a Pterodactyl, deja el nombre de usuario vacío, llena el campo de contraseña con tu clave API generada.
7. Marca la opción "Seguro" si tu panel está usando SSL.
8. Confirma que todo funciona haciendo clic en el botón Probar Conexión -> Guardar Cambios.
9. Regresa a la pantalla de Servidores y presiona Crear Nuevo Grupo, nómbralo como desees y elige el servidor creado y presiona el botón Añadir, Guardar Cambios.
10. Navega a Configuración > Productos/Servicios > Productos/Servicios.
11. Crea tu producto deseado (y grupo de productos si aún no lo has hecho) con el tipo Otro y nombre del producto como desees -> Continuar.
12. Haz clic en la pestaña Configuración del Módulo, elige como Nombre del Módulo Pterodactyl y para el Grupo de Servidores el grupo que creaste en el paso 8.
13. Llena todos los campos no opcionales, ¡y listo!

## Créditos

[Dane](https://github.com/DaneEveritt) y [todos los demás](https://github.com/Pterodactyl/Panel/graphs/contributors) involucrados en el desarrollo del Panel Pterodactyl.
[death-droid](https://github.com/death-droid) por el módulo WHMCS original.
[Crident](https://crident.com) por proporcionarme un entorno de desarrollo para probar el módulo y el video de instalación.

# FAQ

## Migrar desde el módulo de death-droid

Migrar es simple, elimina el módulo de death-droid y luego sube este en su lugar.
Luego haz los pasos 3-6 en las instrucciones de Instalación arriba y reconfigura todos los productos.

## Sobrescribir valores a través de opciones configurables

Sobrescribir valores se puede hacer a través de Opciones Configurables o Campos Personalizados.

Sus nombres deben ser exactamente lo que deseas sobrescribir.
dedicated_ip => Sobrescribirá dedicated_ip si está marcado o no.
Opciones válidas: ``server_name, memory, swap, io, cpu, disk, nest_id, egg_id, pack_id, location_id, dedicated_ip, port_range, image, startup, databases, allocations, backups, oom_disabled, username``

Esto también funciona para cualquier nombre de variable de entorno:
Player Slots => Sobrescribirá la variable de entorno llamada "Player Slots" a su valor.

Truco útil: Puedes usar el separador | para cambiar el nombre visible de la variable así:
dedicated_ip|Dedicated IP => Se mostrará como "Dedicated IP" pero funcionará correctamente.

[Configuración de ejemplo para memoria configurable](https://owo.whats-th.is/85JwhVX.png)

## No se encontraron nodos que satisfagan la solicitud

Esto puede ser causado por cualquiera de los siguientes: Ubicación incorrecta, no hay suficiente espacio en disco/CPU/RAM, o no hay asignaciones que coincidan con los criterios proporcionados.

## El campo de nombre de usuario/contraseña está vacío, ¿cómo obtiene el usuario las credenciales?

El cliente recibe un correo del panel para configurar su cuenta (incl. contraseña) si no tenía una cuenta antes. De lo contrario, debería poder usar sus credenciales existentes.

## El cliente no recibió ningún correo del panel

Verifica que hayas configurado correctamente los ajustes de correo del panel, que el botón de Prueba funciona en la configuración de correo del área de administración, y que has reiniciado pteroq después confirmando que todo funciona.

## Mi juego requiere múltiples puertos asignados

Actualmente, esto no es posible con este módulo pero está planeado.

## El servidor se asigna al primer usuario/administrador del panel en lugar del usuario que ordenó el servicio

Por favor, actualiza tu módulo (redescargándolo).

## El campo feature_limits.backups debe estar presente

Por favor, actualiza tu módulo (redescargándolo).

## Cómo habilitar el registro de depuración del módulo

1. En WHMCS 7 o inferior navega a Utilidades > Registros > Registro del Módulo. Para WHMCS 8.x navega a Registros del Sistema > Registro del Módulo en la barra lateral izquierda.
2. Haz clic en el botón Habilitar Registro de Depuración.
3. Realiza la acción que falló nuevamente y tendrás los registros necesarios para depurar el problema. Todos los errores 404 pueden ser ignorados.
4. Recuerda Deshabilitar el Registro de Depuración si estás usando esto en producción, ya que no se recomienda tenerlo habilitado.
