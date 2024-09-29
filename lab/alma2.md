# Alma
Split arm/x64?

## Update
```bash
sudo dnf update -y
```

## Changing the Hostname
```bash
hostnamectl
sudo hostnamectl set-hostname lts.lab.ch
sudo hostnamectl set-hostname "lab linux terminal server" --pretty
sudo systemctl restart systemd-hostnamed
hostnamectl
```
Alternatively, you can set or change the hostname of your system using NetworkManager's Text User Interface. Run the following command and follow the steps as shown below:

```bash
sudo nmtui
```
