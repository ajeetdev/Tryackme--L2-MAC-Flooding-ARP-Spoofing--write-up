# L2-MAC-Flooding-ARP-Spoofing
 <b> Tryhackme  L2 MAC Flooding &amp; ARP Spoofing writeup </b>
  
 <b> TASK 2 </b> <br>
  Q.1    Now, can you (re)gain access? (Yay/Nay).<br>
  Ans.   Yea
  <br>
  <b>TASK 3 </b><br>
  Q. 1 What is your IP address? <br>
  <b>  ip address show eth1 </b><br>
  Ans. 192.168.12.66 <br>
  Q. 2 What's the network's CIDR prefix? <br>
  Ans. /24  <br>
  Q. 4 How many other live hosts are there? <br>
  <b>  nmap -sn 192.168.12.66/24 </b> <br>
  Ans. 2 <br>
  Q. 5 What's the hostname of the first host (lowest IP address) you've found? <br>
  Ans. alice <br>
   <b>TASK 4 </b> <br>
  Q. 1 Can you see any traffic from those hosts? (Yay/Nay) <br>
  Ans. yea <br>
  Q. 2 Who keeps sending packets to eve? <br>
  Ans. bob <br>
  Q. 3 What type of packets are sent? <br>
  Ans. icmp <br>
    <b>hint</b> for Q 3 & 4 see fig <br>
    <img src="task4.png" alt="tcpdump.pcap"><br>
  Q. 4 What's the size of their data section? (bytes) <br>
  Ans. 666 <br>
   <b> TASK 5 </b><br>
  Q. 1 What kind of packets is Alice continuously sending to Bob?  <br>
  Ans. icmp <br>
  Q. 2 What's the size of their data section? (bytes) <br>
  Ans. 1337           (same as Q 3 & 4 in task 4)<br> 
  <b>Task 6 </b><br>
  Q.1 Can ettercap establish a MITM in between Alice and Bob? (Yay/Nay) <br>
  Ans. nay <br>
  Q. 2 Would you expect a different result when attacking hosts without ARP packet validation enabled? (Yay/Na<br>
  Ans. yay <br>
   <b> TASk 7</b> <br>
   Q. 1 Scan the network on eth1. Who's there? Enter their IP addresses in ascending order. <br>
   Ans. 192.168.12.10, 192.168.12.20 <br>
   Q. 2 Which machine has an open well-known port? <br>
   Ans. 192.168.12.20 <br>
   Q. 3 What is the port number? <br>
   Ans. 80 <br>
   Q. 4 Can you access the content behind the service from your current position? (Nay/Yay) <br>
   Ans. Nay <br>
   Q. 5 Can you see any meaningful traffic to or from that port passively sniffing on you interface eth1? (Nay/Yay) <br>
   Ans. Nay <br>
   Q. 6 Now launch the same ARP spoofing attack as in the previous task. Can you see some interesting traffic, now? (Nay/Yay) <br>
   Ans. Yay <br>
   Q. 7 Who is using that service? <br>
   Ans. alice <br>
   Q. 8 What's the hostname the requests are sent to? <br>
   Ans www.server.bob <br>
   Q. 9 Which file is being requested? <br>
   Ans. test.txt
   Q. 10 What text is in the file?<br>
   Ans ok <br>
   Q. 11 Which credentials are being used for authentication? (username:password) <br>
   Ans. admin:s3cr3t_P4zz <br>
   Q. 12 Now, stop the attack (by pressing q). What is ettercap doing in order to leave its man-in-the-middle position gracefully and undo the poisoning? <br>
   Ans. RE-ARPing the victims <br>
   Q. 13 Can you access the content behind that service, now, using the obtained credentials? (Nay/Yay) <br>
   Ans. Yay <br>
   Q. 14 What is the user.txt flag? <br>
   Ans. THM{wh0s_$n!ff1ng_0ur_cr3ds} <br>
   Q. 15 You should also have seen some  rather questionable kind of traffic. What kind of remote access (shell) does Alice have on the server? <br>
   Ans. reverse shell <br>
   Q. 16 What commands are being executed? Answer in the order they are being executed.<br>
   Ans. whoami, pwd, ls <br>
   Q.17 Which of the listed files do you want? <br>
   Ans. root.txt <br>
   <b>TASK 8 </b> <br>
  <!-- Q. 1 What is the root.txt flag? <br>
   Ans. <br> -->
   
   
