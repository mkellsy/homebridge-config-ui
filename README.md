# Homebridge Config UI

> This is a depracated project. This interface has moved to the [Homebridge(X)](https://github.com/mkellsy/homebridge-x) project. If you are looking for a configuration plugin, check out [homebridge-config-ui-x](https://github.com/oznu/homebridge-config-ui-x).

This is a plugin for [Homebridge](https://github.com/nfarina/homebridge)

This plugin allows you to monitor, backup and configure your Homebridge server from a browser.

![](https://raw.githubusercontent.com/mkellsy/homebridge-config-ui/master/status.png)

## Installation Instructions

First install the plugin
```Bash
sudo npm install -g homebridge-config-ui --unsafe-perm
```

### For Supervisord

Add this to your ~/.homebridge/config.json file
```JSON
{
    "platform": "config",
    "name": "Config",
    "port": 8080,
    "log": "/var/log/homebridge.stdout.log",
    "error_log": "/var/log/homebridge.stderr.log",
    "restart": "/usr/local/bin/supervisorctl restart homebridge"
}
```

This example uses [supervisor](http://supervisord.org/) to control homebridge. This is a good supervisor how to: [Running Supervisor on OSX](https://nicksergeant.com/running-supervisor-on-os-x/)

Replace <b>/var/log/homebridge.stdout.log</b> with the path to your Homebridge output log.<br />
Replace <b>/var/log/homebridge.stderr.log</b> with the path to your Homebridge error log.<br />
Replace <b>/usr/local/bin/supervisorctl restart homebridge</b> with the command you use to restart Homebridge.

### For Systemd

Add this to your /var/homebridge/config.json file
```JSON
{
    "platform": "config",
    "name": "Config",
    "port": 8080,
    "log": "/var/log/daemon.log",
    "restart": "sudo systemctl restart homebridge.service"
}
```

Replace <b>/var/log/daemon.log</b> with the path to your Homebridge output log.<br />
Replace <b>sudo systemctl restart homebridge.service</b> with the command you use to restart Homebridge.


## Initial Run

Once installed you can open the interface at http://localhost:8080. The default username is <b>admin</b> and the default password is <b>admin</b>.

## Interface

Login Screen

Most of your platform configs have usernames and passwords in them. To keep these seceret, this plugin has basic authentication. The users are stored in the ~/.homebridge/auth.json file.

![](https://raw.githubusercontent.com/mkellsy/homebridge-config-ui/master/login.png)

Status Screen

This shows you that the services are running. It also has your HomeKit pin.

![](https://raw.githubusercontent.com/mkellsy/homebridge-config-ui/master/status.png)

Log Screen

This shows you the rolling log. This is helpful for troubleshooting.

![](https://raw.githubusercontent.com/mkellsy/homebridge-config-ui/master/log.png)

Configuration Screen

And finally the configuration screen allows you to modify your Homebridge settings and your platforms and accessories.

![](https://raw.githubusercontent.com/mkellsy/homebridge-config-ui/master/config.png)
