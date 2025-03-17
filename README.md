Python script to parse nmap xml output into influxdb input. Depends on xmltodict (apt-get install python3-xmltodict). Below is sample influxdb input.
```
$ nmap -V
Nmap version 7.93
```
```
$ python3 -V
Python 3.11.2
```
```
$ python3 -c "import xmltodict; print(xmltodict.__version__)"
0.13.0
```
```
run,exit="success" up=25,down=999,total=1024,duration=3700.76 1742075846
result,ip="192.168.4.1",mac="9C:57:BC:C4:DF:12",vendor="eero",proto="tcp",port="53",service="domain" avail=1 1742073911
result,ip="192.168.4.1",mac="9C:57:BC:C4:DF:12",vendor="eero",proto="tcp",port="80",service="http" avail=1 1742073911
result,ip="192.168.4.1",mac="9C:57:BC:C4:DF:12",vendor="eero",proto="tcp",port="1900",service="upnp" avail=1 1742073911
result,ip="192.168.4.1",mac="9C:57:BC:C4:DF:12",vendor="eero",proto="tcp",port="3001",service="nessus" avail=1 1742073911
result,ip="192.168.4.23",mac="18:B4:30:ED:A3:7B",vendor="Nest Labs" avail=1 1742074034
result,ip="192.168.4.25",mac="F8:10:93:D6:48:67",vendor="Apple",proto="tcp",port="49152",service="unknown" avail=1 1742075457
result,ip="192.168.4.25",mac="F8:10:93:D6:48:67",vendor="Apple",proto="tcp",port="62078",service="iphone-sync" avail=1 1742075457
result,ip="192.168.4.26",mac="F0:03:8C:E4:F8:32",vendor="AzureWave Technology",proto="tcp",port="80",service="http" avail=1 1742073587
result,ip="192.168.4.28",mac="60:74:F4:33:59:F8" avail=1 1742073692
result,ip="192.168.4.29",mac="D4:AD:FC:DF:18:C6",vendor="Shenzhen Intellirocks Tech" avail=1 1742074236
result,ip="192.168.4.30",mac="64:52:99:EB:B8:3B",vendor="The Chamberlain Group",proto="tcp",port="80",service="http" avail=1 1742073790
result,ip="192.168.4.30",mac="64:52:99:EB:B8:3B",vendor="The Chamberlain Group",proto="tcp",port="443",service="https" avail=1 1742073790
result,ip="192.168.4.40",mac="80:F3:EF:E6:52:69",vendor="Facebook Technologies" avail=1 1742075846
result,ip="192.168.4.41",mac="54:2A:1B:13:B3:16",vendor="Sonos",proto="tcp",port="1443",service="ies-lm" avail=1 1742073350
result,ip="192.168.4.42",mac="B0:A7:B9:25:E7:78",vendor="TP-Link Limited",proto="tcp",port="9999",service="abyss" avail=1 1742073302
result,ip="192.168.4.43",mac="5C:E9:1E:27:53:28",vendor="Apple",proto="tcp",port="49152",service="unknown" avail=1 1742073655
result,ip="192.168.4.43",mac="5C:E9:1E:27:53:28",vendor="Apple",proto="tcp",port="62078",service="iphone-sync" avail=1 1742073655
result,ip="192.168.4.44",mac="18:B4:30:ED:A9:14",vendor="Nest Labs" avail=1 1742073370
result,ip="192.168.4.45",mac="50:ED:3C:F0:E7:09",vendor="Apple",proto="tcp",port="5000",service="upnp" avail=1 1742073502
result,ip="192.168.4.45",mac="50:ED:3C:F0:E7:09",vendor="Apple",proto="tcp",port="7000",service="afs3-fileserver" avail=1 1742073502
result,ip="192.168.4.48",mac="1C:69:7A:6D:89:A6",vendor="EliteGroup Computer Systems",proto="tcp",port="22",service="ssh" avail=1 1742073736
result,ip="192.168.4.48",mac="1C:69:7A:6D:89:A6",vendor="EliteGroup Computer Systems",proto="tcp",port="80",service="http" avail=1 1742073736
result,ip="192.168.4.48",mac="1C:69:7A:6D:89:A6",vendor="EliteGroup Computer Systems",proto="tcp",port="427",service="svrloc" avail=1 1742073736
result,ip="192.168.4.48",mac="1C:69:7A:6D:89:A6",vendor="EliteGroup Computer Systems",proto="tcp",port="443",service="https" avail=1 1742073736
result,ip="192.168.4.48",mac="1C:69:7A:6D:89:A6",vendor="EliteGroup Computer Systems",proto="tcp",port="902",service="iss-realsecure" avail=1 1742073736
result,ip="192.168.4.48",mac="1C:69:7A:6D:89:A6",vendor="EliteGroup Computer Systems",proto="tcp",port="5988",service="wbem-http" avail=1 1742073736
result,ip="192.168.4.48",mac="1C:69:7A:6D:89:A6",vendor="EliteGroup Computer Systems",proto="tcp",port="5989",service="wbem-https" avail=1 1742073736
result,ip="192.168.4.48",mac="1C:69:7A:6D:89:A6",vendor="EliteGroup Computer Systems",proto="tcp",port="8000",service="http-alt" avail=1 1742073736
result,ip="192.168.4.48",mac="1C:69:7A:6D:89:A6",vendor="EliteGroup Computer Systems",proto="tcp",port="8300",service="tmi" avail=1 1742073736
result,ip="192.168.4.48",mac="1C:69:7A:6D:89:A6",vendor="EliteGroup Computer Systems",proto="tcp",port="9080",service="glrpc" avail=1 1742073736
result,ip="192.168.4.49",mac="00:0C:29:09:CD:73",vendor="VMware",proto="tcp",port="22",service="ssh" avail=1 1742073605
result,ip="192.168.4.49",mac="00:0C:29:09:CD:73",vendor="VMware",proto="tcp",port="8086",service="d-s-n" avail=1 1742073605
result,ip="192.168.4.50",mac="00:0C:29:9E:D6:3E",vendor="VMware",proto="tcp",port="22",service="ssh" avail=1 1742073433
result,ip="192.168.4.51",mac="00:0C:29:ED:31:65",vendor="VMware",proto="tcp",port="22",service="ssh" avail=1 1742073695
result,ip="192.168.4.52",mac="00:0C:29:22:E0:D9",vendor="VMware",proto="tcp",port="22",service="ssh" avail=1 1742073608
result,ip="192.168.4.52",mac="00:0C:29:22:E0:D9",vendor="VMware",proto="tcp",port="3000",service="ppp" avail=1 1742073608
result,ip="192.168.4.70",mac="48:A6:B8:B8:8A:C4",vendor="Sonos",proto="tcp",port="1443",service="ies-lm" avail=1 1742073365
result,ip="192.168.4.70",mac="48:A6:B8:B8:8A:C4",vendor="Sonos",proto="tcp",port="7000",service="afs3-fileserver" avail=1 1742073365
result,ip="192.168.4.197",mac="CC:96:E5:18:34:7D",vendor="Dell" avail=1 1742074251
result,ip="192.168.4.198",mac="08:C2:24:65:61:D0",proto="tcp",port="8009",service="ajp13" avail=1 1742073317
result,ip="192.168.4.208",mac="F0:2F:9E:9C:54:FA",proto="tcp",port="8009",service="ajp13" avail=1 1742073242
result,ip="192.168.4.228",mac="8C:E9:EE:23:49:89" avail=1 1742073998
result,ip="192.168.5.0",mac="00:BB:C1:95:50:5D",vendor="Canon",proto="tcp",port="80",service="http" avail=1 1742073689
result,ip="192.168.5.0",mac="00:BB:C1:95:50:5D",vendor="Canon",proto="tcp",port="443",service="https" avail=1 1742073689
result,ip="192.168.5.0",mac="00:BB:C1:95:50:5D",vendor="Canon",proto="tcp",port="515",service="printer" avail=1 1742073689
result,ip="192.168.5.0",mac="00:BB:C1:95:50:5D",vendor="Canon",proto="tcp",port="631",service="ipp" avail=1 1742073689
result,ip="192.168.4.252",proto="tcp",port="22",service="ssh" avail=1 1742075846
result,ip="192.168.4.252",proto="tcp",port="8086",service="d-s-n" avail=1 1742075846
```
