# myalerts-diskusage
Send email on critical disk space usage.

## Usage
Before using it, you have to change the settings in `/etc/myalerts/diskusage.config`.

### Example configuration (assuming you wanna monitor /dev/sda1 (/) and /dev/sda2 (/var) partitions)
```sh
MYALERTS_EMAIL="user@example.com"

# you need to specify every fs you wanna monitor with the following syntax:
#	<device name or mount point> <maximum allowed usage percentage>
MYALERTS_DISK_CONFIG=(
	/dev/sda1 90
	/var 85
)
```

It will use your server's mail system, so if you want this script to work properly you have to setup one for outgoing mails.

## Installation
- You can either [download](https://github.com/tamas646/myalerts-diskusage/raw/main/myalerts-diskusage_1.0.1_all.deb) and install the deb package or use the source code and setup it yourself.

- If you wish, you can install it from my apt repository too:

  ```sh
  sudo echo "deb [signed-by=/usr/share/keyrings/ptamas-pub.gpg] http://apt.ptamas.hu/main/ ./" > /etc/apt/sources.list.d/apt.ptamas.list
  wget -qO - https://apt.ptamas.hu/ptamas-pub.gpg | gpg --dearmor | sudo tee /usr/share/keyrings/ptamas-pub.gpg > /dev/null
  apt update && apt install myalerts-diskusage
  ```
