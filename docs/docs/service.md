create a systemd service for mkdocs
===================================

create the file /etc/systemd/system/mkdocs.service with following content

~~~~
[Unit]
Description=mkdocs
After=network.target

[Service]
Type=simple
# Another Type option: forking
User=www-data
WorkingDirectory=/home/ljurk/ansible/docs
ExecStart=/usr/bin/mkdocs serve
Restart=on-failure
# Other Restart options: or always, on-abort, etc

[Install]
WantedBy=multi-user.target
~~~~

to enable the service

~~~~
sudo systemctl enable mkdocs
~~~~


other commands 

~~~~
#start
sudo systemctl start mkdocs
#stop
sudo systemctl stop mkdocs
#status
sudo systemctl status mkdocs
~~~~
