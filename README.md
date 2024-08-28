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
-Export to **.html**
```
PS F:\DIPLOMADO 2024_PROGRAMAS\exiftool-12.93_64> .\exiftool.exe -r -all -htmldump .\Taller_Captura.pdf > Taller_Captura.html
```
-Export to **.txt**
```
PS F:\DIPLOMADO 2024_PROGRAMAS\exiftool-12.93_64> .\exiftool.exe -r -all -txt .\Taller_Captura.pdf > Taller_Captura.txt
```
-Export to **.csv**
```
PS F:\DIPLOMADO 2024_PROGRAMAS\exiftool-12.93_64> .\exiftool.exe -r -all -csv .\Taller_Captura.pdf > Taller_Captura.csv
```

3. Modifique los datos de geo-posición con las coordenadas del Planetario de Bogotá.

- Se descarga una imagen del Planetario de Bogotá y se consulta la metadata:
```
PS F:\DIPLOMADO 2024_PROGRAMAS\exiftool-12.93_64> .\exiftool.exe .\Planetario_Bogota.png
ExifTool Version Number         : 12.93
File Name                       : Planetario_Bogota.png
Directory                       : .
File Size                       : 491 kB
Zone Identifier                 : Exists
File Modification Date/Time     : 2024:08:28 15:33:51-05:00
File Access Date/Time           : 2024:08:28 15:33:51-05:00
File Creation Date/Time         : 2024:08:28 15:33:50-05:00
File Permissions                : -rw-rw-rw-
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 1024
Image Height                    : 678
Bit Depth                       : 8
Color Type                      : Palette
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Software                        : Adobe ImageReady
XMP Toolkit                     : Adobe XMP Core 5.3-c011 66.145661, 2012/02/06-14:56:27
Creator Tool                    : Adobe Photoshop CS6 (Windows)
Instance ID                     : xmp.iid:701D5E48A93611EBB65FFC10E86AEC7C
Document ID                     : xmp.did:701D5E49A93611EBB65FFC10E86AEC7C
Derived From Instance ID        : xmp.iid:701D5E46A93611EBB65FFC10E86AEC7C
Derived From Document ID        : xmp.did:701D5E47A93611EBB65FFC10E86AEC7C
Palette                         : (Binary data 768 bytes, use -b option to extract)
Image Size                      : 1024x678
Megapixels                      : 0.694
```
- Ahora vamos agregar nuevos metadatos de geo-posicionamiento:
```
PS F:\DIPLOMADO 2024_PROGRAMAS\exiftool-12.93_64> .\exiftool.exe -GPSLatitude=4.6121881 -GPSLatitudeRef=N -GPSLongitude=-74.0716352 -GPSLongitudeRef=W .\Planetario_Bogota.png
Error: File not found - .6121881
Error: File not found - .0716352
    1 image files updated
    2 files weren't updated due to errors
```
-  Consultamos nuevamente el archivo para consultar los nuevos metadatos:
```
PS F:\DIPLOMADO 2024_PROGRAMAS\exiftool-12.93_64> .\exiftool.exe .\Planetario_Bogota.png
ExifTool Version Number         : 12.93
File Name                       : Planetario_Bogota.png
Directory                       : .
File Size                       : 491 kB
File Modification Date/Time     : 2024:08:28 15:39:25-05:00
File Access Date/Time           : 2024:08:28 15:39:33-05:00
File Creation Date/Time         : 2024:08:28 15:33:50-05:00
File Permissions                : -rw-rw-rw-
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 1024
Image Height                    : 678
Bit Depth                       : 8
Color Type                      : Palette
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Software                        : Adobe ImageReady
XMP Toolkit                     : Adobe XMP Core 5.3-c011 66.145661, 2012/02/06-14:56:27
Creator Tool                    : Adobe Photoshop CS6 (Windows)
Instance ID                     : xmp.iid:701D5E48A93611EBB65FFC10E86AEC7C
Document ID                     : xmp.did:701D5E49A93611EBB65FFC10E86AEC7C
Derived From Instance ID        : xmp.iid:701D5E46A93611EBB65FFC10E86AEC7C
Derived From Document ID        : xmp.did:701D5E47A93611EBB65FFC10E86AEC7C
Palette                         : (Binary data 768 bytes, use -b option to extract)
Exif Byte Order                 : Big-endian (Motorola, MM)
X Resolution                    : 72
Y Resolution                    : 72
Resolution Unit                 : inches
Y Cb Cr Positioning             : Centered
GPS Version ID                  : 2.3.0.0
GPS Latitude Ref                : North
GPS Longitude Ref               : West
Image Size                      : 1024x678
Megapixels                      : 0.694
GPS Latitude                    : 4 deg 0' 0.00" N
GPS Longitude                   : 74 deg 0' 0.00" W
GPS Position                    : 4 deg 0' 0.00" N, 74 deg 0' 0.00" W
```

4. Cambie el copyrigth como propiedad para el Pato Donald.

![](https://github.com/alhemoasde/ciber-forence/blob/main/Planetario_Bogota.png){width='100px'}

- Vamos a agregar © 2024 Pato Donald. Todos los derechos reservados:
```
PS F:\DIPLOMADO 2024_PROGRAMAS\exiftool-12.93_64> .\exiftool.exe -Copyright="@2024 Pato Donald. Todos los derechos reservados." .\Planetario_Bogota.png
    1 image files updated
```
- Ahora consultamos el metadato agregado:
```
PS F:\DIPLOMADO 2024_PROGRAMAS\exiftool-12.93_64> .\exiftool.exe .\Planetario_Bogota.png
ExifTool Version Number         : 12.93
File Name                       : Planetario_Bogota.png
Directory                       : .
File Size                       : 492 kB
File Modification Date/Time     : 2024:08:28 15:52:14-05:00
File Access Date/Time           : 2024:08:28 15:53:34-05:00
File Creation Date/Time         : 2024:08:28 15:33:50-05:00
File Permissions                : -rw-rw-rw-
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 1024
Image Height                    : 678
Bit Depth                       : 8
Color Type                      : Palette
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Software                        : Adobe ImageReady
XMP Toolkit                     : Adobe XMP Core 5.3-c011 66.145661, 2012/02/06-14:56:27
Creator Tool                    : Adobe Photoshop CS6 (Windows)
Instance ID                     : xmp.iid:701D5E48A93611EBB65FFC10E86AEC7C
Document ID                     : xmp.did:701D5E49A93611EBB65FFC10E86AEC7C
Derived From Instance ID        : xmp.iid:701D5E46A93611EBB65FFC10E86AEC7C
Derived From Document ID        : xmp.did:701D5E47A93611EBB65FFC10E86AEC7C
Palette                         : (Binary data 768 bytes, use -b option to extract)
Exif Byte Order                 : Big-endian (Motorola, MM)
X Resolution                    : 72
Y Resolution                    : 72
Resolution Unit                 : inches
Y Cb Cr Positioning             : Centered
GPS Version ID                  : 2.3.0.0
GPS Latitude Ref                : North
GPS Longitude Ref               : West
Copyright                       : @2024 Pato Donald. Todos los derechos reservados.
Image Size                      : 1024x678
Megapixels                      : 0.694
GPS Latitude                    : 4 deg 0' 0.00" N
GPS Longitude                   : 74 deg 0' 0.00" W
GPS Position                    : 4 deg 0' 0.00" N, 74 deg 0' 0.00" W
```

5. Investigue como extraer la miniatura de una imagen (esto debe estar habilitado en la captura de la misma, caso contrario no es posible). Instale y documente la instalación del interfaz gráfico en Windows. Documente el proceso en github. Tome como referencia https://github.com/FrankBijnen/ExifToolGui?tab=readme-ov-file

- Primero se valida que la imagen tenga dentro de su metadata el atributo **-ThumbnailImage*
```
PS F:\DIPLOMADO 2024_PROGRAMAS\exiftool-12.93_64> .\exiftool.exe -ThumbnailImage .\Photo.jpg
Thumbnail Image                 : (Binary data 2302 bytes, use -b option to extract)
```
- Ahora vamos a extraer la imagen de miniatura:
```
PS F:\DIPLOMADO 2024_PROGRAMAS\exiftool-12.93_64> .\exiftool.exe -b -ThumbnailImage .\Photo.jpg > Photo-Thumbnail.jpg
```
