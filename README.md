Python script to parse nmap xml output (nmap.xml) into influxdb input. Depends on xmltodict (apt-get install python3-xmltodict). Below is sample influxdb input.
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
run,exit=success up=27,down=997,total=1024,duration=1149.36 1742343550
result,ip=192.168.4.1,mac=9C:57:BC:C4:DF:12,proto=tcp,port=53,service=domain vendor="eero",avail=1 1742343295
result,ip=192.168.4.1,mac=9C:57:BC:C4:DF:12,proto=tcp,port=80,service=http vendor="eero",avail=1 1742343295
result,ip=192.168.4.1,mac=9C:57:BC:C4:DF:12,proto=tcp,port=1900,service=upnp vendor="eero",avail=1 1742343295
result,ip=192.168.4.1,mac=9C:57:BC:C4:DF:12,proto=tcp,port=3001,service=nessus vendor="eero",avail=1 1742343295
result,ip=192.168.4.23,mac=18:B4:30:ED:A3:7B vendor="Nest Labs",avail=1 1742342870
result,ip=192.168.4.26,mac=F0:03:8C:E4:F8:32,proto=tcp,port=80,service=http vendor="AzureWave Technology",avail=1 1742343165
result,ip=192.168.4.28,mac=60:74:F4:33:59:F8 avail=1 1742342836
result,ip=192.168.4.29,mac=D4:AD:FC:DF:18:C6 vendor="Shenzhen Intellirocks Tech",avail=1 1742342692
result,ip=192.168.4.30,mac=64:52:99:EB:B8:3B,proto=tcp,port=80,service=http vendor="The Chamberlain Group",avail=1 1742343183
result,ip=192.168.4.30,mac=64:52:99:EB:B8:3B,proto=tcp,port=443,service=https vendor="The Chamberlain Group",avail=1 1742343183
result,ip=192.168.4.33,mac=9C:A5:70:6E:F2:8D,proto=tcp,port=53,service=domain vendor="eero",avail=1 1742342942
result,ip=192.168.4.33,mac=9C:A5:70:6E:F2:8D,proto=tcp,port=3001,service=nessus vendor="eero",avail=1 1742342942
result,ip=192.168.4.39,mac=CC:96:E5:18:34:B2 vendor="Dell",avail=1 1742343550
result,ip=192.168.4.41,mac=54:2A:1B:13:B3:16,proto=tcp,port=1443,service=ies-lm vendor="Sonos",avail=1 1742342481
result,ip=192.168.4.42,mac=B0:A7:B9:25:E7:78,proto=tcp,port=9999,service=abyss vendor="TP-Link Limited",avail=1 1742342595
result,ip=192.168.4.43,mac=5C:E9:1E:27:53:28,proto=tcp,port=83,service=mit-ml-dev vendor="Apple",avail=1 1742343124
result,ip=192.168.4.43,mac=5C:E9:1E:27:53:28,proto=tcp,port=340,service=unknown vendor="Apple",avail=1 1742343124
result,ip=192.168.4.43,mac=5C:E9:1E:27:53:28,proto=tcp,port=417,service=onmux vendor="Apple",avail=1 1742343124
result,ip=192.168.4.43,mac=5C:E9:1E:27:53:28,proto=tcp,port=427,service=svrloc vendor="Apple",avail=1 1742343124
result,ip=192.168.4.43,mac=5C:E9:1E:27:53:28,proto=tcp,port=683,service=corba-iiop vendor="Apple",avail=1 1742343124
result,ip=192.168.4.43,mac=5C:E9:1E:27:53:28,proto=tcp,port=1085,service=webobjects vendor="Apple",avail=1 1742343124
result,ip=192.168.4.43,mac=5C:E9:1E:27:53:28,proto=tcp,port=1717,service=fj-hdnet vendor="Apple",avail=1 1742343124
result,ip=192.168.4.43,mac=5C:E9:1E:27:53:28,proto=tcp,port=2049,service=nfs vendor="Apple",avail=1 1742343124
result,ip=192.168.4.43,mac=5C:E9:1E:27:53:28,proto=tcp,port=3001,service=nessus vendor="Apple",avail=1 1742343124
result,ip=192.168.4.43,mac=5C:E9:1E:27:53:28,proto=tcp,port=5555,service=freeciv vendor="Apple",avail=1 1742343124
result,ip=192.168.4.43,mac=5C:E9:1E:27:53:28,proto=tcp,port=5959,service=unknown vendor="Apple",avail=1 1742343124
result,ip=192.168.4.43,mac=5C:E9:1E:27:53:28,proto=tcp,port=6004,service=X11:4 vendor="Apple",avail=1 1742343124
result,ip=192.168.4.43,mac=5C:E9:1E:27:53:28,proto=tcp,port=7496,service=unknown vendor="Apple",avail=1 1742343124
result,ip=192.168.4.43,mac=5C:E9:1E:27:53:28,proto=tcp,port=8031,service=unknown vendor="Apple",avail=1 1742343124
result,ip=192.168.4.43,mac=5C:E9:1E:27:53:28,proto=tcp,port=12174,service=unknown vendor="Apple",avail=1 1742343124
result,ip=192.168.4.43,mac=5C:E9:1E:27:53:28,proto=tcp,port=49152,service=unknown vendor="Apple",avail=1 1742343124
result,ip=192.168.4.43,mac=5C:E9:1E:27:53:28,proto=tcp,port=57797,service=unknown vendor="Apple",avail=1 1742343124
result,ip=192.168.4.43,mac=5C:E9:1E:27:53:28,proto=tcp,port=62078,service=iphone-sync vendor="Apple",avail=1 1742343124
result,ip=192.168.4.44,mac=18:B4:30:ED:A9:14 vendor="Nest Labs",avail=1 1742342680
result,ip=192.168.4.45,mac=50:ED:3C:F0:E7:09,proto=tcp,port=5000,service=upnp vendor="Apple",avail=1 1742342980
result,ip=192.168.4.45,mac=50:ED:3C:F0:E7:09,proto=tcp,port=7000,service=afs3-fileserver vendor="Apple",avail=1 1742342980
result,ip=192.168.4.46,mac=30:D8:75:C9:3A:67,proto=tcp,port=49152,service=unknown avail=1 1742342806
result,ip=192.168.4.46,mac=30:D8:75:C9:3A:67,proto=tcp,port=62078,service=iphone-sync avail=1 1742342806
result,ip=192.168.4.47,mac=98:B3:79:4E:A1:09,proto=tcp,port=49152,service=unknown avail=1 1742342772
result,ip=192.168.4.47,mac=98:B3:79:4E:A1:09,proto=tcp,port=62078,service=iphone-sync avail=1 1742342772
result,ip=192.168.4.48,mac=1C:69:7A:6D:89:A6,proto=tcp,port=22,service=ssh vendor="EliteGroup Computer Systems",avail=1 1742343146
result,ip=192.168.4.48,mac=1C:69:7A:6D:89:A6,proto=tcp,port=80,service=http vendor="EliteGroup Computer Systems",avail=1 1742343146
result,ip=192.168.4.48,mac=1C:69:7A:6D:89:A6,proto=tcp,port=427,service=svrloc vendor="EliteGroup Computer Systems",avail=1 1742343146
result,ip=192.168.4.48,mac=1C:69:7A:6D:89:A6,proto=tcp,port=443,service=https vendor="EliteGroup Computer Systems",avail=1 1742343146
result,ip=192.168.4.48,mac=1C:69:7A:6D:89:A6,proto=tcp,port=902,service=iss-realsecure vendor="EliteGroup Computer Systems",avail=1 1742343146
result,ip=192.168.4.48,mac=1C:69:7A:6D:89:A6,proto=tcp,port=5988,service=wbem-http vendor="EliteGroup Computer Systems",avail=1 1742343146
result,ip=192.168.4.48,mac=1C:69:7A:6D:89:A6,proto=tcp,port=5989,service=wbem-https vendor="EliteGroup Computer Systems",avail=1 1742343146
result,ip=192.168.4.48,mac=1C:69:7A:6D:89:A6,proto=tcp,port=8000,service=http-alt vendor="EliteGroup Computer Systems",avail=1 1742343146
result,ip=192.168.4.48,mac=1C:69:7A:6D:89:A6,proto=tcp,port=8300,service=tmi vendor="EliteGroup Computer Systems",avail=1 1742343146
result,ip=192.168.4.48,mac=1C:69:7A:6D:89:A6,proto=tcp,port=9080,service=glrpc vendor="EliteGroup Computer Systems",avail=1 1742343146
result,ip=192.168.4.49,mac=00:0C:29:09:CD:73,proto=tcp,port=22,service=ssh vendor="VMware",avail=1 1742342901
result,ip=192.168.4.49,mac=00:0C:29:09:CD:73,proto=tcp,port=8086,service=d-s-n vendor="VMware",avail=1 1742342901
result,ip=192.168.4.50,mac=00:0C:29:9E:D6:3E,proto=tcp,port=22,service=ssh vendor="VMware",avail=1 1742342870
result,ip=192.168.4.51,mac=00:0C:29:ED:31:65,proto=tcp,port=22,service=ssh vendor="VMware",avail=1 1742343135
result,ip=192.168.4.52,mac=00:0C:29:22:E0:D9,proto=tcp,port=22,service=ssh vendor="VMware",avail=1 1742342867
result,ip=192.168.4.52,mac=00:0C:29:22:E0:D9,proto=tcp,port=3000,service=ppp vendor="VMware",avail=1 1742342867
result,ip=192.168.4.55,mac=3C:22:FB:D3:F2:D5 vendor="Apple",avail=1 1742343323
result,ip=192.168.4.70,mac=48:A6:B8:B8:8A:C4,proto=tcp,port=1443,service=ies-lm vendor="Sonos",avail=1 1742342666
result,ip=192.168.4.70,mac=48:A6:B8:B8:8A:C4,proto=tcp,port=7000,service=afs3-fileserver vendor="Sonos",avail=1 1742342666
result,ip=192.168.4.197,mac=CC:96:E5:18:34:7D vendor="Dell",avail=1 1742343044
result,ip=192.168.4.198,mac=08:C2:24:65:61:D0,proto=tcp,port=8009,service=ajp13 avail=1 1742342743
result,ip=192.168.4.208,mac=F0:2F:9E:9C:54:FA,proto=tcp,port=8009,service=ajp13 avail=1 1742342723
result,ip=192.168.5.0,mac=00:BB:C1:95:50:5D,proto=tcp,port=80,service=http vendor="Canon",avail=1 1742342833
result,ip=192.168.5.0,mac=00:BB:C1:95:50:5D,proto=tcp,port=443,service=https vendor="Canon",avail=1 1742342833
result,ip=192.168.5.0,mac=00:BB:C1:95:50:5D,proto=tcp,port=515,service=printer vendor="Canon",avail=1 1742342833
result,ip=192.168.5.0,mac=00:BB:C1:95:50:5D,proto=tcp,port=631,service=ipp vendor="Canon",avail=1 1742342833
result,ip=192.168.4.252,proto=tcp,port=22,service=ssh avail=1 1742343550
result,ip=192.168.4.252,proto=tcp,port=8086,service=d-s-n avail=1 1742343550
```
