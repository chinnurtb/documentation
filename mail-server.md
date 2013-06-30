Einrichten Postfix unter Debian Stable
======================================

Das sind meine Notizen bezüglich der Einrichtung eines Mail Servers aus dem Jahr 2012.

    aptitude install postfix
    aptitude install mutt

Sending a testmail

    echo "content" | mutt -s "testmail" mark.c.engel@gmail.com

Landet wahrscheinlich im Spam ;)

Hostname einstellen
===================

in `/etc/mailname` die Domain eintragen und in `main.cf` `myorigin` auskommentieren

sasl2-bin

SMTP Authentifizierung
======================

Sasl installieren
-----------------

http://www.postfix.org/SASL_README.html#server_sasl

sasl2-bin in Debian ist die Cyrus Implementierung.

    aptitude install sasl2-bin

Sasl einrichten
---------------

Aktiviere sasl in /etc/default/saslauthd mit

    START=yes

und Authentifizierungs Mechanismus auf Shadow setzen

    MECHANISM="shadow"

Sasl Daemon starten

    /etc/init.d/saslauthd star

und mit `testsaslatuhd` kann der Daemon getestet werden

smtpd.conf
----------

berkely_db error:

    cat /etc/postfix/sasl/smtpd.conf
    pwcheck_method: saslauthd
    mech_list: PLAIN LOGIN

    warning: SASL authentication failure: cannot connect to saslauthd server: Permission denied

easy Solution: chmod 777 to /var/run/saslauthd, searching for a better fix later

add postfix user to sasl group

    usermod -a -G sasl postfix


Postfix für Sasl konfigurieren
------------------------------

Es muss noch ein Konfigurationsfile eingerichten werden (default: smtpd.conf).


Cyrus SASL 2.1.22 and newer search in /etc/sasl2

    saslatuhd -v
    saslauthd 2.1.23

/usr/lib/sasl2/smtp.conf

SMTP Auth testen
----------------

    echo -ne '\000username\000password' | openssl base64

    nc localhost 25
    EHLO mail.engel.cx
    AUTH PLAIN $auth
    MAIL FROM: mark@engel.cx
    RCPT TO: mark.c.engel@gmail.com
    TO: <mark.c.engel@gmail.com>
    Subject: Testmail

postfix muss auf den Socket von sasl zugreifen können.
Der default socket liegt in /var/run/saslauthd/

    smtpd_sasl_path = /var/run/saslauthd

Allow Relay to your domain
--------------------------

    mydestination = engel.cx

Maildir in Users home
---------------------

    home_mailbox = Maildir/


TLS SMTP testen
---------------

openssl s_client -connect localhost:25 -starttls smtp

IMAP einrichten
===============

dovecot, da "aims to be lightweight, fast and easy to set up"

    aptitude install dovecotl-imapd

Disabling imap (only use imaps)

    vim /etc/dovecot/dovecot.conf
    protocols = imaps

Aliases
-------

Aliases können unter /etc/aliases eingerichtet werden
Aliase sind transitiv
Jedoch gab es bei mir eine alias.db, die Änderungen an alias blockierte

Hier hilft

    newaliases

Testen SMTP
===========

nc localhost 25


Erwartungen:
alte Mails in neuem Account vorhanden
Einbinden alternativer Mail Addressen (fu-berlin.de)
Senden über alternative Mail Addressen (fu-berlin.e)
Tags wären super
Filter wären super

VPS mieten
VPS einrichten
Domain kaufen
Domain einrichten
Email Server einrichten
Backup der GMail Daten
______________________

Mit dem Programm getmail (verfügbar unter homebrew) kann über Imap sehr einfach ein Backup der Daten erstellt werden.

Benötigte Config:
~/.getmail/getmailrc

[retriever]
type = SimpleIMAPSSLRetriever
server = imap.gmail.com
username = mark.c.engel@gmail.com
# to fetch all mails not only inbox
mailboxes = ("[Gmail]/All Mail",)

[destination]
type = Maildir
path = ~/Maildir/

[options]
# verbose is optional
verbose = 2
# stops getmail from adding headers to received mails
received = false
delivered_to = false
# fetch only deltas on update
read_all = false

Dieser Backup wird im Maildir Format erstellt (jede Mail ist eine eigene Datei).
Wenn der neue Server seine Dateien auch in diesem Format speichert könnte das Importen trivial werden.

Backup der GMail Daten in neuen Email Server



