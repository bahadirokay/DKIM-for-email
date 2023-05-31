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
