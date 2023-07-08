# project-potential-area

Project ini dibuat dengan menggunakan banyak metodologi Spatial Analysist, library yang digunakan diantaranya yaitu ArcPy dan Geopandas.
Data yang digunakan yaitu : - Favorite Place Google Maps, dan BPS Demografi Data

Data Diolah menggunakan metode sederhana yaitu : Agregasi data terhadap batasan polygon hexagone, Klasifikasi data berdasarkan range, dan Spatial Join 

## Pengolahan data di Postgree SQL 
Data diolah menggunakan function st_geometry untuk mengagregasikan data ke dalam batasan polygon

'''

	update beben.sde.Hexagon_Map_All_Days c
	set tk_negeri=sub.sum1,
	tk_swasta=sub.sum2,
	sd_negeri=sub.sum3,
	sd_swasta=sub.sum4,
	smp_negeri=sub.sum5,
	smp_swasta=sub.sum6,
	sma_negeri=sub.sum7,
	sma_swasta=sub.sum8,
	jml_penduduk=sub.sum9,
	jml_kk=sub.sum10,
	wanita=sub.sum11,
	pria=sub.sum12,
	tidak_bekerja=sub.sum13,
	asn_pns=sub.sum14,
	tenaga_pengajar=sub.sum15,
	wiraswasta=sub.sum16,
	petani=sub.sum17,
	nelayan=sub.sum18,
	pelajar=sub.sum19,
	tenaga_medis=sub.sum20,
	pensiunan=sub.sum21,
	pekerjaan_lainnya=sub.sum22,
	pop_ses_a=sub.sum23,
	pop_ses_b=sub.sum24,
	pop_ses_c=sub.sum25,
	pop_ses_d=sub.sum26,
	pop_ses_e=sub.sum27,
	pop_dominan_ses=sub.sum28,
	hh_ses_a=sub.sum29,
	hh_ses_b=sub.sum30,
	hh_ses_c=sub.sum31,
	hh_ses_d=sub.sum32,
	hh_ses_e=sub.sum33,
	hh_dominan_ses=sub.sum34,
	jml_mobil=sub.sum35,
	jml_bus=sub.sum36,
	jml_truk=sub.sum37,
	jml_motor=sub.sum38
	
	
	from
	(
		select
		b.objectid,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_pd19_tk_n) sum1,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_pd19_tk_s) sum2,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_pd19_sd_n) sum3,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_pd19_sd_s) sum4,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_pd19_smp_n) sum5,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_pd19_smp_s) sum6,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_pd19_smu_n) sum7,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_pd19_smu_s) sum8,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_d19_jumlah_pen) sum9,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_d19_jumlah_kk) sum10,
	    	SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_d19_wanita) sum11,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_d19_pria) sum12,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_d19_belum_tida) sum13,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_d19_aparatur_p) sum14,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_d19_tenaga_pen) sum15,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_d19_wiraswasta) sum16,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_d19_pertanian_) sum17,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_d19_nelayan) sum18,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_d19_pelajar_ma) sum19,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_d19_tenaga_kes) sum20,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_d19_pensiunan) sum21,
	    SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_d19_lainnya) sum22,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_sen19_pop_a) sum23,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_sen19_pop_b) sum24,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_sen19_pop_c) sum25,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_sen19_pop_d) sum26,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_sen19_pop_e) sum27,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_sen19_pop_dses) sum28,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_sen19_kk_a) sum29,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_sen19_kk_b) sum30,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_sen19_kk_c) sum31,
	    SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_sen19_kk_d) sum32,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_sen19_kk_e) sum33,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_sen19_kk_dses) sum34,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_lls2021_mobil) sum35,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_lls2021_bus) sum36,
	    SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_lls2021_truk) sum37,
		SUM(ST_AREA(ST_INTERSECTION(a.shape, b.shape))/ST_AREA(a.shape)*a.first_lls2021_motor) sum38
	
	
		from beben.sde.bps_data a
		join beben.sde.Hexagon_Map_All_Days b
		on st_intersects(a.shape,b.shape)='t'
		group by b.objectid
	) as sub
	where sub.objectid=c.objectid;

'''

## Pengolahan Data di ArcGIS 
Data diolah untuk mendapatkan data dasar berupa "Generate Polygon Hexagon"


## Spatial Analysist use ArcPy
Pengolahan dengan bantuan function dari ArcPy, sehingga pengolahan akan lebih cepat karena berjalan di stand alone Script
