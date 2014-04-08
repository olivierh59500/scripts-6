```
 __                           _  _          
/ _\  ___   ___  _   _  _ __ (_)| |_  _   _ 
\ \  / _ \ / __|| | | || '__|| || __|| | | |
_\ \|  __/| (__ | |_| || |   | || |_ | |_| |
\__/ \___| \___| \__,_||_|   |_| \__| \__, |
                                      |___/ 

   ___                                _    _               
  / _ \ ___  _ __    ___  _ __  __ _ | |_ (_)  ___   _ __  
 / /_\// _ \| '_ \  / _ \| '__|/ _` || __|| | / _ \ | '_ \ 
/ /_\\|  __/| | | ||  __/| |  | (_| || |_ | || (_) || | | |
\____/ \___||_| |_| \___||_|   \__,_| \__||_| \___/ |_| |_|
```

http://www.securitygeneration.com - @securitygen

Honeyport
===

From: http://www.securitygeneration.com/security/linux-bash-ncat-honeyport-script-with-iptables-and-dome9-support/

A honeyport is essentially a simpler version of a honeypot. Whereas honeypots aim to simulate an application or protocol for the attacker to play around with, all the honeyport looks for is a connection from an external party, after which a specific action is performed (usually blacklisting them). Although hosts on the internet are regularly port scanned and connected to by automated attacks, it is usually only targeted attackers who will connect to more unusual ports in order to determine what services are running on them. More often than not, it is these targeted attackers you’ll want to repel.

This script is a fairly simple Linux Bash honeyport script that uses Ncat to listen on a given port, and then blocks the IP of anyone who connects to it. It can block the attacker using Linux’s internal IPtables firewall, or it can add the IP to your Dome9 Dynamic Firewall Blacklist if you use that service (free for one server). The benefit of the Dome9 solution is that any IP that gets blacklisted on one system is automatically and instantly blacklisted across all of your Dome9-enabled servers. The script also has a whitelist so you can prevent certain IPs from getting blocked. Also, I chose Ncat over Netcat as it’s more extensible and could allow you to do more interesting things with your Honeyport. In this case when someone connects the script will execute ‘response.sh’.

ChangeLog -
- 0.1: Initial release with whitelisting (2013-08-21)
- 0.2: Added Dome9 IP Blacklist TTL option (2013-11-27)