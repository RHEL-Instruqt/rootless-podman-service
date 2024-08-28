---
slug: verify-container-service
id: ndxdhfrqtsoa
type: challenge
title: Verify the container service is working
teaser: Verify that the container service is working.
notes:
- type: text
  contents: In this assigment we'll check that the container service runs properly.
tabs:
- id: cnwbgdnn9qlw
  title: rhel
  type: terminal
  hostname: rhel
  cmd: su - garfield
- id: 0px5a3hqzu86
  title: Editor
  type: code
  hostname: rhel
  path: /home/garfield/.local/share/containers/storage/volumes/systemd-httpd-data/_data/index.html
difficulty: basic
timelimit: 0
lab_config:
  default_layout_sidebar_size: 0
  custom_layout: '{"root":{"children":[{"branch":{"size":65,"children":[{"leaf":{"tabs":["cnwbgdnn9qlw"],"activeTabId":"cnwbgdnn9qlw","size":48}},{"leaf":{"tabs":["0px5a3hqzu86"],"activeTabId":"0px5a3hqzu86","size":49}}]}},{"leaf":{"tabs":["assignment"],"activeTabId":"assignment","size":33}}],"orientation":"Horizontal"}}'
---
We'll check the service is running properly and then modify the index.html through the persistent volume.

Check the service
===
In the [button label="rhel" background="#ee0000" color="#c7c7c7"](tab-0)  terminal, run the following command to check that the httpd container is running.
```bash,run
podman ps
```
![Aug-28-2024_at_14.44.51-image.png](https://play.instruqt.com/assets/tracks/olghe3gyqvaq/cec7903cb7b5739b3329757e67d742a0/assets/Aug-28-2024_at_14.44.51-image.png)

Let's check the systemd service is running the container.
```bash,run
systemctl --user status httpd --no-pager
```
![Aug-28-2024_at_14.46.02-image.png](https://play.instruqt.com/assets/tracks/olghe3gyqvaq/5f6b2c63fe43e85a3796ee778025121d/assets/Aug-28-2024_at_14.46.02-image.png)

You can stop and start the httpd service with the following commands.

To stop the httpd service.
```bash
systemctl --user stop httpd
```

To start the httpd service.
```bash
systemctl --user start httpd
```

Now let's check that the web server actually works.
```bash,run
curl http://localhost:8080
```
![Aug-28-2024_at_14.52.56-image.png](https://play.instruqt.com/assets/tracks/olghe3gyqvaq/d1229aa96426be7cf2ba4ab882238ff2/assets/Aug-28-2024_at_14.52.56-image.png)

Modify index.html
===
Let's modify the index.html of the webserver. We do this by editing the index.html file without having to initiate a terminal connection into the container. We can directly modify the index.html file through the persistent volume mapping.

Persistent volumes for all rootless container services are located in `/home/garfield/.local/share/containers/storage/volumes/`.  For our httpd service, recall that we defined the `httpd-data.volume` file. The volume is contained in `systemd-httpd-data/`.
```bash,run
ls -la /home/garfield/.local/share/containers/storage/volumes/systemd-httpd-data/
```
![Aug-28-2024_at_14.57.37-image.png](https://play.instruqt.com/assets/tracks/olghe3gyqvaq/7b203c4102e7f3630c7a15ee26d28ee0/assets/Aug-28-2024_at_14.57.37-image.png)

Notice that the `_data` directory is owned by garfield:garfield as we specified in the `httpd-data.volume` unit file.

Switch to the Editor tab by clicking on this button: [button label="Editor" background="#ee0000" color="#c7c7c7"](tab-1)
![Aug-28-2024_at_15.00.21-image.png](https://play.instruqt.com/assets/tracks/olghe3gyqvaq/85e430cadedcc3639c52e47eeb27c41b/assets/Aug-28-2024_at_15.00.21-image.png)

Change the sentence `It works!` to `I love lassagne.`.
```text
I love lassagne
```

Switch back to the [button label="rhel" background="#ee0000" color="#c7c7c7"](tab-0) terminal.
Run the curl command again.
```bash,run
curl http://localhost:8080
```
![Aug-28-2024_at_15.11.49-image.png](https://play.instruqt.com/assets/tracks/olghe3gyqvaq/bc852f07a9e953531b16e6c2c4b93c64/assets/Aug-28-2024_at_15.11.49-image.png)
