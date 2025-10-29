#appserver #jobboss #edi 


WinSCP
[Instructions to Automate file transfers](https://winscp.net/eng/docs/guide_automation)

#tasks
Task Scheduler
Import EDI
	"C:\Program Files (x86)\1 EDI Source, Inc\EDI HQ\EDIHQ.exe"
	Arguments   "/DS:Warren EDI" "/Job:Import EDI"
Upload-Download EDI
		"C:\Program Files (x86)\WinSCP\uploadedi.bat"
		"C:\Program Files (x86)\WinSCP\downloadedi.bat"