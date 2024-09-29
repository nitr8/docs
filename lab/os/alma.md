# AlmaLinux OS
Split arm/x64?

## Changing the Hostname
```bash
hostnamectl
sudo hostnamectl set-hostname lts.kwo.lt
sudo hostnamectl set-hostname "lab linux terminal server" --pretty
sudo systemctl restart systemd-hostnamed
hostnamectl
```
Alternatively, you can set or change the hostname of your system using NetworkManager's Text User Interface. Run the following command and follow the steps as shown below:

```bash
sudo nmtui
```

## VMware Tools
```bash
sudo dnf -y install open-vm-tools
```