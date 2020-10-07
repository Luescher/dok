# Rasterdatenaufbereitung
Verantwortlicher: Andreas Neumann

## Beschreibung
Rasterdatenaufbereitung mit GDAL. Getrennt nach Datentypen wird hier aufgezeigt wie Rasterdaten optimiert werden können.
 
### Auslöser
Bei Bedarf, wenn neue Rasterdaten geliefert werden.

## Arbeitsablauf
### Aufbereitung von Orthofotos

Hier die sinnvollen Konvertierungseinstellungen für RGB-Orthofotos:

```
gdal_translate -b 1 -b 2 -b 3 -ot BYTE --config GDAL_DISABLE_READDIR_ON_OPEN TRUE -of GTIFF\
  -co COMPRESS=JPEG -co PHOTOMETRIC=YCBCR -co GDAL_TIFF_INTERNAL_MASK=TRUE -co TILED=YES\
  -co BLOCKXSIZE=512 -co BLOCKYSIZE=512 -co BIGTIFF=YES -co NUM_THREADS=4\
  -a_srs EPSG:2056 ch.swisstopo.orthofoto_2018.rgb.vrt ch.swisstopo.orthofoto_2018.rgb.tif
```

`-co PHOTOMETRIC=YCBR` erlaubt noch besser komprimierte JPEG-Bilder, erlaubt aber nur 3 Bänder in der
Geotiff-Datei. Im Beispiel werden 3 Bänder extrahiert (`-b 1 -b 2 -b 3`), weil das .vrt-File 4 Bänder (inkl. Alpha-Band) enthält.
