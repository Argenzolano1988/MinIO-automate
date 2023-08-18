Configuración e Instalación de MinIO
====================================

Este script de shell está diseñado para configurar e instalar el servidor de almacenamiento MinIO Multi Nodo en un sistema Linux RHEL. MinIO es un sistema de almacenamiento de objetos de alto rendimiento, compatible con Amazon S3. El script realiza los siguientes pasos:

Requisitos
----------

*   Se debe ejecutar este script como superusuario (root).
*   Se asume que ya tienes el archivo RPM de MinIO (minio.rpm) en el directorio actual.

Instrucciones
-------------

1.  **Ejecución del Script**
    
    Ejecuta el script con privilegios de superusuario:
    
    ```bash
    chmod +x ./install
    sudo ./install
    ```
    
2.  **Configuración de MinIO**
    
    El script comenzará pidiendo varios valores de configuración relacionados con MinIO:
    
    *   **Usuario admin de MinIO**: Ingresa el nombre de usuario para el administrador de MinIO.
    *   **Contraseña del usuario admin de MinIO**: Ingresa la contraseña para el usuario administrador de MinIO (por ejemplo, minioadmin).
    *   **Dominio de instalación**: Proporciona el dominio de instalación, por ejemplo, `test.ejemplo.com.ar` o `ejemplo.com`.
    *   **Carpeta de datos de MinIO**: Ingresa el nombre de la carpeta donde se almacenarán los datos de MinIO (por ejemplo, `minio`).
3.  **Creación de Usuarios y Carpetas**
    
    El script creará un usuario `minio-user` y varias carpetas en función de la configuración proporcionada.
    
4.  **Montaje de Discos**
    
    El script montará unidades XFS utilizando los discos y unidades especificados en las matrices `DISK` y `UNIT`.
    
5.  **Instalación de MinIO**
    
    El script instalará MinIO desde el archivo RPM local proporcionado (`minio.rpm`) y dará permisos ejecutables al binario MinIO.
    
6.  **Creación de Archivo de Entorno**
    
    El script creará un archivo de entorno en `/etc/default/minio` con la configuración necesaria para el servidor MinIO. El archivo contendrá detalles sobre volúmenes, opciones de servidor, usuario y contraseña.
    
7.  **Creación de Archivo de Servicio systemd**
    
    El script creará un archivo de servicio systemd en `/etc/systemd/system/minio.service` para administrar el servicio MinIO. El archivo contiene configuraciones de ejecución, usuario y grupo, entre otras.
    
8.  **Habilitación y Arranque del Servicio MinIO**
    
    El script habilitará y arrancará el servicio MinIO utilizando `systemctl`. Luego, verificará si el servicio se inició correctamente.
    

Notas
-----

*   Asegúrate de haber proporcionado todos los valores de configuración requeridos de manera precisa.
*   El script monta los discos utilizando `mount` y asume que los dispositivos de disco son `/dev/sdb`, `/dev/sdc`, etc. Asegúrate de que estos dispositivos sean correctos para tu sistema.
*   Es posible que debas ajustar algunos valores en el script según tus necesidades específicas.
*   Antes de ejecutar el script en un entorno de producción, te recomendamos que lo entiendas completamente y hagas pruebas en un entorno de desarrollo o de prueba.

Recuerda que este script solo proporciona una guía básica de cómo funciona el proceso de configuración e instalación de MinIO. Pueden existir cambios o actualizaciones en las versiones futuras de MinIO o en los sistemas operativos que no estén reflejados aquí. 