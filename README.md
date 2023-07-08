# project-potential-area

Project ini dibuat dengan menggunakan banyak metodologi Spatial Analysist, library yang digunakan diantaranya yaitu ArcPy dan Geopandas.
Data yang digunakan yaitu : - Favorite Place Google Maps, dan BPS Demografi Data

Data Diolah menggunakan metode sederhana yaitu : Agregasi data terhadap batasan polygon hexagone, Klasifikasi data berdasarkan range, dan Spatial Join 

## Pengolahan data di Postgree SQL 
Data diolah menggunakan function st_geometry untuk mengagregasikan data ke dalam batasan polygon


## Pengolahan Data di ArcGIS 
Data diolah untuk mendapatkan data dasar berupa "Generate Polygon Hexagon"

## Spatial Analysist use ArcPy
Pengolahan dengan bantuan function dari ArcPy, sehingga pengolahan akan lebih cepat karena berjalan di stand alone Script
