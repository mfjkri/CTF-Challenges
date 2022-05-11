# Metadata | Difficulty: Easy

## Description:

This challenges is all about reading metadata of the image `alamak.jpg`.\
The flag can be found in Image Description tag of the metadata which can be extracted using `exif`.

---

## Steps:

1. Using `exif`

```
$ exif alamak.jpg
```

Outputs:

```
EXIF tags in 'Metadata/Files/alamak.jpg' ('Intel' byte order):
--------------------+----------------------------------------------------------
Tag                 |Value
--------------------+----------------------------------------------------------
Image Description   |flag@179369
X-Resolution        |72
Y-Resolution        |72
Resolution Unit     |Inch
Exif Version        |Exif Version 2.1
FlashPixVersion     |FlashPix Version 1.0
Color Space         |Uncalibrated
GPS Tag Version     |2.2.0.0
North or South Latit|N
Latitude            | 1, 17, 26.14
East or West Longitu|E
Longitude           |103, 50, 53.28
Altitude Reference  |Sea level
Altitude            | 0
--------------------+----------------------------------------------------------
```

Flag is found at:

```
Image Description   |flag@179369
```
