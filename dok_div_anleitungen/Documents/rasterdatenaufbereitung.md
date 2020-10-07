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
gdal_translate -b 1 -b 2 -b 3 -b mask -of COG --config GDAL_DISABLE_READDIR_ON_OPEN TRUE\
  -co COMPRESS=JPEG -co BIGTIFF=YES -co NUM_THREADS=4 -a_srs EPSG:2056\
  ch.swisstopo.orthofoto_2018.rgb.vrt ch.swisstopo.orthofoto_2018.rgb.tif
```

`-co PHOTOMETRIC=YCBR` (implizit gesetzt bei COG und JPEG mit 3 Kanälen) erlaubt noch besser komprimierte JPEG-Bilder ([using it make the size of the image typically
2 to 3 times smaller than the default value for photometric interpretation (RGB)](http://erouault.blogspot.com/2014/04/advanced-jpeg-in-tiff-uses-in-gdal.html)),
Das 4. Band (-b mask) ist eine 1-bit Maske für NODATA-Werte ausserhalb der Bilddaten.

Erstellung von Pyramiden in Orthofoto-GeoTIFF-Dateien (dieser Schritt ist bei -of COG nicht mehr nötig):

```
gdaladdo -r mode --config COMPRESS_OVERVIEW JPEG --config PHOTOMETRIC_OVERVIEW YCBCR --config INTERLEAVE_OVERVIEW PIXEL\
  --config BIGTIFF_OVERVIEW YES ch.swisstopo.orthofoto_2018.rgb.tif 2 4 8 16 32 64 128 256 512 1024
```
