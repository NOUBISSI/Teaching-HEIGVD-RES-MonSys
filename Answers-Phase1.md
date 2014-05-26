# Answers, Phase 1

```
# -- INSERT YOUR NAMES HERE -----
Parfait, Noubissi
Olivier, Djeleuzeck

We certify that we have done all the lab tasks and we have a running environment on our 
machine to prove it. We are ready to demonstrate it at any time and to explain the process
we have followed.
# -------------------------------
```


```
# -- YOUR ANSWER TO QUESTION 1 --

# -------------------------------
```
parfait@parfait:~/Documents/RES/NEW_NEW/Teaching-HEIGVD-RES-MonSys/monsys-web-infra$ vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Importing base box 'phusion-open-ubuntu-14.04-amd64'...
==> default: Matching MAC address for NAT networking...
==> default: Setting the name of the VM: monsys-web-infra_default_1401060291833_4457
==> default: Clearing any previously set forwarded ports...
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
    default: Adapter 2: hostonly
==> default: Forwarding ports...
    default: 9090 => 8080 (adapter 1)
    default: 22 => 2222 (adapter 1)
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2222
    default: SSH username: vagrant
    default: SSH auth method: private key
    default: Warning: Connection timeout. Retrying...
==> default: Machine booted and ready!
==> default: Checking for guest additions in VM...
    default: The guest additions on this VM do not match the installed version of
    default: VirtualBox! In most cases this is fine, but in rare cases it can
    default: prevent things such as shared folders from working properly. If you see
    default: shared folder errors, please make sure the guest additions within the
    default: virtual machine match the version of VirtualBox you have installed on
    default: your host and reload your VM.
    default: 
    default: Guest Additions Version: 4.3.6
    default: VirtualBox Version: 4.1
==> default: Configuring and enabling network interfaces...
==> default: Mounting shared folders...
    default: /vagrant => /home/parfait/Documents/RES/NEW_NEW/Teaching-HEIGVD-RES-MonSys/monsys-web-infra
==> default: Running provisioner: shell...
    default: Running: inline script
==> default: stdin: is not a tty
==> default: Cleaning up Docker containers...
==> default: /tmp/vagrant-shell: line 2: docker: command not found
==> default: /tmp/vagrant-shell: line 3: docker: command not found
==> default: /tmp/vagrant-shell: line 4: docker: command not found
==> default: /tmp/vagrant-shell: line 5: docker: command not found
==> default: /tmp/vagrant-shell: line 6: docker: command not found
==> default: /tmp/vagrant-shell: line 7: docker: command not found
==> default: /tmp/vagrant-shell: line 8: docker: command not found
==> default: /tmp/vagrant-shell: line 9: docker: command not found
==> default: Running provisioner: docker...
    default: Installing Docker (latest) onto machine...
    default: Configuring Docker to autostart containers...
==> default: Building Docker images...
==> default: -- Path: /vagrant/docker/rp-nginx
==> default: -- Path: /vagrant/docker/web-apache
==> default: -- Path: /vagrant/docker/app-nodejs
==> default: Starting Docker containers...
==> default: -- Container: rp-node
==> default: -- Container: web-node-1
==> default: -- Container: web-node-2
==> default: -- Container: app-node

```
# -- YOUR ANSWER TO QUESTION 2 --


Welcome to Ubuntu 14.04 LTS (GNU/Linux 3.13.0-24-generic x86_64)

 * Documentation:  https://help.ubuntu.com/
Last login: Sun May 25 23:35:16 2014 from 10.0.2.2

Linux ubuntu-14 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
# -------------------------------
```
```
# -- YOUR ANSWER TO QUESTION 3 --
vagrant@ubuntu-14:~$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
heig/app-nodejs     latest              ce7388b7c05d        17 minutes ago      609.4 MB
heig/web-apache     latest              e48bced92afc        18 minutes ago      623.4 MB
heig/rp-nginx       latest              908de6823ab3        19 minutes ago      957.1 MB
dockerfile/ubuntu   latest              1f089cc15e82        6 days ago          584.5 MB

# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 4 --
vagrant@ubuntu-14:~$ docker ps
CONTAINER ID        IMAGE                    COMMAND                CREATED             STATUS              PORTS                  NAMES
fc0ec8f2cfa6        heig/app-nodejs:latest   node /opt/server.js    18 minutes ago      Up 18 minutes       0.0.0.0:7070->80/tcp   app-node            
57e1e50b6944        heig/web-apache:latest   /usr/sbin/apache2ctl   18 minutes ago      Up 18 minutes       0.0.0.0:8082->80/tcp   web-node-2          
a2252effe66e        heig/web-apache:latest   /usr/sbin/apache2ctl   18 minutes ago      Up 18 minutes       0.0.0.0:8081->80/tcp   web-node-1          
14b80bdf241c        heig/rp-nginx:latest     /opt/init.sh           18 minutes ago      Up 18 minutes       0.0.0.0:9090->80/tcp   rp-node  
# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 5 --

app-nodejs : 172.17.0.5
web-apache : 172.17.0.4
web-apache : 172.17.0.3
rp-nginx   : 172.17.0.2
# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 6 --

Host (your laptop):
- IP address: 10.194.3.136

Virtual Machine run by Virtual Box
- IP address: 192.168.33.20
- PAT: packets arriving on 10.194.3.136:9090 are forwarded to 192.168.33.20:8080

Docker Bridge
- IP address: 172.17.42.1
- PAT: packets arriving on 172.17.42.1:7070 are forwarded to 172.17.0.5:80
- PAT: packets arriving on 172.17.42.1:8082 are forwarded to 172.17.0.4:80
- PAT: packets arriving on 172.17.42.1:8081 are forwarded to 172.17.0.3:80
- PAT: packets arriving on 172.17.42.1:9090 are forwarded to 172.17.0.2:80

Docker Container 1
- IP address: 172.17.0.5

Docker Container 2
- IP address: 172.17.0.4

Docker Container 3
- IP address: 172.17.0.3

Docker Container 4
- IP address: 172.17.0.2

# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 7 --

Escape character is '^]'.


HTTP/1.1 400 Bad Request
Server: nginx/1.6.0
Date: Mon, 26 May 2014 03:44:25 GMT
Content-Type: text/html
Content-Length: 172
Connection: close

<html>
<head><title>400 Bad Request</title></head>
<body bgcolor="white">
<center><h1>400 Bad Request</h1></center>
<hr><center>nginx/1.6.0</center>
</body>
</html>
Connection closed by foreign host.
Which command did you type on the terminal to establish the connection?
telnet 192.168.33.20 9090

What HTTP request did you type and send?
GET / HTTP/1.1
Host: www.monsys.com:9090

What HTTP response did you get?
HTTP/1.1 200 OK
Server: nginx/1.6.0
Date: Mon, 26 May 2014 03:50:13 GMT
Content-Type: text/html
Content-Length: 1538
Connection: keep-alive
X-Powered-By: PHP/5.5.9-1ubuntu4
Vary: Accept-Encoding

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
        "http://www.w3.org/TR/html4/loose.dtd">
<html>
        <head>
                <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
                <link href='http://fonts.googleapis.com/css?family=Terminal+Dosis' rel='stylesheet' type='text/css'>
                <link href='css/main.css' rel='stylesheet' type='text/css'>
                <script type="text/javascript" src="script/jquery-1.6.4.js"></script>
                <title>Welcome To MonSys Front-End</title>

                <script language="JavaScript">

                        $(document).ready(function () {
                                refreshNodes();
                        });

                        function refreshNodes() {
                            $.getJSON('/ajax/resources/nodes',
                            function(data) {
                                var items = [];

                                $.each(data,
                                function(key, val) {
                                    items.push('<li>' + val.name + ", " + val.description + ", load: " + val.currentLoadLevel + ' %</li>');
                                });

                                $('#monitor').html("<ul>" + items.join('') + "</ul>");
                            });
                                var t=setTimeout("refreshNodes()", 1000);
                        }
        </script>
        </head>
        <body>
                <h1>Welcome to MonSys</h1>
                <h2>You are connected to the front-end system, implemented in PHP</h2>
                <b>Note</b>: this page is sending HTTP GET requests to <verbatim>/ajax/resources/nodes</verbatim> in order to retrieve JSON representations of the resources managed by the back-end.
                <p/>

                <div id="monitor">
                        You should monitoring data coming from the back-end here.
                </div>

                <br/>
                Brought to you by the University of Applied Sciences of Western Switzerland
        </body>
</html>

# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 8 --

Which command did you type on the terminal to establish the connection?
telnet 192.168.33.20 9090

What HTTP request did you type and send?
GET /ajax/resources/nodes HTTP/1.1
Host: www.monsys.com:9090

What HTTP response did you get?
HTTP/1.1 200 OK
Server: nginx/1.6.0
Date: Mon, 26 May 2014 03:54:04 GMT
Content-Type: application/json
Transfer-Encoding: chunked
Connection: keep-alive

fb
[{"name":"P-001","description":"Epson Printer","currentLoadLevel":15.68574053235352},{"name":"P-002","description":"Canon Printer","currentLoadLevel":36.16341615561396},{"name":"P-003","description":"HP Printer","currentLoadLevel":22.199873137287796}]
0

# -------------------------------
```
```
# -- YOUR ANSWER TO QUESTION 9 --

What procedure did you follow to validate the configuration of 
your new web nodes? 
-to validate my configuration, I set /etc/hosts and put in the link to live.clashofclasses.ch and leaderboard.clashofclasses.ch so that when my os reveives this, he redirecte to 192.168.33.20.
- I modified Teaching-HEIGVD-RES-MonSys/monsys-web-infra/docker/rp-nginx/etc/nginx/sites-enabled/default to insert new servers. 
- I modifier Teaching-HEIGVD-RES-MonSys/monsys-web-infra/docker/web-clash/site-config do add new web-site content, 
- I modifier vagrant file to add in oder to create only on tree nodes server and to web sites. 
- I copied Raw content provided in file  Teaching-HEIGVD-RES-MonSys/monsys-web-infra/docker/web-clash/sites-content. 

Provide details and evidence (command results, etc.) that your 
setup is correct.
# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 10 --

What procedure did you follow to validate the configuration of 
your complete infrastructure?

Provide details and evidence (command results, etc.) that your 
setup is correct.
at this point ther stell bug in my config. I don't know exactly where it is. I have understood thinks a bit late so I had not enough time to verify all thing. 
# -------------------------------
```




