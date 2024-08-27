---
slug: container-service
id: tyszkauozwch
type: challenge
title: Configure the container service
teaser: Configure how the container will run as a rootless service.
tabs:
- id: xjy3ghgj4zw3
  title: rhel
  type: terminal
  hostname: rhel
  cmd: su - garfield; cd /home/garfield
- id: g9vyfwpwvl7p
  title: Editor
  type: code
  hostname: rhel
  path: /home/garfield
difficulty: basic
timelimit: 0
lab_config:
  default_layout_sidebar_size: 0
  custom_layout: '{"root":{"children":[{"branch":{"size":65,"children":[{"leaf":{"tabs":["xjy3ghgj4zw3"],"activeTabId":"xjy3ghgj4zw3","size":48}},{"leaf":{"tabs":["g9vyfwpwvl7p"],"activeTabId":"g9vyfwpwvl7p","size":48}}]}},{"leaf":{"tabs":["assignment"],"activeTabId":"assignment","size":33}}],"orientation":"Horizontal"}}'
---
Now we'll edit the service configuration files, also known as `systemd unit` files. These files are plain text ini-style files that encode information about the podman container that we want to run as a rootless service.

In other words, we will log into a non-root user account on our RHEL system and configure a service to run a docker container with Podman.

There are many types of Podman systemd unit files, including container, volume, and network (to name a few). The container unit file contains configuration information about how the docker container should by run by Podman, including where to obtain the image, how to map persistent volumes, and what ports to expose for incoming client connections. For more information, please refer to the Podman [documentation here](https://docs.podman.io/en/latest/markdown/podman-systemd.unit.5.html).

Configure the container unit file
===
We will
Click on this red button: [button label="rhel" background="#ee0000" color="#c7c7c7"](tab-0) to switch the menu context to the rhel terminal.

Run the follow

Notice that



