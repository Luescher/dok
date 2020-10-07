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
gdal_translate -b 1 -b 2 -b 3 -of GTIFF -ot BYTE --config GDAL_DISABLE_READDIR_ON_OPEN TRUE\
  --config GDAL_TIFF_INTERNAL_MASK YES -co COMPRESS=JPEG -co PHOTOMETRIC=YCbCr -co TILED=YES\
  -co BLOCKXSIZE=512 -co BLOCKYSIZE=512 -co BIGTIFF=YES -co NUM_THREADS=4\
  -a_srs EPSG:2056 ch.swisstopo.orthofoto_2018.rgb.vrt ch.swisstopo.orthofoto_2018.rgb.tif
```

`-co PHOTOMETRIC=YCBR` erlaubt noch besser komprimierte JPEG-Bilder ([using it make the size of the image typically
2 to 3 times smaller than the default value for photometric interpretation (RGB)](http://erouault.blogspot.com/2014/04/advanced-jpeg-in-tiff-uses-in-gdal.html)), erlaubt aber nur 3 Bänder in der Geotiff-Datei. Im Beispiel werden 3 Bänder extrahiert (`-b 1 -b 2 -b 3`),
weil das .vrt-File 4 Bänder (inkl. Alpha-Band) enthält.

Erstellung von Pyramiden in Orthofoto-GeoTIFF-Dateien:

```
gdaladdo -r mode --config COMPRESS_OVERVIEW JPEG --config PHOTOMETRIC_OVERVIEW YCBCR --config INTERLEAVE_OVERVIEW PIXEL\
  --config BIGTIFF_OVERVIEW YES ch.swisstopo.orthofoto_2018.rgb.tif 2 4 8 16 32 64 128 256 512 1024
```
