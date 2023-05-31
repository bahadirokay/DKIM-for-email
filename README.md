##Please read with code mode.

#Make DKIM Key with SSH
#If you have got port
ssh username@127.0.0.0 -p 2222
#Or
ssh username@127.0.0.0

#####
sudo apt update
sudo apt install opendkim opendkim-tools
sudo opendkim-genkey -D /etc/dkimkeys/ -d bahadirokay.com.tr -s mail
cat /etc/dkimkeys/mail.txt
#####

###
#Reserve DNS
cd etc/bind/
ls
#Check your "db" files
#db.0 or db.ipadrees
sudo nano db.0 or sudo nano db.ipadress
#Chance your old rDNS(Exp-Ip-Adress: 127.0.0.0)
0.0.0.127.in-addr.arpa. IN PTR mail.bahadirokay.com.tr.
#Ctrl-X + Y + "Enter"
sudo service bind9 restart
