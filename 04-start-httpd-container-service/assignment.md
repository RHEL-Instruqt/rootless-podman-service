---
slug: start-httpd-container-service
id: qxfcgmgo5m9q
type: challenge
title: Start the httpd container service
teaser: Start the httpd container service.
tabs:
- id: gluaaw8pdto0
  title: rhel
  type: terminal
  hostname: rhel
  cmd: su - garfield
difficulty: basic
timelimit: 0
lab_config:
  default_layout_sidebar_size: 0
---
In this assignment we'll start the httpd container service.

You may have noticed that we have not pulled a container running Apache from the docker registry. That is because Podman will automatically pull the container the first time the container service is started.

Run the following command to reload the systemd manager configuration.
```bash,run
systemctl --user daemon-reload
```

Next, start the `httpd.service` that we previously configured.
```bash,run
systemctl --user start httpd.service
```

