# SAP-Study-Case
study case ABAP sandbox

NO	DOC_TYPE	VENDOR	PURCH_ORG	PUR_GROUP	MATERIAL	PLANT	QUANTITY	PO _UNIT	GL_ACCOUNT	BUS_AREA	COSTCENTER	DELIV_DATE
PO1	PM1	53000107	ME01	PU1	448	2000	15	G	1200000006		cc_mm_raw	30042026
PO1	PM1	53000107	ME01	PU1	455	2000	15	G	1200000006		cc_mm_raw	30042026
PO2	PM1	53000107	ME01	PU1	452	2000	15	G	1200000006		cc_mm_raw	30042026


CASE BAPI										
Objective										
Create Conversion Program 										
										
Flow Program										
Upload file can from local or server based template file										
"Display ALV , display validations, action button Check and Post
Check Button -> Run in Test Mode
Post Button -> Run Without Test Mode"										
"Light Indicator Red -> Validation Failed / Error Posting BAPI
Yellow -> Validation Success and Ready Post
Green -> Success Post BAPI

All message will be write in message column ALV"										
										
	Selection Screen									
										
	o	Local Upload		Radio Button						
		Filename		Parameter						
	o	Server 		Radio Button						
		File Path		Parameter						
										
			Upload Immedietly	Checbox						
										
										
										
	FILENAME	TYPE	RLGRAP-FILENAME		Hint: Use FM F4_FILENAME AT SELECTION-SCREEN and FM GUI_UPLOAD	Ex:				
	FILEPATAH	TYPE	CHAR100	Default : usr/sap/HAG/(Filename.csv)	Hint: OPEN DATASET, READ DATASET, CLOSE DATASET					
	UPLOAD IMMEDIETLY	TYPE	AS CHECKBOX	if checked directly call BAPI and Display result in ALV, if not checked display ALV first			TCODE: AL11			
							usr/sap/HAG/Test1.csv			
	Format CSV (Sheet 2)									
										
	FUNCTION BAPI 	"BAPI_PO_CREATE1
Jika Sukses Panggil FM BAPI_TRANSACTION_COMMIT jika gagal BAPI_TRANSACTION_ROLLBACK"								
	Test variant	"
Test Study Case BAPI 3"								
										
	Jika di variant ada namun file upload tidak , isikan default value sesuai di test data function, contoh Payment Term, Profit Center									
										
	DISPLAY ALV									
										
	ICON	Light Indicator	Red : Validasi Gagal / Posting Gagal							
			Yellow : Ready Post							
			Green: Post Berhasil							
	Display all field header & item based Upload									
	Message	String	Excute pertama berisi validasi field2 mandatory jika gagal message akan terisi, jika tidak akan kosong							
			"Setelah Button CHECK / POST ditekan message akan berisi No PO yang terbentuk atau message Error dari BAPI
Multiple Header dapat diexcute dalam satu kali klik button, Jika CHECK maka akan run dalam TEST MODE = X yang mana tidak akan menghasilkan nomor dokumen"							
