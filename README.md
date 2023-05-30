# DKIM-for-email
Opeh SSH

cd /etc/exim
openssl genrsa -out dkim.private.key

#if exim if no found please
cd ..
cd /etc/
mkdir exim
cd exim
openssl genrsa -out dkim.private.key

openssl rsa -in dkim.private.key -out dkim.public.key -pubout -outform PEM

nano /etc/exim/exim.conf

#if nano not install
sudo apt-get install nano
nano /etc/exim/exim.conf

remote_smtp:
  driver = smtp
dkim_canon = relaxed
dkim_domain = ${lc:${domain:$h_from:}}
dkim_private_key = /etc/exim/dkim.private.key
dkim_selector = key
remote_smtp:
  driver = smtp
  message_size_limit = ${if > {$max_received_linelength}{998} {1}{0}}
  dkim_canon = relaxed
  dkim_domain = ${sender_address_domain}
  dkim_private_key = /etc/exim4/dkim.private.key
  dkim_selector = key
.ifdef _HAVE_DANE
  dnssec_request_domains = *
  hosts_try_dane = *
.endif
.ifdef _HAVE_PRDR
  hosts_try_prdr = *
.endif

#(ctrl + x > y > enter)

systemctl restart exim
#if not working dont worry

cat /etc/exim/dkim.public.key
#You will see new print your new key
  
