# Raspberry Pi OS
Everything you need to know about the RaspberryPi available in the LAB. It is currently used to provide external access to the LAB via ZeroTier and hosts the LAB documentation.

## Installed Software
- RaspberryPi OS 64 bit
- ZeroTier Client
- SSH Server
- VNC Server (Legacy Connection Enabled)
- DOCFX

## Credentials
| Username | Password |
| ----------- | ----------- |
| admin | l3tm31n |

## Networking
| IP | Connection Type |
| ----------- | ----------- |
|127.0.0.1| Ethernet|
|1.1.1.1| ZeroTier|

## ZeroTier
> [!NOTE]
> Consider using Tailscale
- Is a "virtual switch", every device that has the agent installed can communicate natively with each other. 
- Network ID: `a1b2c3d4e5` (LAB)
- 172.16.0.0/12

| Username | Password |
| ----------- | ----------- |
| lab@lab.ch | 50m353cuR3P455w0rd$! |

## Backup
The RaspberryPi gets backed up every midnight using the following script located in `/usr/local/bin` via crontab:
```
#!/bin/bash

# User Variables #
MountPoint="/media/backup/"
ServerName="//127.0.0.2/backup"
UserName="backup_user"
Password="50m353cuR3P455w0rd$!"


# You Should Not Need To Edit Past This Line #
hname=`hostname`
BackupDir="${MountPoint}${hname}"

 
# Check for backup directory, if not found create it #
directory_check () {
echo "Checking for "$BackupDir" and creating if missing"
[ ! -d "$BackupDir" ] && mkdir -p "$BackupDir"
}
 
 
# Do something else below #

mount.cifs ${ServerName} ${MountPoint} -o user=${UserName},password=${Password}

directory_check

echo "Starting Backup"
dd if=/dev/mmcblk0 of=${BackupDir}/$(date +%Y-%m-%d).img bs=1M status=progress
echo "Backup Complete"
umount /media/backup
```
The Backups do not get rotated. The RaspberryPi uses own credentials for accessing the [NAS](/hardware/nas.html).
