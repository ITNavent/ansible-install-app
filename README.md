Install App
=========

Role para instalar aplicaciones en la nube de Navent.

Para instalar una aplicación que corre vía java -jar hay que definir las siguientes variables.

- type_app_install: Tipo de instalación. Ver la sección **Tipos de instalación**
- newrelic_agent: En caso de correr con NewRelic, escribir el llamado al agente de new relic
 
- jvm_arg: Parametros para la JVM. Por ejemplo parámetros de la memoria.
- app_arg: Parámetros de la APP.
- jmx_arg: Parámetros para la JVM trabajar con JMX.

- app_user: En caso que se quiera definir el usuario con la cual corre la aplicación (root es default)

Parámetros de nexus:

- maven_group: Nombre del grupo de maven.
- app_name: Nombre de la app. Es el mismo nombre que usa maven para identificar el Artefacto
- maven_version: Nombre de la versión de maven.
- maven_repository: Nombre del repositorio de maven
- archive_extension: Extensión del artefacto a descargar de nexus. Default: jar

Parámetros de tomcat:

- tomcat_root_home: Directorio donde escribe el archivo de contexto. Deafult: /opt/tomcat/conf/Catalina/localhost

Parámetros de zabbix:
- zabbix_window: Crear una maintenance-window en zabbix para deshabilitar los triggers de health-check (default "no")
- zabbix_hostnames: Hostnames de zabbix a los cuales aplicarles la maintenance window
- zabbix_login_user: Usuario de zabbix
- zabbix_login_password: Password de zabbix
- zabbix_window_name: Nombre de la maintenance-window (Debe ser único por aplicación)
- zabbix_server_url: Url del server de zabbix
- app_port: Puerto al cual esperar para validar que la aplicación esté levantada

Parámetros de newrelic:
- newrelic_deployment: Envia a NewRelic una notificación de deploy.
- newrelic_path: Path donde está el archivo newrelic.jar

El rol lo que hace es:

- Instalar el servicio en supervisor
- Crear los archivos:
    - startup.sh
    - shutdown.sh
    - install.sh
    
## Tipos de instalación
 
- supervisor: Default
- tomcat: Si la variable type_app_install es igual a **tomcat** instala una apliación en un tomcat dejando el contexto como Root. 
- service: Si la variable type_app_install es igual a **service** instala un nuevo servicio con el nombre definido por la variable
    ```app_name``` que ejecuta los scripts startup.sh y shutdown.sh al iniciar y finalizar el servicio. El servicio se inicia
    en la etapa de booteo, pero no cuando se ejecuta el rol. 

## Parámetro agregado
- navent_folder: Se agrega para poder cambiar la carpeta de instalación que por default es 'navent'. Nos sirvió para poder instalar varios jars en una misma instancia para un problema justo donde necesitabamos eso.


