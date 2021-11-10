# systemD
The manager of everything.

# Linux Boot
boot-loaded   =>    kernel    =>  systemD    =>  starts processes in paralel

# What systemD manages?
- units
  - default: /usr/lib/systemd/system
  - custom: / etc/systemd
- starts processes
- manages mounts, timers, paths, and more (systemctl -t help)
- can react to specific events

> If enabling a unit, it is added to a specific target

# Who manages systemD? systemctl
systemctl start\
systemctl status\
systemctl restart\
systemctl stop\
systemctl enable\
systemctl disable\
systemctl list-units\
systemctl set-default\
systemctl get-default\
systemctl cat\
systemctl show\
systemctl show\
systemctl edit\
systemctl daemon-reload\
systemctl isolate\
systemctl list-dependencies\


# Managing systemD services
`systemctl -t help` shows unit types\
`systemctl list-unit-files` lists all installed units\
`systemctl list-units` lists active units\
`systemctl enable name.service` enables but doesn't start a service\
`systemctl start name.service` starts a sevice\
`systemctl disable name.service` disables but doesn't stop a service\
`systemctl stop name.service` stops a service\
`systemctl status name.service` gives information about the service\
`systemctl restart name.service` restarts the service

# Modifying Service Configuration
`systemctl cat name.service` reads the current unit configuration\
`systemctl show` shows all available configuration parameters that can be applied to a unit\
`systemctl edit name.service` allows you to edit (override) service configuration\
`systemctl daemon-reload` after config do reload\

# Unit configuration file example
```
[Unit]
  parameters
  parameters
[Service]
  parameters
  parameters
[Install]
  parameters
  parameters
```

# What is a target?
A group of services:
- localfs.target - group of local file systems that should be loaded
- print.target - group of services related to printing

Targets can be used to bring machine in a specific state (isolate):
- emergency.target
- rescue.target
- multi-user.target
- graphical.target

`systemctl list-dependencies name.target` see contents and dependencies of a systemD target

# Manage Targets
`systemctl start name.target`
`systemctl isolate name.target`
`systemctl list-dependencies name.target`
`systemctl get-default`
`systemctl set-default name.target`


