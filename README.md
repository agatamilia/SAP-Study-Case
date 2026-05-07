# SAP-Study-Case
					
	Objective				
	Create Table (Maintenance and Transaction Table)				
	Create Custom Data Elements and Domain				
	Create Database Views to Combine Table				
	Create Elementary Search Help				
	Create Program to Maintain Material				
	Create Transaction Code 				
					
					
					
					
	1. Buat Table ZXXX_MATERIAL_CAT				
		TABLE MATERIAL CATEGORY			
	Keperluan Maintenance Data	FIELDNAME	Data Type	Data Elements & Domain Setting	Keterangan
	Buat Table Maintenance Generator (TMG)	IDCAT	CHAR(4)	Gunakan Z Data Element	Primary Key
	Field Ernam , erdat dan erzet akan terisi otomatis saat membuat data baru material cat (Gunakan Event dalam TMG)	DESC	CHAR(20)	Gunakan Z Data Element	
	Isi beberapa data melalui SM30	ERNAM		Gunakan standard Data element ERNAM (Username)	
		ERDAT		Gunakan standard Data element ERDAT (Created Date)	
		ERZET		Gunakan standard Data element ERZET (Created Time)	
					
					
					
	2. Buat Table ZXXX_MATERIAL				
		TABLE MATERIAL  			
	Keperluan Transaksi hanya bisa diinsert or update by program	FIELDNAME	Data Type	Data Elements & Domain Setting	Keterangan
		NOMAT	CHAR(10)	Gunakan Z Data Element	Primary Key, Format: CHAR
		NAME 	CHAR(40)	Gunakan Z Data Element	
		IDCAT	CHAR(4)	Gunakan Data element yang sama di table Material Cat	Bekerja seperi foreign key
		PRICE	CURR (Length 13 Dec 2)	Gunakan Z Data Element	
		CURRY	CUKY	Gunakan standard Data element WAERS	
		WEIGH	QUAN (Lengeh 13 Dec 3)	Gunakan Z Data Element	Berat (Weight)
		MEINS	UNIT	Gunakan standard Data element MEINS	
		STATS	CHAR(10)	Gunakan Z Data Element dan Z Domain Fixed Value	Value: A (Active), I (Inactive)
					
	XXX = Isi Inisial nama				
					
	3. Create Database Views to Combine View Table Material Cat and Material based IDCAT relationship				
		View ZVXXX_MATERIAL	(From Table)		
		NOMAT	TABLE MATERIAL		
		NAME 	TABLE MATERIAL		
		IDCAT	TABLE MATERIAL		
		DESC	TABLE MATERIAL CATEGORY		
		PRICE	TABLE MATERIAL		
		CURRY	TABLE MATERIAL		
		WEIGH	TABLE MATERIAL		
		MEINS	TABLE MATERIAL		
		STATS	TABLE MATERIAL		
					
					
	4. Create 2 Elementary Search Help for Value Table Material Cat & Nomor ID Material	Selection Method	Search Help Parameter		
		ZXXX_MATERIAL_CAT	IDCAT		
	Selection Screen PARAMETERS can use this Searh Help with addition MATCHCODE OBJECT		DESC		
		Selection Method	Search Help Parameter		
		ZXXX_MATERIAL	NOMAT		
			NAMA		
					
					
	Note				
	Selain yang dibuat beberapa poin yang jadi bahan belajar				
	Perbedaan Table, Structure dan Table Type				
	Perbedaan Data Elements dan Domain				
	Apa itu Lock Object				
