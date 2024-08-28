---
slug: configure-unit-files
id: jxdvchivmtxq
type: challenge
title: Configure the unit files
teaser: Configure the container and volume unit files.
notes:
- type: text
  contents: We will walk through the configuration of systemd unit files to set up
    an Apache web server container. Once the unit files are created, we'll start the
    container service which initiates the automatic download of a specified container
    image, and set up the persistent storage to store the data to serve a web page.
tabs:
- title: rhel
  type: terminal
  hostname: rhel
  cmd: su - garfield
- title: Editor
  type: code
  hostname: rhel
  path: /home/garfield/.config/containers/systemd/
difficulty: basic
timelimit: 0
lab_config:
  default_layout_sidebar_size: 0
---

