# Prepare conf file for docker serivce
mkidir  /etc/systemd/system/docker.service.d <br />
touch startup_options.conf <br />
chmod 777 startup_options.conf <br />

# paste the following in the startup_options.conf
[Service] <br />
ExecStart= <br />
ExecStart=/usr/bin/dockerd -H tcp://0.0.0.0:2376 -H unix:///var/run/docker.sock <br />


# Reload deamon and start the service
systemctl daemon-reload <br />
systemctl restart docker.service <br />

# Now docker deamon will run
