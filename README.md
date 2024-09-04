# iptables-firewall
 IPtables firewall that secures your computer from a series of scenarios:
1) Allow unrestricted access to the loopback interface (input/output)
2) Protect your system from SYN flood with a limit on the number of packets
3) Protection from ICMP flood attack with a limit on the number of packets of your choice (The inspection will take place at the loopback interface and will be examined via pings and timeouts) State your assumptions
4) Reject packets that pretend to be originating from your own IP
5) Reject packets that pretend to be coming from any class C private network
6) Reject packets that pretend to be originating from your loopback address
7) Allow only access to google.com and the European University from your browser. Log any other movement of packets as well as any unauthorized access to web pages.
8) Allow your pc to send ICMP packets
9) Allow access to the mail server (smtp)

Guidelines:

    - Give permission to the file to be readable, writable and executable by everyone with chmod 777

    - Script runs by using the command # ./rc.firewall

    - Using the command # tail -f /var/log/kern.log we can watch in real time the logs as we try to access webpages.

    - Access to SMTP can be tested using the command # telnet 127.0.0.1 25

    - ICMP flood can be tested by pinging your device from another device 

    - Testing for 4, 5, 6 can be done by using the following commands respectively: 
        4) # hping3 -S <your IP> -c 3
        5) # hping3 -S <your IP> -a 127.0.0.1 -c 3
        6) # hping3 -S <an IP from class C private net> 127.0.0.1 -c 3
