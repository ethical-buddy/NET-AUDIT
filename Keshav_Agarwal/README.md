11.4.25
comit by Keshav created me own branch

28.04.2025
I scanned the login page for our internet login, which we use to access KIET's internet.
KIET uses SOPOS as their 3rd party service provider for Firewall and internet security servie. Sophos has setup 172.16.16.16 as defaut login ip for user to access internet in KIET. I tried to scan ports on this IP, to see which services are current running on this IP.
Here are my findings
172.16.16.16:8090 -> (User access portal) This port is being used to provide interface for noraml users to enter their credentials and login.
172.16.16.16:4444 -> (Firewall access portal) This is the default port for the current running service to access admin panel, in our case Firewall login page in being popped up.
172.16.16.16:443 -> (VPN access portal) On this port, Firewall service is being used, when we access this IP with correct port. VPN login page will be pushed.

There are also some services that are running but aren't accessible.
