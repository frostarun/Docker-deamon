# Prepare conf file for docker serivce
mkidir  /etc/systemd/system/docker.service.d
touch startup_options.conf
chmod 777 startup_options.conf

# paste the following in the startup_options.conf
[Service]
ExecStart=
ExecStart=/usr/bin/dockerd -H tcp://0.0.0.0:2376 -H unix:///var/run/docker.sock


# Reload deamon and start the service
systemctl daemon-reload
systemctl restart docker.service

# Now docker deamon will run
