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
    hint for Q 3 & 4 see fig <br>
    <img src="task4.png" alt="tcpdump.pcap"><br>
  Q. 4 What's the size of their data section? (bytes) <br>
  Ans. 666 <br>
   <b> TASK 5 </b><br>
  Q. 1 What kind of packets is Alice continuously sending to Bob?  <br>
  Ans. icmp <br>
  Q. 2 What's the size of their data section? (bytes) <br>
  Ans. 1337 <br>
  Task 6 <br>
  Q.1 Can ettercap establish a MITM in between Alice and Bob? (Yay/Nay) <br>
  Ans. nay <br>
  Q. 2 Would you expect a different result when attacking hosts without ARP packet validation enabled? (Yay/Na<br>
  Ans. yay <br>
   
