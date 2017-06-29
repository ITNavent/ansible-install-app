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

- tomcat_home: Directorio donde escribe el archivo de contexto. Deafult: /opt/tomcat/conf/Catalina/localhost

El rol lo que hace es:

- Instalar el servicio en supervisor
- Crear los archivos:
    - startup.sh
    - shutdown.sh
    - install.sh
    
 ## Tipos de instalación
 
 - supervisor: Default
 - tomcat: Si la variable type_app_install es igual a **tomcat** instala una apliación en un tomcat dejando el contexto como Root. 



