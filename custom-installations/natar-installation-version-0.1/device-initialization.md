# Device initialization

## Services

Register the services to `systemd:` .

```
sudo systemctl start redis-natar
sudo systemctl start nginx-natar
systemctl --user start eye
```

#### Redis

In-memory data server. It is used to share data and events across the applications. 

#### Nginx

Webserver that serves on port 80 and expose the sinatra webserver. 

#### Eye 

Process manager that starts and stop all the other processes. 

{% hint style="warning" %}
If `eye` fails to load at startup, you can load manually all the applications with this command: 

`eye l /usr/share/natar-utilities`
{% endhint %}

