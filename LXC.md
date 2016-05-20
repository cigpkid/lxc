Como funciona LXC

Su funcion es mantener aislado varios sistemas en uno solo.

Teniendo independencia en sus procesos, sistema de archivos y recursos.

Instalación.

Ejecutamos la siguiente linea para instalar la paqueteria necesaria

apt-get install lxc lxctl lxc-templates

![1_instalar_paqueteria.png](/img/1_instalar_paqueteria.png "")

Ahora checamos la configuracion para validar que se instalo bien

lxc-checkconfig

![2_config_lxc.png](/img/2_config_lxc.png "")

Validamos los templates que tenemos disponibles

ls /usr/share/lxc/templates/

![3_templates_lxc.png](/img/3_templates_lxc.png "")

Validamos los procesos init antes de ejecutar un contenedor

ps -aux | grep init

![4_antes_lxc.png](/img/4_antes_lxc.png "")

Creamos contenedor con la siguiente linea

sudo lxc-create -n ubuntu01 -t ubuntu

![5_crear_contenedor_ubuntu01.png](/img/5_crear_contenedor_ubuntu01.png "")

iniciamos y vemos los procesos existentes para ver que hay mas de un init

sudo lxc-start -n ubuntu01 -d

ps -aux | grep init

![6_iniciamos_contenedor_vemos_nuevo_init.png](/img/6_iniciamos_contenedor_vemos_nuevo_init.png "")

Nos logueamos al contenedor y vemos los procesos

sudo lxc-console -n ubuntu01

ps -aux | grep init

![8_dentro_diferentes procesos y su propioinit.png](/img/8_dentro_diferentes procesos y su propioinit.png "")

Se crea un segundo contenedor abriendo en una nueva terminal y vemos sus procesos

![10_despuessegunda instancia.png](/img/10_despuessegunda instancia.png "")

Como se puede observar sus procesos son independientes entre si, y solo el SO linux principal ve los procesos de los contenedores.



