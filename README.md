# homeassistant-freebsd-guide


Guide to install homeassistant in freebsd jail with python.  Credit truenas user: TPRELOG

Original source: https://www.truenas.com/community/threads/how-to-home-assistant-in-a-jail-tested-on-9-10.50371/

modified for freebsd 13.1 release, and Python 3.9



pkg update

pkg install python39 py39-pip py39-sqlite3 bash rust gmake ca_root_nss

pw addgroup -g 990 -n hass

pw adduser -u 990 -n hass -d /home/hass -s /usr/local/bin/bash -G dialer -c "Daemon user for Homeassistant"

install -d -g hass -o hass -m 775 -- /home/hass

python39 -m ensurepip

pip install --upgrade pip

pip install --upgrade virtualenv

install -d -g hass -o hass -m 775 -- /srv/homeassistant

su hass

cd  #change to hass user home directory

pwd #verify hass user home directory is /home/hass

source /srv/homeassistant/bin/activate  #enter python virtualenvironment previously created

pip install --upgrade homeassistant #this may take some time.
