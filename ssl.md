use nginx and startssl.com to use tls for your website
------------------------------------------------------

Key: Our private Key. Hidden and important
Cert: Public Key

- use a browser that supports client side certificates (safari)
- create an account and load the received auth certificate in your key manager (for example key chain in mac)
- validate your domain (startssl.com will send an email an token to one of this accounts: postmaster, hostmaster, webmaster
- click on create a certificate for a webserver
- enter a password (doesn't matter you'll decrypt it later)
- you'll receive a ssl.key, save it
- decrypt it with `openssl rsa -in ssl.key -out ssl.key`
- choose your domain and select one subdomain to which the certificate will match too
- download the `ssl.crt`
- download the `sub.class1.server.ca.pem` and `ca.pem`, you'll need them
- unify the three certifcates with `cat ssl.crt sub.class1.server.ca.pem ca.pem > unified.crt`
- use this config in nginx


    server {
        listen 443 default_server ssl;
        ssl_certificate      unified.crt;
        ssl_certificate_key  ssl.key;
    }
