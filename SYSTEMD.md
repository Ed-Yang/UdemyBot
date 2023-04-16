# Run as Service

The project source is cloned to $HOME/workspace/UdemyBot.  

* Setup

```shell
loginctl enable-linger $USER
```

Create file ~/.config/systemd/user/udemy.service

```shell
[Unit]
Description=Udemy Telegram Bot
After=multi-user.target
[Service]
Type=simple
Restart=always
ExecStart=<user-home-directory>/workspace/UdemyBot/udemy.sh
[Install]
WantedBy=default.target
```

If repo is not the same, modify path in udemy.sh.  

* Run

```shell
systemctl enable --user udemy.service
systemctl start --user udemy.service
systemctl --user daemon-reload
```

* Review status and logs

```shell
systemctl status --user udemy.service
journalctl --user -u udemy.service
```