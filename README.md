# Taller Exiftool

_Haciendo uso de exifttool tome tres tipos diferentes de archivo y:_

1. Elimine toda la metadata.

Para eliminar la metadata de un archivo ingresamos a la carpeta de instalación del programa exifttool y ejecutamos:
- Inicialmente leer la metadata:
```
Windows PowerShell
Copyright (C) Microsoft Corporation. Todos los derechos reservados.

Instale la versión más reciente de PowerShell para obtener nuevas características y mejoras. https://aka.ms/PSWindows

PS F:\DIPLOMADO 2024_PROGRAMAS\exiftool-12.93_64> .\exiftool.exe ".\Taller_clase_FOCA.pdf"
ExifTool Version Number         : 12.93
File Name                       : Taller_clase_FOCA.pdf
Directory                       : .
File Size                       : 487 kB
Zone Identifier                 : Exists
File Modification Date/Time     : 2024:08:27 15:45:42-05:00
File Access Date/Time           : 2024:08:28 14:30:04-05:00
File Creation Date/Time         : 2024:08:28 14:30:04-05:00
File Permissions                : -rw-rw-rw-
File Type                       : PDF
File Type Extension             : pdf
MIME Type                       : application/pdf
PDF Version                     : 1.7
Linearized                      : No
Page Count                      : 7
Language                        : es
Tagged PDF                      : Yes
XMP Toolkit                     : 3.1-701
Producer                        : Microsoft┬« Word para Microsoft 365
Creator                         : DHC. JAIDER OSPINA NAVAS
Creator Tool                    : Microsoft┬« Word para Microsoft 365
Create Date                     : 2024:08:27 12:04:36-05:00
Modify Date                     : 2024:08:27 12:04:36-05:00
Document ID                     : uuid:29EE37EB-C813-49A2-9D53-E64B61E5B537
Instance ID                     : uuid:29EE37EB-C813-49A2-9D53-E64B61E5B537
Author                          : DHC. JAIDER OSPINA NAVAS
```
- Ahora eliminamos la metadata del archivo:
```
PS F:\DIPLOMADO 2024_PROGRAMAS\exiftool-12.93_64> .\exiftool.exe -all=.\Taller_clase_FOCA.pdf
Warning: [minor] ExifTool PDF edits are reversible. Deleted tags may be recovered! - ./Taller_clase_FOCA.pdf
    1 image files updated
´
- Ahora leemos nuevamente la metadata del archivo para validar que fue eliminada:
´
PS F:\DIPLOMADO 2024_PROGRAMAS\exiftool-12.93_64> .\exiftool.exe ".\Taller_clase_FOCA.pdf"
ExifTool Version Number         : 12.93
File Name                       : Taller_clase_FOCA.pdf
Directory                       : .
File Size                       : 487 kB
File Modification Date/Time     : 2024:08:28 14:31:13-05:00
File Access Date/Time           : 2024:08:28 14:31:33-05:00
File Creation Date/Time         : 2024:08:28 14:30:04-05:00
File Permissions                : -rw-rw-rw-
File Type                       : PDF
File Type Extension             : pdf
MIME Type                       : application/pdf
PDF Version                     : 1.7
Linearized                      : No
Page Count                      : 7
Language                        : es
Tagged PDF                      : Yes
```

2. Guarde la metadata en diferentes formatos (HTML, txt y svc ) para su futuro análisis.
3. Modifique los datos de geo-posición con las coordenadas del Planetario de Bogotá.
4. Cambie el copyrigth como propiedad para el Pato Donald.
5. Investigue como extraer la miniatura de una imagen (esto debe estar habilitado en la captura de la misma, caso contrario no es posible). Instale y documente la instalación del interfaz gráfico en Windows. Documente el proceso en github. Tome como referencia https://github.com/FrankBijnen/ExifToolGui?tab=readme-ov-file