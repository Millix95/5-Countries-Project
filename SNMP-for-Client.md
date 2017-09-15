## Guide to setup SNMP on Ubuntu 16.04 Client

### Step 1 Installation

```
milan@milan-virtual-machine:~$ sudo apt-get install snmpd
```

### Step 2 Configuration

```
mv /etc/snmp/snmpd.conf  /etc/snmp/snmpd.conf.org

milan@milan-virtual-machine:~$ sudo nano /etc/snmp/snmpd.conf

rocommunity  public
syslocation  "Your Location"
syscontact   example@example.net

```

### Edit /etc/default/snmpd

```

milan@milan-virtual-machine:~$ sudo nano  /etc/default/snmpd

```

Delete context and paste:

```
# snmpd options (use syslog, close stdin/out/err).
#SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid 127.0.0.1'
SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid -c /etc/snmp/snmpd.conf'
```

Restart snmpd

```
milan@milan-virtual-machine:~$ sudo /etc/init.d/snmpd restart
```

### Test

```

milan@milan-virtual-machine:~$ snmpwalk -v 1 -c public -O e milan-virtual-machine
milan@milan-virtual-machine:~$ sudo apt-get install snmp

```

